# BAYBREAK.exe: upload instructions (mobile release)

Repository: https://github.com/barneysmith-sys/baybreak

1. Unzip `BAYBREAK-MOBILE-READY.zip`. There is no wrapper folder; `index.html` is at the top.
2. On GitHub: **Add file > Upload files**.
3. Drag in the four files below and commit to `main`. Vercel redeploys automatically.

## Replace (4)
- `index.html` (the mobile layer; desktop behaviour is unchanged)
- `CHANGELOG.md`
- `UPLOAD-INSTRUCTIONS.md`
- `MANIFEST.md`

Every other file in the ZIP is byte-identical to GitHub `main`: all artwork, `vercel.json`, `favicon.ico`, `assets/icons/`, `assets/social/` and every Open Graph, Twitter and SEO tag. They're included so the ZIP is a complete copy, but you don't need to upload them.
