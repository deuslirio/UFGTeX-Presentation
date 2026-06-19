![UFGTeXPresentation logo](https://raw.githubusercontent.com/deuslirio/UFGTeX-Presentation/master/readme/ufgtexpresentation.png)

## What is it?
A Latex template to help students, professors, or researchers from Universidade Federal de Goiás (UFG) to prepare their presentation slides in the **format 16:9**. This template is based on the version available in the Google Slides at [here](https://docs.google.com/presentation/d/1NSXSP5SnpIE0fsVCebAj9x2UfSAlGvlGEEt0zA_y2aE). Besides presenting a modern design concept, UFGTeXPresentation provides different slides’ layouts and color schemas to personalize the presentation.

![Template example](https://raw.githubusercontent.com/deuslirio/UFGTeX-Presentation/master/readme/title_layout_print.png)

## How to use
After downloading or cloning this repository, **copy** `presentation.tex` to a new file (e.g. `my-talk.tex`) and edit that copy. `presentation.tex` is a living reference showcase of all template features — keep it intact. Compile without changes to see [what it looks like](https://github.com/deuslirio/UFGTeX-Presentation/blob/master/figs/UFGTeX_Presentation.pdf).

**To set the default color** of the presentation, use `\setPrimaryColor{color}`. Supports any template color or a user-defined color.

```tex
\setPrimaryColor{UFGBlue} 
```

**To set the logo** use `\setLogos{path/title_logo}{path/slide_logo}`. First path is used on the title slide, second on all other slides.
```tex
\setLogos{lib/logos/INF-full-white.png}{lib/logos/INF-compact-white.png} 
```

**To define a layout** for a slide, you must use the command `\setLayout{layoutname}`, just informing the name of the layout you would like to use. This command must be placed before the command `\begin{frame}` of the slide you would like to change.  

```tex
\setLayout{horizontal} 
\begin{frame}
  \frametitle{Table of Contents}
  \tableofcontents
\end{frame}
```  

**To define a color for the background** of a slide, you must use the command `\setBGColor{color}` informing a color. This command must be placed before the command `\begin{frame}` of the slide you would like to change. The color may be one of the template’s colors or a personalized color defined by the user. 

```tex
\setBGColor{DarkOrange}
\begin{frame}
\frametitle{Pause Example}

    \begin{itemize}
        \item In this slide \pause
        \item the text will be partially visible \pause
        \item And finally everything will be there
    \end{itemize}

\end{frame}
```

```tex
\definecolor{MyColor}{RGB}{10, 115, 110} 
\setBGColor{MyColor}
\begin{frame}
  % ... 
\end{frame}
```

> **ATTENTION:** When you use the commands `\setLayout` and `\setBGColor`, all later slides are affected. Thus, if you want to return to a previous layout or color, you must reuse the commands just before the intendant slide.


## Template's Colors

| Color Name    | RGB           | Hex       |
|---------------|---------------|-----------|
| UFGBlue       | 0, 114, 185   | #0072B9   |
| INFBlue       | 0, 92, 161    | #005CA1   |
| DarkOrange    | 255, 152, 0   | #FF9800   |
| LightOrange   | 255, 193, 7   | #FFC107   |
| DarkGreen     | 91, 141, 8    | #5B8D08   |
| LightGreen    | 122, 188, 12  | #7ABC0C   |
| DarkPurple    | 142, 36, 170  | #8E24AA   |
| LightPurple   | 191, 83, 219  | #BF53DB   |
| Ocean         | 129, 194, 234 | #81C2EA   |
| DarkGray      | 33, 33, 33    | #212121   |
| LightGray     | 150, 150, 150 | #969696   |
| VeryLightGray | 249, 249, 249 | #F9F9F9   |

Despite the colors defined in the template, one can define his/her personalized color by using the following command:
```tex
% First parameter is the color name and the last one is the RGB code of the color
\definecolor{ColorName}{RGB}{0,0,0} 
```

## Template's Layouts
At this momment, UFGTeXPresentation has five option for slides' layout: **titlepage, vertical, horizontal, mainpoint,** and **blank**. You can see each layout appearance at the following figure:  
 ![Template example](https://raw.githubusercontent.com/deuslirio/UFGTeX-Presentation/master/readme/layouts.png) 

## Summary of the Template's commands

| Command           | Params | Example                                                        |
|-------------------|--------|----------------------------------------------------------------|
| `\setLayout`      | 1      | `\setLayout{vertical}` — vertical, horizontal, blank, mainpoint, titlepage |
| `\setBGColor`     | 1      | `\setBGColor{DarkPurple}`                                      |
| `\setPrimaryColor`| 1      | `\setPrimaryColor{UFGBlue}` — preamble only                    |
| `\setLogos`       | 2      | `\setLogos{lib/logos/INF-full-white.png}{lib/logos/INF-compact-white.png}` |
| `\section`        | 1 + optional color + optional short title | `\section[DarkPurple]{Section Title}` · `\section[UFGBlue][Short]{Long Title}` |
| `\profilephoto`   | 2 + optional size  | `\profilephoto[3.2cm]{figs/photo.png}{FL}`           |
| `\stat`           | 2      | `\stat{73\%}{teams adopted AI}` — large metric display         |
| `\statsep`        | 0      | vertical rule separator between `\stat` columns                |
| `\quoteblock`     | 2      | `\quoteblock{Quote text.}{Author, Year}`                       |

## AI Assistant Support

This template includes guides for AI assistants:

- **`AGENTS.md`** — universal guide for any AI assistant (Claude, Copilot, Cursor, Gemini). Contains layout rules, block patterns, color palette, column constraints, TikZ patterns, and common mistakes. Read automatically by assistants that support project-level context files.

- **`.claude/skills/`** — Claude Code skill that activates automatically when editing slides. Provides interactive checklists (bio photo, section color strategy) and detailed generation guidance on top of `AGENTS.md`.

Both files are kept in sync. To start a new presentation, copy `presentation.tex` rather than editing it directly — it serves as the living reference showcase.

## UFGTeX-Presentation on Overleaf

This project was fully developed on [Overleaf](https://www.overleaf.com). You may find UFGTeX-Presentation available in the official Overleaf templates gallery [here](https://www.overleaf.com/latex/templates/ufgtex-presentation/zhvynsrvwnrg).

## Other UFG Latex Template

- [UFGTeXPoster](https://github.com/altinodantas/ufgtexposter)

## Disclaimer

This project is a personal initiative, under open source and collaborative principles, which until now has no formal association with the Federal University of Goiás institution. Thus, this template is not an official artifact from such a university.

> If you have some comments or suggestion, let we know by sending email to deuslirio.junior@gmail.com or tinodantas@gmail.com.
