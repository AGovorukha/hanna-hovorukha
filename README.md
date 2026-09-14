# hanna-hovorukha.github.io

Portfolio site for Hanna Hovorukha, architect and interior designer.
Plain HTML and CSS, no build step, served by GitHub Pages.

## Where the PDF goes

**Put the portfolio PDF in the root of this repository, named exactly `portfolio.pdf`.**

That is the only file you need to touch to update the portfolio. Nothing in the
HTML needs changing — the page links to `portfolio.pdf` by name.

From the command line:

```sh
cp /path/to/her-portfolio.pdf portfolio.pdf
git add portfolio.pdf
git commit -m "Update portfolio"
git push
```

Or in the browser: open the repository on github.com, click `portfolio.pdf`,
then the pencil / "Replace this file" control, and upload the new one.

The live site picks the change up in about a minute.

### Size limits — read this before uploading

| Limit | Value |
|---|---|
| Single file, hard limit | **100 MB** (GitHub rejects the push above this) |
| Single file, warning | 50 MB |
| Whole Pages site, soft limit | 1 GB |

Architecture portfolios full of renders go past 100 MB easily. If the PDF is too
big, export a web version at lower image resolution (in most tools: export as
PDF, downsample images to 150 dpi). Keep the print-resolution original elsewhere.

To check the size first: `ls -lh portfolio.pdf`

## Files

| File | What it is |
|---|---|
| `index.html` | The whole page. Name, intro, capability schedule, PDF viewer, contact. |
| `style.css` | All styling. Colours are CSS variables at the top. |
| `portfolio.pdf` | The portfolio. **Replace this file.** |
| `assets/` | Optional images, if the page ever grows project sections. |
| `.nojekyll` | Tells Pages to serve the files as-is, without Jekyll processing. |

## The portfolio PDF

The committed `portfolio.pdf` is a web-optimised build: the 94 MB original was
downsampled to 150 dpi with Ghostscript, giving 14 MB across the same 37 pages.
Keep the full-resolution original off GitHub — anything committed here stays in
git history permanently.

To regenerate from a new original:

```sh
gs -q -dNOPAUSE -dBATCH -dSAFER -sDEVICE=pdfwrite -dCompatibilityLevel=1.5 \
   -dDetectDuplicateImages=true \
   -dDownsampleColorImages=true -dColorImageDownsampleType=/Bicubic -dColorImageResolution=150 \
   -dDownsampleGrayImages=true -dGrayImageDownsampleType=/Bicubic -dGrayImageResolution=150 \
   -dAutoFilterColorImages=false -dColorImageFilter=/DCTEncode -dJPEGQ=82 \
   -sOutputFile=portfolio.pdf "/path/to/original.pdf"
```

## Still to check

- `Berlin` in `index.html` — change if that's not where she's working.

## Moving the site to Hanna's own account

The site currently lives under `AGovorukha`. To get the URL
`https://hanna-hovorukha.github.io`:

1. Hanna creates a GitHub account with the username **`hanna-hovorukha`** (it was
   free as of Sept 2026).
2. On this repo: Settings → General → Danger Zone → **Transfer ownership** → to
   `hanna-hovorukha`.
3. On her account, rename the repo to **`hanna-hovorukha.github.io`**.
4. Settings → Pages → set source to branch `main`, folder `/ (root)`.

History and the old URL's redirect are preserved by GitHub.
