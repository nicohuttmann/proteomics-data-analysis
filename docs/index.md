--- 
title: "Proteomics Data Analysis in R"
author: "Nico Hüttmann"
date: "2025-06-03"
site: bookdown::bookdown_site
documentclass: book
bibliography: [book.bib, packages.bib]
# url: your book url like https://bookdown.org/yihui/bookdown
# cover-image: path to the social sharing image like images/cover.jpg
description: |
  Handbook for Proteomics Data Analysis in R . 
biblio-style: apalike
csl: chicago-fullnote-bibliography.csl
---



# Preface {-}

Hi y'all, welcome to this little collection of workflows, code snippets, and ideas for proteomics data analysis. Written by me, for me,^[I am losing control over all the different scripts and stuff.] but hopefully useful to you as well!

This is the nth attempt of producing something coherent and useful over a longer period of time.^[see the first version [here](https://nicohuttmann.github.io/pOmics-handbook/) and my latest try [here](https://nicohuttmann.github.io/embl-bioinfo-pRoteomics/)] We'll see how this goes :)

## Structure {-}



## Acknowledgements {-}

In the [first version](https://nicohuttmann.github.io/pOmics-handbook/introduction.html), I spent plenty of time thanking people and probably less time actually completing what I started. To keep it short, this is only possible thanks to the incredible open and stimulating environment of the [Savitski lab](https://www.embl.org/groups/savitski/) and its [members](https://www.embl.org/groups/savitski/members/). Thanks guys!



# Navigation {-}

The previous page describes this as a collection of things, but motivated by workshops in the past, it'll contain some introductory content as well.^[It looks nicer and feels more complete.]

If you...

- are new to R or would like a short refresher, head to [R Basics](#r-and-rstudio)^[10 points for Gryffindor if you find the hidden message]

- want to analyze your first proteomics dataset, start with 

- fancy some functional insights into your biological system, 

- look for an oddly specific solution for 

- feel the need to look at your raw mass spec data, please enjoy [Raw MS Data](#raw-ms-data)

- wanna browse some random pieces of code and other ideas, [here you go]()^[Yes, I use this as a blog.]

- like the style of this book, copy [this Github repository]() and modify it, or read about it [here]()

- are still not satisfied, use the search function in the top left corner. Maybe you are lucky!






<!-- ## Blocks -->

<!-- ## Equations -->

<!-- Here is an equation. -->

<!-- \begin{equation}  -->
<!--   f\left(k\right) = \binom{n}{k} p^k\left(1-p\right)^{n-k} -->
<!--   (\#eq:binom) -->
<!-- \end{equation}  -->

<!-- You may refer to using `\@ref(eq:binom)`, like see Equation \@ref(eq:binom). -->


<!-- ## Theorems and proofs -->

<!-- Labeled theorems can be referenced in text using `\@ref(thm:tri)`, for example, check out this smart theorem \@ref(thm:tri). -->

<!-- ::: {.theorem #tri} -->
<!-- For a right triangle, if $c$ denotes the *length* of the hypotenuse -->
<!-- and $a$ and $b$ denote the lengths of the **other** two sides, we have -->
<!-- $$a^2 + b^2 = c^2$$ -->
<!-- ::: -->

<!-- Read more here <https://bookdown.org/yihui/bookdown/markdown-extensions-by-bookdown.html>. -->

<!-- ## Callout blocks -->


<!-- The `bs4_book` theme also includes special callout blocks, like this `.rmdnote`. -->

<!-- ::: {.rmdnote} -->
<!-- You can use **markdown** inside a block. -->

<!-- ```{r collapse=TRUE} -->
<!-- head(beaver1, n = 5) -->
<!-- ``` -->

<!-- ::: -->

<!-- It is up to the user to define the appearance of these blocks for LaTeX output.  -->

<!-- You may also use: `.rmdcaution`, `.rmdimportant`, `.rmdtip`, or `.rmdwarning` as the block name. -->


<!-- The R Markdown Cookbook provides more help on how to use custom blocks to design your own callouts: https://bookdown.org/yihui/rmarkdown-cookbook/custom-blocks.html -->






<!-- This is an introduction to R -->

<!-- ```{r } -->
<!-- 1 + 4 -->
<!-- ``` -->

<!-- ```{r} -->
<!-- b <- 5 -->
<!-- ``` -->

<!-- ```{r} -->
<!-- sqrt(4) -->
<!-- ``` -->

<!-- ```{r} -->
<!-- ?round -->

<!-- round(2.576, digits = 2) -->
<!-- ``` -->

<!-- ```{r} -->
<!-- library(tidyverse) -->
<!-- ``` -->

<!-- ```{r} -->
<!-- mice_pheno <- read_csv(file= url("https://raw.githubusercontent.com/genomicsclass/dagdata/master/inst/extdata/mice_pheno.csv")) -->

<!-- mice_pheno$Bodyweight <- as.numeric(mice_pheno$Bodyweight) -->
<!-- ``` -->


<!-- ```{r} -->
<!-- head(mice_pheno) -->

<!-- dim(mice_pheno) -->

<!-- str(mice_pheno) -->
<!-- ``` -->


<!-- ```{r} -->
<!-- mice_pheno[1:2, 3] -->
<!-- ``` -->


<!-- ```{r} -->
<!-- print(names(PlantGrowth)) -->
<!-- PlantGrowth$weight -->

<!-- PlantGrowth[, "weight"] -->
<!-- ``` -->


<!-- ```{r} -->
<!-- table(mice_pheno$Sex) -->
<!-- ``` -->

<!-- ```{r} -->
<!-- mice_female <- mice_pheno %>%  -->
<!--   filter() -->
<!-- ``` -->



<!-- ```{r} -->
<!-- mice_pheno %>%  -->
<!--   ggplot(aes(x = Diet, y = Bodyweight, fill = Sex)) +  -->
<!--   geom_boxplot() -->
<!--   ggforce::geom_sina() -->
<!-- ``` -->


<!-- kjdslkfjdsj -->
<!-- ```{r} -->
<!-- mice_pheno %>%  -->
<!--   mutate(rep = row_number(), .by = c("Sex", "Diet")) %>%  -->
<!--   pivot_wider(id_cols = c("Sex", "rep"),  -->
<!--               names_from = "Diet",  -->
<!--               values_from = "Bodyweight") -->
<!-- ``` -->

<!-- ::: {.rmdnote} -->



<!-- ::: -->

<!-- <button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button1" aria-expanded="false" aria-controls="button1"> Hint </button> <div id="button1" class="collapse">   -->
<!-- \ -->

<!-- </div> -->

<!-- <button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button2" aria-expanded="false" aria-controls="button2"> Code </button> <div id="button2" class="collapse">   -->
<!-- \ -->

<!-- ```{r} -->

<!-- ``` -->

<!-- We can do the same in a condensed way. -->
<!-- ```{r} -->

<!-- ``` -->
<!-- </div> -->

