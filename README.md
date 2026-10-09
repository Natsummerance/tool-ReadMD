# ReadMD capability packs

Optional, offline engines for ReadMD. Reading, Markdown editing and Rust-native Word/EPUB conversion remain in the main application. Word conversion does not require Office, WPS or LibreOffice.

## Available Windows x64 packs

- **pdfium 7881**: 17.3 MiB download, 13.0 MiB installed. SHA-256 and individual file locks are included in catalog.json and locks/.
- **typst 0.15.1**: 29.9 MiB download, 50.1 MiB installed. SHA-256 and individual file locks are included in catalog.json and locks/.
- **ocr 5.5.3-r1**: 9.4 MiB download, 12.7 MiB installed. SHA-256 and individual file locks are included in catalog.json and locks/.

PDFium provides PDF page editing/rasterization; Typst provides academic PDF typesetting; OCR includes a static Tesseract/Leptonica engine and English, simplified Chinese and traditional Chinese recognition models. Rust decodes images; no Office, Python, Node, VC redistributable or OS OCR language pack is required for this OCR path. OCR accuracy depends on the scan; handwriting is not certified.

Install directly at the corresponding feature entry, choose components in the Windows installer (OCR is recommended and can be deselected), or import a .readmd-pack file offline. ReadMD verifies the application-pinned manifest, every file digest, and a real engine operation before atomic installation. Packs contain no installer scripts. The existing application lock is the trust root; a remotely edited catalog cannot authorize arbitrary code.

Only Windows x64 packs have been prepared and native tested. Transcription, TeX and other-platform delivery remain pending. Upstream licenses and dependency/font notices are included inside each pack. This package release does not publish a new version of the main ReadMD application.

## Reproducibility

Builders are archived here for inspection; they run from the matching rust-ReadMD checkout, which supplies assets/, tools/ and the Rust worker source. Copy builders/ to tools/ in that checkout, prepare the exact locked local inputs, then use each script's usage line. OCR source/model/tool hashes are in builders/ocr-runtime-inputs.lock.json. The OCR compiler and every pack builder run offline; explicit preparation of locked sources is separate. The PDF worker must be built with the checkout's Cargo.lock.

Builders do not fetch floating versions or execute package installer scripts. Runtime downloads use this repository rather than an upstream project release. Every new pack version needs an updated application lock and native evidence. Compiler output is locked per reviewed build; the recipes do not claim bit-for-bit reproducibility across arbitrary compiler versions.
