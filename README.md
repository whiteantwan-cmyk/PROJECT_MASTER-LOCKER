
#!/usr/bin/env bash
set -e

# === CONFIG ===
REPO_URL="https://github.com/whiteantwan-cmyk/PROJECT_MASTER-LOCKER.git"
CLONE_DIR="PROJECT_MASTER-LOCKER"
BRANCH="main"

# Clone or init repo
if git ls-remote "$REPO_URL" &>/dev/null; then
  git clone "$REPO_URL" "$CLONE_DIR"
  cd "$CLONE_DIR"
else
  echo "Remote repo not found or inaccessible: $REPO_URL"
  echo "If the repo doesn't exist, create it on GitHub first or use 'gh repo create'."
  exit 1
fi

# If repository empty (no commits), create main branch by making a README if needed
if [ -z "$(git rev-parse --symbolic-full-name --abbrev-ref HEAD 2>/dev/null || true)" ] || [ "$(git rev-parse --abbrev-ref HEAD)" = "HEAD" ]; then
  git checkout -b "$BRANCH"
fi

# Create files (overwrite if exist)
cat > index.html <<'HTML'
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Project Master Locker — Dashboard</title>
  <style>
    :root{--bg:#0f1724;--card:#0b1220;--accent:#06b6d4;--muted:#9aa5b1;color-scheme:dark}
    *{box-sizing:border-box;font-family:Inter,system-ui,-apple-system,Segoe UI,Roboto,"Helvetica Neue",Arial}
    body{margin:0;background:linear-gradient(180deg,#071022 0%, #0b1220 100%);color:#e6eef3;min-height:100vh;display:flex;flex-direction:column;align-items:center}
    header{width:100%;max-width:1100px;padding:28px 20px;display:flex;align-items:center;gap:16px}
    h1{margin:0;font-size:20px}
    .subtitle{color:var(--muted);font-size:13px}
    main{width:100%;max-width:1100px;padding:20px;display:grid;grid-template-columns:repeat(auto-fit,minmax(300px,1fr));gap:18px}
    .card{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));border-radius:10px;padding:16px;box-shadow:0 4px 18px rgba(2,6,23,0.6);border:1px solid rgba(255,255,255,0.03)}
    .card h2{margin:6px 0 10px;font-size:16px}
    .actions{display:flex;gap:8px;flex-wrap:wrap}
    a.button{display:inline-block;padding:10px 12px;border-radius:8px;text-decoration:none;color:#062b31;background:linear-gradient(90deg,#06b6d4,#0ea5a7);font-weight:600}
    a.ghost{background:transparent;border:1px solid rgba(255,255,255,0.06);color:var(--muted);padding:8px 10px}
    .preview{height:340px;border-radius:8px;overflow:hidden;border:1px solid rgba(255,255,255,0.02);background:#020617}
    iframe{width:100%;height:100%;border:0}
    footer{width:100%;max-width:1100px;padding:18px 20px;color:var(--muted);font-size:13px}
    @media (max-width:420px){ .preview{height:220px} header, footer{padding-left:12px;padding-right:12px} }
  </style>
</head>
<body>
  <header>
    <div style="flex:1">
      <h1>Project Master Locker</h1>
      <div class="subtitle">One place for your demo pages — snake game and sales dashboard</div>
    </div>
    <div style="text-align:right">
      <div style="font-size:12px;color:var(--muted)">Deployed via GitHub Pages</div>
      <div style="font-size:12px;color:var(--muted)">Tip: Add to iPhone home screen</div>
    </div>
  </header>

  <main>
    <section class="card">
      <h2>Live Preview — Snake Game</h2>
      <div class="preview" title="Snake Game preview">
        <iframe src="snake_game.html" loading="lazy" referrerpolicy="no-referrer"></iframe>
      </div>
      <div style="margin-top:12px" class="actions">
        <a class="button" href="snake_game.html" target="_blank">Open Snake Game</a>
        <a class="ghost" href="snake_game.html" target="_blank">Open in new tab</a>
      </div>
    </section>

    <section class="card">
      <h2>Live Preview — Sales Dashboard</h2>
      <div class="preview" title="Sales Dashboard preview">
        <iframe src="sales_dashboard.html" loading="lazy" referrerpolicy="no-referrer"></iframe>
      </div>
      <div style="margin-top:12px" class="actions">
        <a class="button" href="sales_dashboard.html" target="_blank">Open Sales Dashboard</a>
        <a class="ghost" href="sales_dashboard.html" target="_blank">Open in new tab</a>
      </div>
    </section>

    <section class="card" style="grid-column:1/-1">
      <h2>Repository & Deployment</h2>
      <p style="color:var(--muted);margin:6px 0 12px">If you saved these files to your repository root and enabled Pages on the main branch, your site will be available at:
      <br><strong style="color:#9be7ef">https://whiteantwan-cmyk.github.io/PROJECT_MASTER-LOCKER/</strong>
      </p>
      <div class="actions">
        <a class="button" href="https://github.com/whiteantwan-cmyk/PROJECT_MASTER-LOCKER" target="_blank">Open Repository</a>
        <a class="ghost" href="https://docs.github.com/en/pages" target="_blank">GitHub Pages docs</a>
      </div>
    </section>
  </main>

  <footer>
    I created three ready-to-paste files (index.html, snake_game.html, sales_dashboard.html). Paste each file into your PROJECT_MASTER-LOCKER repo via "Add file → Create new file", commit, then enable Pages on the gh-pages or main branch; your live dashboard will appear at the Pages URL in a minute or two.
  </footer>
</body>
</html>
HTML

cat > snake_game.html <<'HTML'
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale*](#)

