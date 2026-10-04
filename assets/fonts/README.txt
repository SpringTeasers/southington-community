SELF-HOSTED FONTS — Southington Community Site
==============================================
styles.css declares three @font-face rules pointing at this folder. The files
are NOT yet in the repo, so the declared stacks fall back cleanly:

  Display headings → Georgia, "Times New Roman", serif
  Body / UI        → system-ui / -apple-system / Segoe UI / Roboto / Arial

Drop these two files (plus the italic serif) into this folder and the real
faces take over with no other change:

  FT-01  SourceSerif4-Variable.woff2         (400-700, italic axis)
         SourceSerif4-Italic-Variable.woff2  (400-700 italic)
         License: SIL Open Font License 1.1
         Source:  https://github.com/adobe-fonts/source-serif

  FT-02  Inter-Variable.woff2                (400-700)
         License: SIL Open Font License 1.1
         Source:  https://github.com/rsms/inter

Requirements (design/assets.md §6):
  - Latin subset, .woff2 only
  - font-display: swap (already declared)
  - preload the two above-the-fold faces
  - NO Google Fonts CDN call — privacy and uptime independence
