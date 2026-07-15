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

The local AI engine still runs in each visitor's browser. On first load, the page imports WebLLM and downloads the Llama 3.2 1B q4f16 browser model. After that, the browser cache can make repeat visits faster.

No API key or private backend is needed.

## Browser Notes

- Chrome or Edge on desktop are the best targets because WebGPU support is strongest there.
- WebGPU is required for the smarter local model.
- If the model cannot load, the game silently falls back to its built-in phrase generator so rounds do not crash.
- First load can take a while because larger model files are downloaded by the visitor's browser.

## Model

- Model: `Llama-3.2-1B-Instruct-q4f16_1-MLC`
- Library: WebLLM
- Approximate first-load model download: several hundred MB, depending on CDN/model shard packaging and browser cache behavior
- Runtime requirement: WebGPU
