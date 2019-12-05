![UFGTeXPresentation logo](https://raw.githubusercontent.com/deuslirio/UFGTeX-Presentation/master/readme/ufgtexpresentation.png)

## What is it?
A Latex template to help students, professors, or researchers from Universidade Federal de Goiás (UFG) to prepare their presentation slides in the **format 16:9**. This template is based on the version available in the Google Slides at [here](https://docs.google.com/presentation/d/1NSXSP5SnpIE0fsVCebAj9x2UfSAlGvlGEEt0zA_y2aE). Besides presenting a modern design concept, UFGTeXPresentation provides different slides’ layouts and color schemas to personalize the presentation.

![Template example](https://raw.githubusercontent.com/deuslirio/UFGTeX-Presentation/master/readme/title_layout_print.png)

## How to use
After downloading or cloning this repository, you must edit the file **presentation.tex** to fill the content of the presentation. Firstly, take a look at the "Primary Definitions" part, at the begin of such a **.tex**, and modify its parties, whether is needed. if you compile the code without changing, it will look like [this](https://github.com/deuslirio/UFGTeX-Presentation/blob/master/figs/UFGTeX_Presentation.pdf). 

**To set the default color** of the presentation, you can use the command `\setPrimaryColor{color}`. This command supports one of the colors defined by the template or any color defined by the user.  

```tex
\setPrimaryColor{UFGBlue} 
```

**To set the logo** of the department or institute, from the authors take part, you must use the command `\setLogos{path/horizontal_logo}{path/squared_logo}` to inform the paths of two files. The first one is the logo in title slide - we recommend using a horizontal image - and the second one is the logo used in the remaining slides - we recommend using a square image.
```tex
\setLogos{lib/logos/infw.png}{lib/logos/infw2.png} 
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

| Color Name    | RGB         | Color Name  | RGB          |
|---------------|-------------|-------------|--------------|
| INFBlue       | 0, 92, 161  | DarkOrange  | 255, 152, 0  |
| UFGBlue       | 0, 114, 185 | LightOrange | 255, 193, 7  |
| PrimaryColor | 33, 33, 33  | DarkGreen   | 91, 141, 8   |
| DarkGray      | 33, 33, 33    | LightGreen  | 122, 188, 12 |
| LightGray     | 150, 150, 150 | LightPurple | 191, 83, 219 |
| Ocean         | 129, 194, 234 | DarkPurple  | 142, 36, 170 |

Despite the colors defined in the template, one can define his/her personalized color by using the following command:
```tex
% First parameter is the color name and the last one is the RGB code of the color
\definecolor{ColorName}{RGB}{0,0,0} 
```

## Template's Layouts
At this momment, UFGTeXPresentation has five option for slides' layout: **titlepage, vertical, horizontal, mainpoint,** and **blank**. You can see each layout appearance at the following figure:  
 ![Template example](https://raw.githubusercontent.com/deuslirio/UFGTeX-Presentation/master/readme/layouts.png) 

## Summary of the Template's commands

| Template Commands  | Number of Params | Type of Params | Example                                            |
|--------------------|------------------|----------------|----------------------------------------------------|
| setLayout          | 1                | Layout         | \setLayout{vertical}                               |
| setBGColor         | 1                | Color          | \setBGColor{DarkPurple}                            |
| setPrimaryColor    | 1                | Color          | \setPrimaryColor{UFGBlue}                          |
| setLogos           | 2                | Image URL      | \setLogos{lib/logos/infw.png}{lib/logos/infw2.png} |

## UFGTeXPoster on Overleaf

This project was fully developed on the [Overleaf](https://www.overleaf.com), an online LaTeX editor that has joined with another service called ShareLatex. Therefore, if you prefere working online in one of the services above, you may find UFGTexPresentation available in the official Overleaf's templates gallery at [here](https://www.overleaf.com/latex/templates/ufgtex-presentation/zhvynsrvwnrg).

## Other UFG Latex Template

- [UFGTeXPoster](https://github.com/altinodantas/ufgtexposter)

## Disclaimer

This project is a personal initiative, under open source and collaborative principles, which until now has no formal association with the Federal University of Goiás institution. Thus, this template is not an official artifact from such a university.

> If you have some comments or suggestion, let we know by sending email to deuslirio.junior@gmail.com or tinodantas@gmail.com.
