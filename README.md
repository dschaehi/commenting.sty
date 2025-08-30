# commenting.sty

Lightweight, color‑coded collaborative annotation tools for LaTeX manuscripts.

## Features
- Added (tracked) text with per‑author signatures
- Inline and footnote-style comments
- Multi-line inline and footnote comment environments
- Colored paragraph environments (author-highlighted blocks)
- Draft / final mode switch (all markup suppressed in final mode)
- Colorblind-safe palette (10 distinct hues)
- Minimal macro namespace pollution (per-author command families)

## Installation
Place `commenting.sty` somewhere in your `TEXINPUTS` path (same directory or a local texmf tree), then:

```latex
\usepackage[draft]{commenting} % or [final]
```

## Basic Usage

```latex
\usepackage[draft]{commenting}
\registerauthor{alice}[Alice][cbBlue]
\registerauthor{bob}[Bob][cbOrange]

Some \alice{new important wording}. \alicei{Maybe refine term?}
\bobf{Source?} Added sentence.

\begin{aliceienv}
Spanning multi-line inline comment.
\end{aliceienv}

\begin{bobfenv}
Longer rationale in a footnote comment block.
\end{bobfenv}

\begin{aliceenv}
This whole paragraph is highlighted for Alice.
\end{aliceenv}
```

Switch to final mode:

```latex
\usepackage[final]{commenting}
```

## Author Registration

```latex
\registerauthor{<id>}[<Display Name>][<Color>]
```

Defaults:
- Display Name: first token of `\author` (if any) else empty
- Color: `cbRed`

For `id = alice` you get:
- `\alice{<text>}` added text (draft: colored + signature; final: plain)
- `\alicei{<comment>}` inline comment (draft only)
- `\alicef{<comment>}` footnote comment (draft only)
- `\begin{aliceenv}...\end{aliceenv}` colored block (draft only margin signature)
- `\begin{aliceienv}...\end{aliceienv}` multi-line inline comment (draft only)
- `\begin{alicefenv}...\end{alicefenv}` multi-line footnote comment (draft only)

## Draft vs Final Behavior

| Element               | Draft                         | Final                      |
|-----------------------|-------------------------------|----------------------------|
| Added text            | Color + signature             | Plain text                 |
| Inline comment        | Visible                       | Removed                    |
| Footnote comment      | Visible footnote              | Removed                    |
| Inline comment env    | Visible                       | Removed                    |
| Footnote comment env  | Visible footnote              | Removed                    |
| Colored block env     | Highlight + margin signature  | Body only (uncolored)      |

## Color Palette (Colorblind-Safe)

| Name     | RGB          | Role / Hint                  |
|----------|--------------|------------------------------|
| cbBlue   | 51,114,189   | Strong cool base             |
| cbOrange | 255,127,42   | Warm contrast                |
| cbTeal   | 64,204,204   | Soft accent                  |
| cbRed    | 217,37,37    | High-salience warning        |
| cbPurple | 148,103,189  | Muted secondary              |
| cbGreen  | 0,158,115    | Positive / approval          |
| cbYellow | 240,228,66   | Caution / highlight          |
| cbPink   | 204,121,167  | Neutral accent               |
| cbBrown  | 146,73,0     | Earth tone separation        |
| cbGray   | 128,128,128  | Neutral / meta               |

Override example (before any `\registerauthor` calls):
```latex
\definecolor{cbBlue}{RGB}{30,90,170}
```

## Footnote Stream
Comment footnotes use a separate `manyfoot` stream (alphabetic, tinted marker) so scholarly footnotes remain unaffected.

## Customization Hooks
- Redefine `\signature` to change superscript style.
- Redefine palette colors prior to `\registerauthor`.
- Wrap added text macros to layer further styling.

## Robustness Notes
- User-facing macros are robust (safe in section titles, captions).
- Final mode removes comments cleanly (no stray spaces).

## Minimal Example

```latex
\documentclass{article}
\author{Alice A. Author}
\usepackage[draft]{commenting}
\registerauthor{alice}[Alice][cbBlue]
\begin{document}
An \alice{additional} clarification. \alicei{Check phrasing.}
\end{document}
```

## Roadmap
- Deletion / replacement markup (`\strike`, `\replace`)
- Comment list / summary generator
- Export comments to external JSON

## License
MIT (see repository).

## Changelog (Excerpt)
- v2.1 Documentation improvements, clarified version metadata
- v2.0 Refactor & robust command definitions
