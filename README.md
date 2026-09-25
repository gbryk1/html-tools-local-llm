# HTML tools z lokalnym modelem w przeglądarce

Samodzielne narzędzia HTML w duchu
[„Useful patterns for building HTML tools”](https://simonwillison.net/2025/Dec/10/html-tools/)
Simona Willisona: pojedyncze pliki HTML, bez Reacta, bez build-stepu, bez backendu.
Modele neuronowe są wbudowane w strony jako **base64** i uruchamiane w przeglądarce przez
WebAssembly / WebGPU z pomocą [transformers.js](https://github.com/huggingface/transformers.js).
Dane użytkownika nigdy nie opuszczają urządzenia.

## Narzędzia

| Narzędzie | Model | Rozmiar | Uwagi |
|---|---|---|---|
| [`docs/speech-to-text.html`](docs/speech-to-text.html) | `onnx-community/whisper-tiny` (q8, wielojęzyczny) | 58 MB | Cały model w jednym pliku HTML |
| [`docs/chat.html`](docs/chat.html) | `onnx-community/SmolLM2-135M-Instruct-ONNX` (q4f16) | 117 MB → 156 MB base64 | Model podzielony na 3 pliki `.txt` (limit 100 MB/plik na GitHub Pages) |
| [`docs/cassandra-course.html`](docs/cassandra-course.html) | — (brak modelu ML) | ~160 KB | Animowany kurs wewnętrznej architektury i zasad designu Apache Cassandra w stylu „Head First” (scrollytelling, SVG/Canvas, IntersectionObserver). Źródło: `src/cassandra-course.html`, kopiowane przez `build.py` |

### Jak to działa

1. **Model jako base64.** `build.py` czyta pliki ONNX i koduje je do base64:
   * speech-to-text: base64 trafia inline do `<script type="text/plain">` w HTML,
   * chat: base64 trafia do `chat-model.b64.part*.txt`, strumieniowo pobieranych i dekodowanych do
     jednego bufora `Uint8Array`.
2. **Wbudowany model udaje serwer.** Strona podmienia `window.fetch` i przechwytuje żądania
   kierowane do `https://local-model.invalid/…`, zwracając bajty z pamięci jako `Response`.
   Dzięki temu `transformers.js` ładuje model „z sieci”, choć nic nie wychodzi z przeglądarki.
3. **Inferencja lokalna.** `pipeline('automatic-speech-recognition', …)` (Whisper) oraz
   `pipeline('text-generation', …)` (SmolLM2) działają na WebGPU, z fallbackiem na WASM.
   Biblioteka `transformers.js` ładowana jest z CDN (wzorzec „load dependencies from CDNs”).

Bajty modelu są mapowane po nazwie pliku plus aliasy (`encoder_model*.onnx` → wersja `q8`,
`model*.onnx` → wersja `q4f16`), więc kwantyzacja jest wybierana przez `dtype` w kodzie strony.

## Skille

- [`skills/animated-knowledge-page`](skills/animated-knowledge-page/SKILL.md) — metoda budowy animowanych,
  scrollytellingowych stron wiedzy w stylu „Head First” (jak `cassandra-course.html`): plan rozdziałów, boxy,
  diagramy SVG/Canvas uruchamiane przez IntersectionObserver, quiz, ściąga, test headless
  ([`scripts/check-page.cjs`](skills/animated-knowledge-page/scripts/check-page.cjs)) i znane pułapki.

## Przebudowa

```bash
# 1. modele (nie są trzymane w repo — 160 MB)
mkdir -p models/whisper models/chat
W=https://huggingface.co/onnx-community/whisper-tiny/resolve/main
C=https://huggingface.co/onnx-community/SmolLM2-135M-Instruct-ONNX/resolve/main
for f in config.json generation_config.json preprocessor_config.json \
         tokenizer.json tokenizer_config.json added_tokens.json special_tokens_map.json; do
  curl -sL -o models/whisper/$f "$W/$f"
done
curl -sL -o models/whisper/encoder_model_quantized.onnx "$W/onnx/encoder_model_quantized.onnx"
curl -sL -o models/whisper/decoder_model_merged_quantized.onnx "$W/onnx/decoder_model_merged_quantized.onnx"
for f in config.json generation_config.json tokenizer.json tokenizer_config.json special_tokens_map.json; do
  curl -sL -o models/chat/$f "$C/$f"
done
curl -sL -o models/chat/model_q4f16.onnx "$C/onnx/model_q4f16.onnx"

# 2. build (do docs/)
python3 build.py --clean

# 3. lokalny podgląd
python3 -m http.server 8099 -d docs
```

## Uwagi

- **Rozmiar.** GitHub Pages nie przyjmuje plików >100 MB, dlatego model czatu (156 MB base64) jest
  podzielony. Przy pierwszym wejściu pobierze się ~156 MB (gzip w tranzycie zmniejsza to o ~25%).
- **WebGPU.** `q4f16` jest zoptymalizowany pod WebGPU (Chrome/Edge 113+, Safari 18+). Bez WebGPU
  strona próbuje WASM i pokazuje komunikat, jeśli format nie jest obsługiwany.
- **Prywatność.** Brak backendu, brak telemetrii; opcjonalnie całość działa offline po pierwszym
  załadowaniu, o ile biblioteka z CDN jest w cache przeglądarki.