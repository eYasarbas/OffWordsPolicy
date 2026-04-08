# Smart Kategori model artifacts

This folder is used by the Smart Kategori app to download its on-device model files.

## Files

- `smart_kategori_model_manifest.json` — model manifest consumed by the app
- `smart_kategori_model.onnx` — the actual model file (to be added)

## Manifest format

The app expects a JSON object with:

- `download_url` (string) — direct HTTPS URL to the model binary (raw GitHub URL)
- `size_bytes` (number) — model size in bytes
- `sha256` (string) — hex sha256 of the model file
- `model_id` (string) — stable id (e.g. `smart_kategori`)
- `version` (string) — semantic version for cache folder (e.g. `1.0.0`)

## How to compute SHA256 and size (Windows)

```powershell
$file = "smart_kategori_model.onnx"
(Get-FileHash $file -Algorithm SHA256).Hash.ToLower()
(Get-Item $file).Length
```

## Note about large files

If the ONNX file is large, consider using Git LFS. If you use LFS, `download_url`
must still point to a raw file URL that returns the binary bytes.

