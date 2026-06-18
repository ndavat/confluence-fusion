# Confluence — Free Model Fusion via OpenRouter

A single static HTML page that:

1. Lets you paste an [OpenRouter](https://openrouter.ai) API key
2. Fetches OpenRouter's live model list and auto-filters it to free models (`:free` suffix or all-zero pricing)
3. Lets you pick **up to 4** free models to run as a panel, in parallel, on your prompt
4. Sends all 4 panel responses to a **judge model** (free or paid — your choice, picked at runtime from a dropdown) which synthesizes one final answer

No backend, no build step, no server. It's one `index.html` that talks directly to `https://openrouter.ai/api/v1/*` from the browser (OpenRouter's API supports CORS for browser-based calls with a bearer key).

## Run it locally

Just open `index.html` in a browser. That's it — no `npm install`, no server.

(Some browsers restrict `fetch` from `file://` pages. If you hit issues, run a tiny local server instead:)

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy on GitHub Pages

```bash
git init
git add index.html README.md
git commit -m "Confluence: free-model fusion via OpenRouter"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

Then in the repo on GitHub: **Settings → Pages → Source: Deploy from branch → Branch: `main` / `(root)` → Save**.

Your tool will be live at:
```
https://<your-username>.github.io/<repo-name>/
```

## How your API key is handled

- The key is stored only in `sessionStorage` in your browser tab — it clears when the tab closes.
- It is never sent anywhere except `https://openrouter.ai/api/v1/...` requests, directly from your browser.
- Because this is a static site with no backend, **the key never touches a server you don't control.** (It's still visible in your browser's network tab / dev tools, as with any client-side API usage — don't share your screen with it visible, and don't use a key with a high spend limit on a machine you don't trust.)

## How model selection works

On page load (once a valid key is entered), the app calls `GET /api/v1/models` and filters for models where either:
- the model `id` ends in `:free`, or
- every pricing field (`prompt`, `completion`, `request`, `image`) is `0`

You can free-text filter that list (e.g. type "qwen" or "llama") and check up to 4 boxes.

## How the judge works

The judge dropdown defaults to showing only free models too; check **"Show paid models too"** to pick something like a frontier paid model as judge. The judge receives:

- The original prompt
- Each panel model's full response, labeled by model ID
- Instructions to synthesize one answer: combine the strongest reasoning, resolve contradictions, drop hallucinated/wrong content, and flag genuine unresolved disagreement

You can edit the judge instructions in `buildJudgePrompt()` in `index.html` if you want a different synthesis style (e.g. "pick the single best answer" instead of "merge them").

## Costs

- Panel models tagged free cost nothing.
- The judge call is a normal OpenRouter completion — free if you pick a free judge, billed normally otherwise.
- If a panel model fails (rate-limited, down, etc.) the app still judges using whatever succeeded; if all 4 fail, it stops before calling the judge.

## Customizing

Everything is in one file, `index.html`:
- `MAX_PANEL` constant — change from 4 to any number
- `SLOT_COLORS` — panel accent colors
- `buildJudgePrompt()` — the synthesis instructions sent to the judge
- `isFreeModel()` — the free-model filter logic, if OpenRouter changes how free models are tagged
