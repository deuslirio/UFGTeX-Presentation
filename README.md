![UFGTeXPresentation logo](https://raw.githubusercontent.com/deuslirio/UFGTeX-Presentation/master/readme/ufgtexpresentation.png)

## What is it?
A Latex template to help students, professors and/or researchers from Universidade Federal de Goiás (UFG) preparing their 
presentation slides in the format 16:9. The template provides different options to change its visual aspect as well as shows examples
of exposing images, tables, and bibliography references.

![Template example](https://raw.githubusercontent.com/deuslirio/UFGTeX-Presentation/master/readme/title_layout_print.png)

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
\definecolor{ColorName}{RGB}{0,0,0}
```

## Layout Options
  - titlepage
  - vertical
  - horizontal
  - mainpoint
  - blank
  
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

If you have some comments or suggestion, let me know by sending email to deuslirio@gmail.com.
