# Human or AI? V2 - GitHub Pages Version

This folder is ready to upload to a GitHub repository and publish with GitHub Pages.

## Files

- `index.html` - the complete game
- `.nojekyll` - tells GitHub Pages to serve files directly without Jekyll processing
- `README.md` - these setup notes

## Publish On GitHub Pages

1. Create a new GitHub repository.
2. Upload the files in this folder to the repository root.
3. Go to the repository's `Settings`.
4. Open `Pages`.
5. Under `Build and deployment`, choose:
   - Source: `Deploy from a branch`
   - Branch: `main`
   - Folder: `/ (root)`
6. Save.

GitHub will give you a URL like:

```text
https://YOUR_USERNAME.github.io/YOUR_REPO_NAME/
```

Send that link to friends.

## How It Works

The game is a static single-page app, so GitHub Pages can host it without a backend server.

The local AI engine still runs in each visitor's browser. On first load, the page imports Transformers.js from jsDelivr and downloads the small SmolLM2 ONNX model from Hugging Face. After that, the browser cache can make repeat visits faster.

No API key or private backend is needed.

## Browser Notes

- Chrome or Edge on desktop are the best targets because WebGPU support is strongest there.
- If WebGPU is unavailable, the game tries the browser WASM runtime.
- If the model cannot load, the game silently falls back to its built-in phrase generator so rounds do not crash.
- First load can take a while because model files are downloaded by the visitor's browser.

## Model

- Model: `HuggingFaceTB/SmolLM2-135M-Instruct`
- Library: Transformers.js `3.8.1`
- Approximate first-load model download: roughly `80-120 MB`, depending on CDN/model shard packaging and browser cache behavior
- License: Apache-2.0 upstream model family
