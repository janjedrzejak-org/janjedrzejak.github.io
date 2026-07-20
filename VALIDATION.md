# Validation report

Completed locally on the updated bundle:

- JavaScript syntax: `node --check home.js` — passed
- HTML parser validation — passed
- Duplicate ID check — passed
- Translation-key coverage: 118/118 keys — passed
- No plain-text translation marker contains nested interactive markup — passed
- Portrait markup and `img/me.jpg` source — passed
- Desktop Chromium render at 1440 × 1000 — passed
- Desktop EN → PL → EN switch — passed
- Animated hero headline rebuild after language change — passed
- Polish navigation, document title and ARIA language-toggle label — passed
- Desktop horizontal overflow: 0 px — passed
- Mobile Chromium render at 390 × 844 — passed
- Mobile browser locale (`pl-PL`) selects Polish — passed
- Mobile horizontal overflow: 0 px — passed
- Mobile menu state and translated ARIA label — passed
- Portrait responsive width on mobile — passed
- Runtime browser errors — none
- Reduced-motion rules — present

The browser validation used an offline inlined copy of the production HTML/CSS/JS because the execution environment blocks local and external browser navigation. The portrait was replaced only in that isolated test with a neutral placeholder; the delivered HTML continues to use `img/me.jpg` with a GitHub-avatar fallback.
