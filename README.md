# ReadMD capability packs

Optional, offline engines for ReadMD. The reader, Markdown editing, native Word/EPUB conversion and basic PDF export remain in the main application.

## Available Windows x64 packs

- **pdfium 7881**: 17.3 MiB download, 13.0 MiB installed. SHA-256 and individual file locks are included in catalog.json and locks/.
- **typst 0.15.1**: 29.9 MiB download, 50.1 MiB installed. SHA-256 and individual file locks are included in catalog.json and locks/.

Install directly at the corresponding feature entry, choose optional components in the Windows installer, or import a .readmd-pack file offline. ReadMD verifies the application-pinned manifest, every file digest, and a real engine operation before atomic installation. Packs do not contain installer scripts.

Only Windows x64 packs have been prepared and native tested. OCR, transcription, TeX and other-platform delivery are still being prepared; this repository does not claim those are available. Upstream licenses and dependency/font notices are included inside each pack.

## Reproducibility

The builders assemble previously reviewed local resources only; they do not fetch floating versions or install dependencies. Runtime downloads use this repository rather than an upstream project release. Every new pack version needs an updated application lock and native evidence.
