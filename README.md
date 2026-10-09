# ReadMD capability packs

Optional offline engines for ReadMD. Markdown, Rust-native DOCX/EPUB conversion and basic PDF output remain in the core. Generating Word files does not require Office, WPS or LibreOffice.

| Engine | Platform | Download | Installed |
| --- | --- | ---: | ---: |
| pdfium 7881 | windows-x64 | 17.3 MiB | 13.0 MiB |
| typst 0.15.1 | windows-x64 | 29.9 MiB | 50.1 MiB |
| ocr 5.5.3-r1 | windows-x64 | 9.4 MiB | 12.7 MiB |

PDFium provides PDF page-object editing/rasterization. Typst provides academic PDF typesetting. OCR includes a static Tesseract/Leptonica engine and English, simplified Chinese and traditional Chinese models; Rust decodes images without Office, Python, Node or OS OCR language packs. Handwriting and universal recognition accuracy are not certified.

Use the feature-entry installer, choose components in Windows setup, or import a .readmd-pack offline. Application-pinned locks, each file digest and an actual engine operation are checked before installation. Packs contain no installer scripts. A remotely edited catalog cannot authorize new code for an existing application.

Only listed platform packs are prepared. Native evidence currently covers Windows x64. Transcription, traditional TeX, additional fonts, GUI host delivery and other platforms remain open. Original upstream licenses and notices are retained inside every pack. This release is independent of the main ReadMD application version.

## Rebuilding and publishing

Builders are archived for inspection; run them from the matching rust-ReadMD checkout, which supplies assets/, tools/, the worker source and Cargo.lock. Copy builders/ into that checkout's tools/ if necessary. Prepare exact locked local inputs separately, then build offline. OCR source/model/tool locks are in builders/ocr-runtime-inputs.lock.json. Compiler output is locked per reviewed build; bit-identical output across arbitrary compilers is not promised.

Put catalog-named packages in one staging directory. From the main checkout run:

```sh
node tools/publish-capability-packs.mjs --packs STAGING_DIRECTORY
```

The default is an offline preflight: no network or credential read. After review, append --publish to update only this owned repository using the configured GitHub credential. All local payloads are checked first. Existing published assets with a different digest are refused rather than overwritten. New versions need a new release tag, updated application locks, licenses and native evidence. No documents, videos, social assets or user profile files are included.
