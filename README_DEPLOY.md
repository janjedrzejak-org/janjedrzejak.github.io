# Jan Jędrzejak portfolio redesign

This bundle is a drop-in redesign for `janjedrzejak/janjedrzejak.github.io`.

## Files

- `index.html` — complete homepage replacement with bilingual EN/PL content and portrait section
- `home.css` — isolated homepage design system, responsive layout and portrait/language-switch styling
- `home.js` — language switching, progressive animation, parallax, canvas network, reveal, cursor and mobile menu logic
- `apply-redesign.sh` — helper that copies the three production files into a local repository checkout
- `preview-desktop.png` and `preview-mobile.png` — visual previews

The existing `styl.css`, `projects.html`, `blog.html`, cookie scripts and repository assets remain untouched. This protects the current secondary pages from regressions.

## Language switch

- The homepage supports English and Polish without a page reload.
- The initial language follows a previously saved choice; otherwise it follows the browser language.
- The choice is stored under `portfolio-language` in `localStorage`.
- Visible content, navigation, buttons, SEO title/description, Open Graph locale and accessibility labels are updated.
- The animated headline is rebuilt safely after every language change.

## Portrait

The profile section uses the existing repository asset:

```text
img/me.jpg
```

If that file cannot be loaded, the script falls back to Jan's public GitHub avatar. The bundle deliberately does not overwrite the existing portrait file.

## Deployment

Copy the three production files to the repository root and commit them on a feature branch:

```bash
git switch -c agent/immersive-portfolio-redesign
cp /path/to/index.html ./index.html
cp /path/to/home.css ./home.css
cp /path/to/home.js ./home.js
git add index.html home.css home.js
git commit -m "Add bilingual immersive portfolio redesign"
git push -u origin agent/immersive-portfolio-redesign
```

Alternatively:

```bash
./apply-redesign.sh /path/to/janjedrzejak.github.io
```

Then open a pull request into `main`.

## Design and implementation notes

- No framework migration: remains compatible with GitHub Pages.
- No animation dependency: all effects use native CSS, Canvas and browser APIs.
- Supports `prefers-reduced-motion`.
- Canvas rendering pauses outside the viewport.
- Device pixel ratio is capped to limit GPU cost.
- Touch devices do not receive cursor, tilt or magnetic interactions.
- Existing project, blog, résumé, privacy, cookie, contact and asset URLs are preserved.
- Homepage styles are isolated in `home.css`, so replacing `styl.css` is unnecessary.

## Suggested verification after deployment

1. Confirm that `img/me.jpg` displays correctly.
2. Switch EN → PL → EN and reload the page to confirm that the saved preference is restored.
3. Test at 1440px, 1024px, 768px, 390px and 320px widths.
4. Run Lighthouse for Performance, Accessibility, Best Practices and SEO.
5. Verify `projects.html`, `blog.html`, `resJanJedrzejakCV.pdf`, cookie consent and contact links.
6. Test with reduced motion enabled at OS/browser level.
