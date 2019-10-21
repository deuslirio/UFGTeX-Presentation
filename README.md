![UFGTeXPresentation logo](https://raw.githubusercontent.com/deuslirio/UFGTeX-Presentation/master/readme/ufgtexpresentation.png)

## What is it?
A Latex template to help students, professors, or researchers from Universidade Federal de Goiás (UFG) to prepare their presentation slides in the format 16:9. Besides presenting a modern design concept, UFGTeXPresentation provides different slides’ layout and color schemas to personalize the presentation.

![Template example](https://raw.githubusercontent.com/deuslirio/UFGTeX-Presentation/master/readme/title_layout_print.png)

## How to use
After downloading or cloning this repository, you must edit the file **presentation.tex** to fill the content of the presentation. Firstly, take a look at the "Primary Definitions" part, at the begin of such a **.tex**, and modify its parties, whether is needed. 

To set the default color of the presentation, one may use the command \setPrimaryColor{color}. This command supports one of the colors defined by the template or any color defined by the user.  

To set the logo of the department or institute, from the authors take part,  one must use the command \setLogos{}{} to inform paths of two files. The first one is logo in title slide - we recommend using a horizontal image - and second one is the logo used in the remaining slides - we recommend using a square image.


## Table of colors

| Color Name    | RGB         | Color Name  | RGB          |
|---------------|-------------|-------------|--------------|
| INFBlue       | 0, 92, 161  | DarkOrange  | 255, 152, 0  |
| UFGBlue       | 0, 114, 185 | LightOrange | 255, 193, 7  |
| PrimmaryColor | 63, 63, 63  | DarkGreen   | 91, 141, 8   |
| DarkGray      | 63,63,63    | LightGreen  | 122, 188, 12 |
| LightGray     | 150,150,150 | LightPurple | 191, 83, 219 |
| Ocean         | 129,194,234 | DarkPurple  | 142, 36, 170 |

Despite the colors defined in the template, one can define his/her personalized color by using the following command:
```tex
\definecolor{ColorName}{RGB}{0,0,0} % First parameter is the color name and the last one is the RGB code of the color
```

## Layout names
At this momment, UFGTeXPresentation has five option for slides' layout:
  - titlepage
  - vertical
  - horizontal
  - mainpoint
  - blank

Each Layout seens like the following figure:  
 ![Template example](https://raw.githubusercontent.com/deuslirio/UFGTeX-Presentation/master/readme/layouts.png) 

## Table of commands

| Template Commands  | Number of Params | Type of Params | Example                                            |
|--------------------|------------------|----------------|----------------------------------------------------|
| setLayout          | 1                | Layout         | \setLayout{vertical}                               |
| setBGColor         | 1                | Color          | \setBGColor{DarkPurple}                            |
| setPrimaryColor    | 1                | Color          | \setPrimaryColor{UFGBlue}                          |
| setLogos           | 2                | Image URL      | \setLogos{lib/logos/infw.png}{lib/logos/infw2.png} |

## Other Latex Template

- [UFGTeXPoster](https://github.com/altinodantas/ufgtexposter)

## Disclaimer

This project is a personal initiative, under open source and collaborative principles, which until now has no formal association with the Federal University of Goiás institution. Thus, this template is not an official artifact from such a university.

If you have some comments or suggestion, let we know by sending email to deuslirio.junior@gmail.com or tinodantas@gmail.com.
