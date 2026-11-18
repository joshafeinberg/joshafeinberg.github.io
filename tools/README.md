# Tools

## skyline.html — background generator

Generates `assets/images/bg.png`: a 4800×1200 Chicago skyline rendered in monospace Kotlin code, used as the site's background image.

### Regenerating the background

1. Open `skyline.html` in Chrome/Chromium.
2. Wait until the page title becomes **SKYLINE-READY**.
3. In DevTools console run:

   ```js
   const c = document.getElementById("c");
   Object.assign(document.createElement("a"), { download: "bg.png", href: c.toDataURL() }).click();
   ```

4. Replace `assets/images/bg.png` with the downloaded file (verify it is 4800×1200).

### Customizing

Everything lives in the single `<script>` at the bottom of the page:

- **Colors** — the `BG`, `FG`, and `SPIRE` constants. Keep `FG` close to `BG`: the code should read as texture, not compete with the white page text that sits on top of it.
- **Buildings** — the "skyline layout" section at the end: one call per building (`slab`, `willis`, `hancock`, `wrigley`, `tribune`), each taking `(x, width, height)`. The image is anchored bottom-left, so the left ~1500px of the 4800px canvas is what most visitors see — put landmarks there.
- **Code pool** — `snippets` (Chicago-themed lines) and `realSnippets` (lines sampled from real Kotlin projects). Each run places code randomly, so every regeneration looks different. Keep `realSnippets` free of personal or financial details — the image is public.
