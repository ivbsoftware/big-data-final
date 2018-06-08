# Preparing APA Journal Articles in Windows
Preparation of APA-style article for this project is done with help of [papaja](https://github.com/crsh/papaja) package for RStudio. 
This document describes the environment and the procedure.

## Installation
The following software is required (get the latest, always choose 64-bit versions where there is a choice):
- Install [7-Zip](https://www.7-zip.org/) to extract the tar.gz files.
- Install [R](https://cran.r-project.org/).
- Install [RStudio](https://www.rstudio.com/products/rstudio/download/).
- Install [MikTex](https://miktex.org/) - TeX/LaTeX typesetting system for Microsoft Windows. 
- Install [PanDoc](http://pandoc.org/getting-started.html) - command-line tool to convert files from one markup format into another.
- Launch RStudio desktop.
- In RStudio  console execute the following:
```
> install.packages(c("devtools","afex","lsmeans","MBESS","testthat","rmarkdown","ggplot2","matlib"))
> devtools::install_github("crsh/papaja")
```
- *Optional:* Download [papaja](https://socialsciences.mcmaster.ca/jfox/Courses/R/ICPSR/R-install-instructions.html) and use it to create new APA-style articles.

## Compiling the big-final-data report
Assuming that you downloaded a *[big-final-data](https://github.com/ivbsoftware/big-data-final)* repository from Github:
- Launch RStudio desktop.
- Use 'Open' menu to open **final-project-group1.rmd** file in RSTudio.
- In the file window toolbar, click "Knit" down arrow and then click 'Knit to apab6_pdf' item. If the Word formad is required, line **papaja::apa6_pdf** in the **final-project-group1.rmd** file should be changed to **papaja::apa6_word**.

## *To be continued...*
