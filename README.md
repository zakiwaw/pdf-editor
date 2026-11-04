# PDF Editor

PDF Editor mit C++ (QPDF) – PDFs hochladen, Seiten löschen, drehen, umsortieren,
zusammenstellen und neu speichern. Alles läuft im Browser, Dateien werden
nirgendwo hochgeladen.

Online: https://zakiwaw.github.io/pdf-editor/

## Dateien

- `index.html` – Seite und Aufbau, lädt die Dateien unten
- `style.css` – Aussehen
- `app.js` – die ganze Editor-Logik (C++-Engine, Text & OCR, Touch-Drag)
- `vendor/pdf-lib.min.js` – PDF schreiben (Reserve-Engine)
- `vendor/pdf.min.js` – PDF lesen und Vorschau (pdf.js)
- `vendor/pdf.worker.min.js` – pdf.js Worker
- `vendor/qpdf.js` – C++-Engine QPDF, kompiliert zu WebAssembly
- `vendor/qpdf.wasm` – die WebAssembly-Datei der C++-Engine

Tesseract.js (OCR, Deutsch + Englisch) wird nur auf Knopfdruck per CDN
geladen, sonst ist die Seite offline nutzbar.
