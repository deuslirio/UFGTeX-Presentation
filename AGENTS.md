# UFGTeX-Presentation — AI Guide

Template guide for AI assistants (Claude, Copilot, Cursor, Gemini, etc.).
Reference this file when writing or editing slides for this Beamer template.

---

## Starting a new presentation

**Never edit `presentation.tex` directly.** It is the reference showcase — always copy it:

```bash
cp presentation.tex my-talk.tex
```

Work in the new file. `presentation.tex` stays intact as a living reference of all template features.

---

## Questions to ask before authoring a new presentation

**Section color strategy** — ask the user before writing any `mainpoint` frame:

> "Do you want a single color for all section transitions (more formal/unified) or a different color per section (more dynamic/energetic)?"

- **Single color**: same `\setBGColor` on every `mainpoint`. Suits academic, institutional, technical presentations.
- **Per-section color**: one color per section, kept through all frames of that section. Suits talks, workshops, storytelling-driven content.

Do not assume a default — let the user decide once and apply consistently.

## Checklist when writing a bio slide

- Place bio as slide 2 — right after `\titlepage`, before the agenda. Use `\setLayout{horizontal}` (outside any section scope).
- Check if `figs/photo.png` exists. If not, warn the user — `\profilephoto` renders a hexagon with initials until the photo is added.
- Ask the user for their initials to pass as the 3rd arg: `\profilephoto[3.2cm]{figs/photo.png}{FL}`

---

## Vertical Space Budget

Beamer 16:9 slides have ~96mm total height. After decorations and frametitle, usable vertical space:

| Layout | Usable height | Notes |
|---|---|---|
| `vertical` | ~7.0cm | Sidebar on right, frametitle top |
| `horizontal` | ~5.5cm | Bottom bar reduces height significantly |
| `blank` | ~8.0cm | No decorations |
| `mainpoint` | title only | Body content silently ignored |

**Hard limits per frame:**

| Element | vertical | horizontal |
|---|---|---|
| Bullet items (single column) | ≤ 5 | ≤ 4 |
| Bullet items per column (two-col) | ≤ 4 | ≤ 3 |
| Stacked blocks | ≤ 3 | ≤ 2 |
| Block text lines per block | ≤ 3 | ≤ 2 |

When content exceeds budget: split into two slides, shorten bullet text to one line, or replace stacked blocks with a table.

## Text Fitting Guidelines

Content must fit within the layout — never let text overflow margins. Strategies:

| Situation | Fix |
|---|---|
| Title too long on titlepage | Break with `\\`; title moves up automatically |
| Many authors on titlepage | Use multiple `\inst{}` — Beamer splits horizontally |
| `\stat` label overflows column | Shorten label text; use `\footnotesize` override if needed |
| Block text too long | Trim prose; split into two slides |
| Table too wide | Wrap in `\resizebox{\textwidth}{!}{...}` |

Prefer short labels — especially inside `\stat{}{}` and table cells.

---

## Core Constraint

`\textwidth` ≈ **80% of `\paperwidth`** (left margin 5% + right margin 15%).  
**Always size content relative to `\textwidth`, never `\paperwidth`.**

---

## Layouts

| Layout | Visual marker | Text color | Safe content area |
|---|---|---|---|
| `vertical` | Right sidebar (~20% width) | Dark | `\textwidth` (80% of slide) |
| `horizontal` | Bottom bar (~12% height) | Dark | `\textwidth`, limited height |
| `blank` | None — solid color bg | **White** | Full `\textwidth` |
| `mainpoint` | None — solid bg + overlay | **White** | Title only (via `\frametitle{}`) |
| `titlepage` | Wide right sidebar + bottom bar | White | Use only with `\titlepage` |

`\setLayout{name}` persists to all following frames until changed.

### Layout selection

```
Type of slide?
├── title              → titlepage  (\frame[noframenumbering]{\titlepage})
├── section transition → mainpoint + \setBGColor{}
├── normal content     → vertical (default)
├── two columns / diagram beside text → horizontal
└── emphasis / color (stat, closing)  → blank + \setBGColor{}
```
- **mainpoint** → section transition only — body content is silently ignored

### Logo Color Rule

**White variant** → logo on colored/dark surface (sidebar, bottom bar, `blank`/`mainpoint` bg).  
**Black or color variant** → logo in content area with white/light background (bio slide, acknowledgement).

---

## Commands

```latex
\setLayout{vertical}            % vertical | horizontal | blank | mainpoint | titlepage
\setBGColor{DarkOrange}         % changes bgcolor (persists until changed)
\setPrimaryColor{UFGBlue}       % preamble only
\setLogos{title.png}{slide.png} % preamble only
```

---

## Color Palette

| Name | Use |
|---|---|
| `UFGBlue` | Primary — links, borders, emphasis |
| `INFBlue` | Alternate primary |
| `Ocean` | Teal — accent, diagrams |
| `DarkOrange` | Alert/highlight — alertblock border |
| `LightOrange` | Softer highlight |
| `DarkGreen` | Positive/example — examples block border |
| `LightGreen` | Softer green |
| `DarkPurple` | Accent |
| `LightPurple` | Softer accent |
| `DarkGray` | Neutral dark |
| `LightGray` | Neutral mid |
| `VeryLightGray` | Code block background |

Color mixing works: `UFGBlue!60`, `DarkOrange!80!black`.  
Custom colors: `\definecolor{MyColor}{RGB}{r,g,b}` in preamble — compatible with all commands.

---

## Section Slides

### Automatic (recommended)

Add to preamble:
```latex
\AtBeginSection[]{%
    \setLayout{mainpoint}%
    \setBGColor{\currentsectioncolor}%
    \begin{frame}[noframenumbering]{}%
        \frametitle{\insertsectionhead}%
    \end{frame}%
    \setLayout{vertical}%
}
```

Use `\sectionslide` instead of `\section`:
```latex
\sectionslide[DarkPurple]{Section Title}   % color optional — defaults to DarkGray
\sectionslide{Another Section}             % uses DarkGray
```

`\setBGColor` persists through all frames of a section. Convention: pick one color per section for visual identity; change only on the next `\sectionslide`.

### Manual

```latex
\setLayout{mainpoint}
\setBGColor{DarkPurple}
\begin{frame}{}
    \frametitle{Section Title}
\end{frame}
\setLayout{vertical}   % always reset after
```

---

## Block Patterns

**Use blocks sparingly.** Blocks are for highlights — key takeaways, warnings, recommendations. Regular content (lists, results, steps) stays as bullet points. A slide full of blocks loses hierarchy and feels noisy.

| Environment | Border | Use for |
|---|---|---|
| `\begin{block}{Title}` | PrimaryColor | Key takeaway, definition, summary |
| `\begin{alertblock}{Title}` | DarkOrange | Warnings, risks, tensions |
| `\begin{recommendationblock}{Title}` | DarkGreen | Recommendations, best practices |
| `\begin{examples}` | DarkGreen | Built-in Beamer — literal examples, auto-translated title |

**When NOT to use a block:** listing results, describing steps, presenting background — use `\begin{itemize}` instead.

```latex
% Untitled block
\begin{block}{}  content  \end{block}

% Stacked blocks
\begin{block}{What works}  ...  \end{block}
\vspace{0.8em}
\begin{alertblock}{The risk}  ...  \end{alertblock}
\vspace{0.8em}
\begin{recommendationblock}{Recommendation}  ...  \end{recommendationblock}
```

Blocks inside `blank` layout render correctly — body text color is always DarkGray regardless of white config.

---

## Column Patterns

**Every frame with `\begin{columns}` MUST have `\setLayout{horizontal}` immediately before `\begin{frame}`.** `\AtBeginSection` resets to `\setLayout{vertical}` — set horizontal explicitly every time.

```latex
% Symmetric comparison
\setLayout{horizontal}
\begin{frame}{Title}
    \begin{columns}
        \column{0.5\textwidth}
        ...
        \column{0.5\textwidth}
        ...
    \end{columns}
\end{frame}

% Asymmetric text + image
\setLayout{horizontal}
\begin{frame}{Title}
    \begin{columns}
        \column{0.6\textwidth}
        ...
        \column{0.4\textwidth}
        \begin{center}
            \includegraphics[width=0.9\textwidth]{figs/figure.png}
        \end{center}
    \end{columns}
\end{frame}

% Bio slide
\setLayout{horizontal}
\begin{frame}{Who am I}
    \begin{columns}
        \column{0.6\textwidth}
        ...
        \column{0.4\textwidth}
        \begin{center}
            \profilephoto[3.5cm]{figs/photo.png}{FL}
        \end{center}
    \end{columns}
\end{frame}
```

**Width rule:** column widths must sum ≤ `\textwidth`. Never use `\paperwidth` as base.

### \profilephoto

```latex
\profilephoto[3.5cm]{figs/photo.png}{FL}
```

- 3rd arg = initials shown when file is missing (e.g. `FL` for "First Last").
- File exists → image clipped to hexagon with PrimaryColor border.
- File missing → PrimaryColor hexagon with white initials (intentional placeholder).
- Convention: always use `figs/photo.png` as path.

---

## Stat Display

```latex
\begin{columns}[c]
    \column{0.3\textwidth}  \stat{73\%}{of teams adopted AI}
    \column{0.03\textwidth} \statsep
    \column{0.3\textwidth}  \stat{12x}{faster code generation}
    \column{0.03\textwidth} \statsep
    \column{0.3\textwidth}  \stat{3 months}{average adoption time}
\end{columns}
```

Widths: 3×0.30 + 2×0.03 = 0.96 ≤ `\textwidth`. Use in `blank` layout.

---

## Quote Block

```latex
\quoteblock{Quote text here.}{Author, Year}
```

Thick PrimaryColor left border, italic text, attribution right-aligned. Vertically centered on frame. Use on `vertical` or `blank`.

---

## Code Listing

Add to preamble: `\usepackage{listings}`

```latex
\begin{frame}[fragile]{Title}
    \begin{lstlisting}[language=Python, caption=Example]
def process(data):
    return [transform(x) for x in data]
    \end{lstlisting}
\end{frame}
```

Theme-matching `\lstset` activates automatically. Inline: `\lstinline|code|`.

---

## Table Styling

**Large or results tables deserve their own slide** — no competing content. Split if a table shares space with blocks or bullets.

**`blank` layout works well for results tables** — removes sidebar/bar decorations and focuses attention on the data. Text color inside `tabular` is always forced to DarkGray by the theme regardless of layout.

```latex
\begin{table}[]
    \centering
    \caption{Caption}
    \renewcommand{\arraystretch}{1.5}
    \setlength{\tabcolsep}{10pt}
    {\rowcolors{2}{}{LightGray!10}
        \begin{tabular}{p{3cm}p{3cm}p{3cm}}
            \toprule
            \textbf{H1} & \textbf{H2} & \textbf{H3} \\
            \midrule
            ...
            \bottomrule
        \end{tabular}
    }
\end{table}
```

No vertical lines. Sum of `p{...}` widths ≤ ~12cm for 16:9 vertical layout.

---

## TikZ Diagrams

Add to preamble: `\usetikzlibrary{positioning}`

### Reusable node styles

```latex
% Org-chart / hierarchy
rect/.style={rectangle, rounded corners=5pt, minimum height=0.72cm,
             align=center, font=\small\bfseries, text=white}
arr/.style={->, thick, color=gray!50}
darr/.style={->, thick, dashed, color=UFGBlue!60}   % secondary/implied relation

% Triangle / balance diagrams
vnode/.style={circle, minimum size=1.9cm, align=center,
              font=\scriptsize\bfseries, text=white}
```

### Hierarchy diagram (vertical layout)

```latex
\begin{center}
\begin{tikzpicture}[rect/.style={...}, arr/.style={...}]
    % Rows at y = 3.2, 2.2, 1.2 — safe node width: up to 9.5cm
    \node[rect, fill=DarkOrange, minimum width=9.5cm] (top) at (0, 3.2) {Top Level};
    \node[rect, fill=UFGBlue,    minimum width=4.5cm] (l)   at (-2.6, 2.2) {Left};
    \node[rect, fill=DarkPurple, minimum width=4.5cm] (r)   at (2.6, 2.2) {Right};
    \draw[arr] (top.south) -- ++(0,-0.15) -| (l.north);
    \draw[arr] (top.south) -- ++(0,-0.15) -| (r.north);
\end{tikzpicture}
\end{center}
\vspace{0.2em}
\begin{block}{}
    Explanatory text.
\end{block}
```

### Triangle / balance diagram (inside column)

```latex
\begin{tikzpicture}[vnode/.style={...}]
    \coordinate (A) at (0,    3.2);
    \coordinate (B) at (-2.4, 0.3);
    \coordinate (C) at ( 2.4, 0.3);
    \draw[thick, gray!35] (A) -- (B) -- (C) -- cycle;
    \node[vnode, fill=UFGBlue]    at (A) {Label A};
    \node[vnode, fill=DarkOrange] at (B) {Label B};
    \node[vnode, fill=DarkGreen]  at (C) {Label C};
\end{tikzpicture}
```

### Height budget

- Full-width hierarchy (4 rows) fits ~3.5cm → leaves ~3cm for a block below (vertical layout)
- Diagram inside `0.45\textwidth` column can be taller — no full-width constraint

### Colors in TikZ

Template palette is global — use directly:
```latex
fill=UFGBlue  fill=DarkOrange  fill=DarkPurple  fill=DarkGreen  fill=DarkGray
fill=DarkOrange!80!black   fill=UFGBlue!55   % mixing works anywhere xcolor is accepted
```

---

## Common Mistakes

| Mistake | Fix |
|---|---|
| Two-column slide in `vertical` layout | Use `\setLayout{horizontal}` |
| `blank` for regular list/text content | `blank` = emphasis only (stat, closing) |
| `\column{0.5\paperwidth}` | Use `\column{0.5\textwidth}` |
| Body content in `mainpoint` frame | Only `\frametitle{}` renders — body is ignored |
| Forgetting `\setLayout` after `blank`/`mainpoint` | Color persists — always reset |
| `\includegraphics[width=\paperwidth]` | Use `width=\textwidth` |
| Missing `\usetikzlibrary{positioning}` | Add to preamble for TikZ node positioning |
| `lstlisting` inside a `block` | Won't compile — `block` uses `tabular` internally, verbatim env incompatible. Place `lstlisting` directly in frame, outside block. |
| Too many items/blocks in `horizontal` | Bottom bar cuts usable height to ~5.5cm. Max 4 items per column, max 2 stacked blocks. Split into two slides if needed. |
| Long bullet text wrapping to 2+ lines | Each item must fit in one line. Shorten or remove — slides are not documents. |
| Table text white on `blank` layout | Theme forces DarkGray inside tabular — this is handled automatically. |
