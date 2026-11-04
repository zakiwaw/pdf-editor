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

## Rust-Engine (lopdf, WebAssembly) – neu seit 04.11.2026

Zusätzlich zur C++-Engine (QPDF) gibt es Rust (lopdf 0.35) als WebAssembly:
- Dateien: `vendor/rust_pdf.js` (wasm-bindgen Glue, 7 KB) + `vendor/rust_pdf.wasm` (634 KB)
- Rust-Projekt: `workspace/pdf-editor-rust/` (Cargo.toml, src/lib.rs, pkg/ als Build-Ausgabe)
- Echte Funktion: PDF verkleinern – Metadaten entfernen, ungenutzte Objekte
  entfernen, Streams neu komprimieren, neu speichern. Bereich
  „Rust – PDF verkleinern“ auf der Seite, lädt erst auf Knopfdruck.
- Kein Passwort-Schutz: lopdf 0.35 kann verschlüsselte PDFs nur lesen,
  es gibt keine API zum Verschlüsseln beim Speichern.
- Fällt Rust aus, läuft die Seite weiter normal mit C++.
