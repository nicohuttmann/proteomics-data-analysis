# (PART\*) R Basics {-} 




# R and RStudio

>"R is ‘GNU S’, a freely available language and environment for statistical computing and graphics which provides a wide variety of statistical and graphical techniques: linear and nonlinear modelling, statistical tests, time series analysis, classification, clustering, etc."

This is the description of R on the R website. 

## Install the R language

Download the most recent release of R for your platform from https://cloud.r-project.org/. Install it like any other program. It is important to install R before RStudio.


## Install RStudio

RStudio is an integrated development environment (IDE) for R. Other IDEs do exist, but RStudio is the software of choice by far. Like, by far. Download the desktop version of RStudio from https://www.rstudio.com/products/rstudio/. This is the program in which you will interact with the R language and conduct all your analyses.

# How does R work?

> “To understand computations in R, two slogans are helpful:
Everything that exists is an object.
Everything that happens is a function call." — John Chambers^[[Chambers, 2007](https://books.google.de/books?id=kxxjDAAAQBAJ&pg=PA4&lpg=PA4&dq=%22Everything+that+exists+in+R+is+an+object%22&source=bl&ots=c6AiUD6NXp&sig=NiI4WlvJBolTQ3jSVisPIBcm-fU&hl=en&sa=X&redir_esc=y#v=onepage&q=%22Everything%20that%20exists%20in%20R%20is%20an%20object%22&f=false)]

Ok, cool. So what now? Well, this statement tells us that everything in our R code falls into two categories, either it is an object or it is a function (which will most likely take an object as input and give back a modified object in return).

## Objects 

Please have a look at the [Workflow: basics](https://r4ds.hadley.nz/workflow-basics) as a first introduction or recapitulation^[If you are already familiar with all of this, it may help you formalize your problems better by getting familiar with the vocabulary the authors of R use.] into coding in R.

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button1" aria-expanded="false" aria-controls="button1"> Done? </button> <div id="button1" class="collapse">  
\
The most important takeaway from this is that you can assign/create an object in R with the assignment operator `<-`. And while we are at it, the __c__ ombine function `c()`^[which I always called vector, and wondered where the c is coming from...] will be one of the most frequently used functions in R. 

You can simply copy the code below by marking it or pressing this helpful button in the top right corner of the code chunk and paste it into your R script. Then just run the lines of code and have a look at what they produce.

```r
# Assign the vector to an object called numbers
numbers <- c(1, 2, 3)
# Execute the following line to print it to the console
numbers
# Some objects (not this one) need to be forced to show in the console 
print(numbers)
```
This ` c(1, 2, 3) -> numbers` works as well, but please do not ever do this.^[[here](https://stat.ethz.ch/R-manual/R-devel/library/base/html/assignOps.html)'s a list of other assignment operators]
</div>

\
What we have created here is called a vector, and more precisely an atomic vector. This means its elements are all of the same type. You can read more on this in the [Vectors](https://adv-r.hadley.nz/vectors-chap.html) chapter of [Advanced R](https://adv-r.hadley.nz/) if you have some waiting time or if you are unsure about the behavior of your vectors. Examples would be:

```r
mixed_numbers <- c(0, 1, 2, "three")
mixed_numbers_2 <- c(F, TRUE, 2, 3)
# You don't actually need to assign them
c(F, TRUE, 2, "three")
```

If you are unhappy that the type of your data has changed in the previous example, simply change `c()` to `list()`.^[The `typeof()` function comes in handy if you ever need to test if your code does what you think it does.]

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button2" aria-expanded="false" aria-controls="button2"> I am lazy. </button> <div id="button2" class="collapse">  
\

```r
list(0, 1, 2, "three")
list(F, TRUE, 2, 3)
list("these" = F, "are" = TRUE, "names" = 2, "three")
list("and" = F, 
     "they" = TRUE, 
     "work" = 2, 
     "notemptyanymore" = "for both lists and vectors :)")
```
</div>

\
The other data types can be found in the [Vectors](https://adv-r.hadley.nz/vectors-chap.html) chapter as mentioned previously or will be covered throughout the project.  

## Functions 

Besides the most basic object in R, a vector, we have also covered two functions as well. The `c()` and the `list()` functions which allow us to create atomic vector and list objects. If you want to understand a function, simply write `?c`^[question mark + function name] and R will prompt you to the documentation of the function in the Help pane on the bottom right.^[Or google the function like a normal human being.]

The number of functions exceeds the number of object types by far, therefore we should see how to use functions properly. Each function 1. has a name, 2. is an object itself and 3. can be evoked by `()` brakets following its name. Let's try this:

```r
sum(1, 2, 3)
```
Nice! But bad example. Write the function name `sum` again and wait for a list of options to appear. If this does not happen, you can press Tab. Once you see a list, scroll through it with your arrow buttons and choose a function with Tab or Enter. Once your cursor is in between the brackets of the function, press Tab again. Now, you see the arguments of a function. Arguments are the different inputs for a function and declare precisely which input goes where within the function. Our bad example has a special type of argument `...`, the [(dot-dot-dot)](https://adv-r.hadley.nz/functions.html?q=...#fun-dot-dot-dot), that accepts an undefined number of arguments, in this case multiple numbers.

A better example is the `intersect()` function, which takes two sets in form of atomic vectors `x` and `y` and returns the intersection. 

```r
intersect(x = c(1, 2, 3), 
          y = c(2, 3, 4))
```

The other [Set Operation](https://stat.ethz.ch/R-manual/R-devel/library/base/html/sets.html) functions will be useful at one point for sure. Another resource worth mentioning for this example and in generalis the [R-bloggers website](https://www.r-bloggers.com/2024/11/the-complete-guide-to-using-setdiff-in-r-examples-and-best-practices/).

For a formal description of functions, you can read [Function fundamentals](https://adv-r.hadley.nz/functions.html?q=...#function-fundamentals). And now let's see where all these functions come from.


# R packages



>"R packages are collections of functions and data sets developed by the community. They increase the power of R by improving existing base R functionalities, or by adding new ones."^[https://www.datacamp.com/community/tutorials/r-packages-guide] 

Basically, R packages are nothing but collections of functions bundled together in a way that makes sense. Like different cookbooks that only contain recipes for a particular kind of food. They can be installed from many different sources which will be explored below. 

## From CRAN

[The Comprehensive R Archive Network](What are R and CRAN?) (CRAN) package repository features 18,000+ R packages. Here's the list of [Available CRAN Packages By Name](https://cran.r-project.org/web/packages/available_packages_by_name.html). Most general purpose packages can be found here, however due to reasons, some packages are only available from other sources. 

As a first example, we will download the [tidyverse](https://www.tidyverse.org/), a collection of R packages for data science. 

>"The tidyverse is an opinionated collection of R packages designed for data science. All packages share an underlying design philosophy, grammar, and data structures."

We can install packages from CRAN with the `install.packages()` function like this:

```r
install.packages("tidyverse")
```

Note, that we can also download more than one package at once using a vector (`c()`) containing all package names:

```r
install.packages(c("BiocManager", "devtools"))
```

`BiocManager` as well as `devtools` will be used in the following to download R packages from other sources.


## From Bioconductor

The [Bioconductor](https://bioconductor.org/) is a collection of R packages for bioinformatics purposes. The first packages we will need from the Bioconductor will be downloaded with the `install()` function from the `BiocManager` package: 

```r
BiocManager::install(c("fgsea",
                       "org.Hs.eg.db",
                       "UniProt.ws"))
```



## From GitHub and others sources

Another important source of R packages is GitHub. GitHub is not just the place where most R packages are being developed before they are put to repositories such as CRAN or Bioconductor, many other packages including the `PELSA` package can be installed from it as well. 

Here is an example with the `install_github()` function from the `devtools` package. This package is not required yet. 

```r
devtools::install_github("nicohuttmann/PELSA")
```


# The tidyverse

You may have already installed the [`tidyverse`](https://www.tidyverse.org/) in the previous chapter. It is a [collection](https://www.tidyverse.org/packages/) of many R packages made for data science. I see it as a high level dialect - which allows you to do the same as base R 

>"The tidyverse is an opinionated collection of R packages designed for data science. All packages share an underlying design philosophy, grammar, and data structures."

The tidyverse is extensively described in the [R for Data Science (2e)](https://r4ds.hadley.nz) book^[I'm a fan, if you haven't noticed] as recommended in [Learn the tidyverse](https://www.tidyverse.org/learn/) and individual packages are summarized in some [Posit cheatsheets](https://posit.co/resources/cheatsheets/).


# Coding style 

Okay, we nearly made it to our project. One last chapter. I promise. 

One decision which you may have already guessed, is that I am a follower of the tidyverse and try to use it instead of the base R solutions wherever possible.^[base R refers to the functions which are available to you in R without installing any additional package. And little surprisingly, it is a package as well. You could check it's functions by writing `base::`and pressing Tab. _I just found all the basic mathematical operators by doing this and scrolling up. I'm learning so much by doing this!_] Still, it is not almighty and sometimes you will need other solutions. For example dividing two data frames through each other would require the tidyverse functions `pivot_longer`, `inner_join`, `mutate` and `pivot_wider`. The elegant base R solution is having the data as matrices and simply using the mathematical operator `/`. 

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button3" aria-expanded="false" aria-controls="button3"> base R solution </button> <div id="button3" class="collapse">  
\

```r
m1 <-  matrix(1:9, nrow = 3)

m2 <-  matrix(1:9, nrow = 3) * 2

m2 / m1
```
</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button4" aria-expanded="false" aria-controls="button4"> tidyverse solution </button> <div id="button4" class="collapse">  
\

```r
# Making the tibble works slightly different in our exampe 
t1 <- tibble(a = 1:3, b = 4:6, c = 7:9)
# and multiplying each element by 2 gets done with mutate and across. 
# We will get back to this later
t2 <- tibble(a = 1:3, b = 4:6, c = 7:9) %>% 
  # \(x) x * 2 is equivalent to function(x) x * 2
  mutate(across(everything(), \(x) x * 2))

t2 / t1
```

Damn, while writing this example, I found out that what I was trying to show not to work, did somehow work. But let me explain why I don't like the example. 

The structure of an object in R can be found by using the `class()` function. Just try it.


```r
class(m1)

class(m2)

class(m2 / m1)
```

All objects in the base R example are matrices. Let's check the tidyverse example. 


```r
class(t1)

class(t2)

class(t2 / t1)
```

The output of the divide operation is not a `tibble`/"tbl_df" object anymore, it is a `data.frame`. This is not a big problem for now, and can be solved quite easily with the `tibble::as_tibble()` function:

```r
tibble::as_tibble(t2 / t1)
```

However, it is recommended to not change the `class` of your data in such a way during your analysis.

The real tidyverse solution would work the following. The key is that we combine both tibbles into one which allows us to divide the columns through each other in a simple `dplyr::mutate()` operation.


```r
# First we add a row column to the tibbles, this brings them closer to real data 
t1_r <- t1 %>% 
  mutate(row = c("1", "2", "3"), 
         .before = 1)
# Do it again 
t2_r <- t2 %>% 
  mutate(row = c("1", "2", "3"), 
         .before = 1)
# Now we bring our data from a wide format into a long format 
t1_long <- pivot_longer(t1_r, 
                        cols = c("a", "b", "c"), 
                        names_to = "column", 
                        values_to = "number")
# And again 
t2_long <- pivot_longer(t2_r, 
                        cols = -1, 
                        names_to = "column", 
                        values_to = "number")

# We start with combining the data frames by matching both tibbles by the 
# columns "row" and "column" and choosing a suffing for overlapping column names
full_join(t1_long, t2_long, by = c("row", 
                                   "column"), 
          suffix = c("_1", "_2")) %>% 
  # Then we can divide the values of t2 by t1 and save them in a new column 
  mutate(number = number_2 / number_1) %>% 
  # Now we finally pivot back to the wide data format from the beginning
  pivot_wider(id_cols = "row", 
              names_from = "column", 
              values_from = "number")
```

This seems like a very tedious example in comparison, but also bears it's advantages as we will see later. 

Btw, this is how I would've done the above in a code-condensed form. 


```r
# First we put the tibbles in a list 
list("t1" = t1, "t2" = t2) %>% 
  # map allows us to do the same computation for all objects of the list as 
  # defined by the function \(x) x...
  map(\(x) x %>% 
        mutate(row = c("1", "2", "3"), 
               .before = 1) %>% 
        pivot_longer(cols = -1, 
                     names_to = "column", 
                     values_to = "number")) %>% 
  # Once both tibbles are ready to be combined, we can access them via the with 
  # function (we may talk about this again, I find it very helpful sometimes)
  with(full_join(t1, t2, by = c("row", 
                                "column"), 
                 suffix = c("_1", "_2"))) %>% 
  # Now we continue as above
  mutate(number = number_2 / number_1) %>% 
  # And back to a wide format tibble 
  pivot_wider(id_cols = "row", 
              names_from = "column", 
              values_from = "number")
```

You do not need to understand all of this immediately, but these are some of the most common operations in omics data science. If you understand the `tidyr::pivot_longer/wider` functions within this week, you're years ahead compared to my journey in data science :)

</div>

## Coding style

![](https://upload.wikimedia.org/wikipedia/en/b/b9/MagrittePipe.jpg)

Well, what is this?! It is not a pipe. But this `%>%` is. Or is it?^[You can read the history to this picture when you are done with a section and really bored: http://adolfoalvarez.cl/blog/2021-09-16-plumbers-chains-and-famous-painters-the-history-of-the-pipe-operator-in-r/]

We previously learned that "Everything that happens is a function call." and in order for the result of the function to 'exist', we need to assign it as an object. Fine. Works. But what happens if we need to do multiple operations on the same object to get our result?

Let's consider the generic example of a vector that contains letters which we would like to count and represent in a barplot. 


```r
letters_freq <- c("A" = 5, "B" = 18, "C" = 20, "D" = 2,
                  "E" = 24, "F" = 13, "G" = 1, "H" = 25,
                  "I" = 21, "J" = 11, "K" = 19, "L" = 6,
                  "M" = 10, "N" = 14, "O" = 16, "P" = 9,
                  "Q" = 23, "R" = 17, "S" = 8, "T" = 26,
                  "U" = 22, "V" = 7, "W" = 15, "X" = 12,
                  "Y" = 3, "Z" = 4)

random_letters <- rep(names(letters_freq), letters_freq)

```

This is the first exercise in this book^[I call it an exercise, because I am not sure if it is well explained and therefore the 'exercise' is to understand what I intend to show you here :)]. Once you are done with the above code, observe what happened and then continue with the code below. 


```r
# Count each element of random_letters 
random_letters_table <- table(random_letters)
# Sort table in decending order 
random_letters_table_sorted <- sort(random_letters_table, decreasing = T)
# Plot the frequency of each letter 
barplot(random_letters_table_sorted)
```

The code above yields a barplot that represents the frequency of each letter. To get to our result, we created two intermediate objects `random_letters_table` and `random_letters_table_sorted`. We can do the same all with the `random_letters` object, simply overwriting it in each line. 


```r
# Count each element of random_letters 
random_letters <- table(random_letters)
# Sort table in descending order 
random_letters <- sort(random_letters, decreasing = T)
# Plot the frequency of each letter 
barplot(random_letters)
```

You saw in the examples above that there are different ways to chain the outputs of the different computations into each other to arrive at the barplot. Let's try and use the `%>%` operator to simplify this process. 


```r
# We reassign random_letters since we overwrote it in the previous example
random_letters <- rep(names(letters_freq), letters_freq)

random_letters %>%  
  table() %>% 
  sort(decreasing = T) %>% 
  barplot()
```

The chain begins with an object `random_letters` and is then followed by functions in each subsequent line. The output of the preceding line is always used as the first argument of the following function.

The above is equivalent to this nested construct:^[Multiple functions within each other get evaluated from the inside to the outside.]

```r
barplot(sort(table(random_letters), decreasing = T))
```

I hope it is obvious why the `%>%` is a useful tool, not just for writing less code but also making the code more legible. Btw, did you find the hidden message in the barplot? If not, try and stretch the 'Plots' window or press 'Zoom' in the 'Plots' panel.

The making of this exercise is an even better example of the utility of the `%>%` :)

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button5" aria-expanded="false" aria-controls="button5"> Making of </button> <div id="button5" class="collapse">  
\

```r
sentence_full <- "The quick brown fox jumps over the lazy dog"
## Unrelated but, wow I just discovered there's a `sentences` object in R

# Generate the frequency of each individual letter
letters_freq <- sentence_full %>% 
  # Remove spaces
  str_remove_all(" ") %>% 
  # Split the string into individual letters 
  str_split("") %>% 
  # Extract vector from list 
  unlist() %>% 
  # Make all letters upper case
  toupper() %>% 
  # Remove dublicated letters 
  unique() %>% 
  # Make vector with letters as names and numbers from 26 to 1 as content
  # Do you see how the . marks the position of the argument coming from the previous line?
  setNames(26:1, .) %>% 
  # Reorder the vector so that the solution is not immediately obvious to you guys 
  # Not this is some weird stuff here, do try this at home
  `[`(., order(names(.)))

# Test if it works
random_letters <- rep(names(letters_freq), letters_freq)


# Now prepare the example for the exercise

# This function copies a vector to the console 
.cat_character_named <- function(...) {
  
  n <- paste0(names(...), '" = "', ..., '"')
  
  cat(paste0('c("', paste(n, collapse = ',\n\t"'), ')'))
  
}

.cat_character_named(random_letters)

letters_freq <- c("A" = 5,
                  "B" = 18,
                  "C" = 20,
                  "D" = 2,
                  "E" = 24,
                  "F" = 13,
                  "G" = 1,
                  "H" = 25,
                  "I" = 21,
                  "J" = 11,
                  "K" = 19,
                  "L" = 6,
                  "M" = 10,
                  "N" = 14,
                  "O" = 16,
                  "P" = 9,
                  "Q" = 23,
                  "R" = 17,
                  "S" = 8,
                  "T" = 26,
                  "U" = 22,
                  "V" = 7,
                  "W" = 15,
                  "X" = 12,
                  "Y" = 3,
                  "Z" = 4)

```
</div>

\
For a probably better explanation of pipes or more in-depth explanation, please have a look at the [corresponding chapter](https://r4ds.had.co.nz/pipes.html) in [R for Data Science](https://r4ds.had.co.nz/) or the [chapter](https://r4ds.hadley.nz/workflow-style.html#sec-pipes) in its second edition, [R for Data Science (2e)](https://r4ds.hadley.nz).

Using the `%>%` pipe operator is only one part of the [Style guide](https://r4ds.hadley.nz/workflow-style.html) but will have a big impact on the legibility of your code. I visually prefer the [old version](http://adv-r.had.co.nz/Style.html) and suggest reading one of the two. If you are at the beginning of your coding career, not all recommendations will be immediately obvious, but you will remember them later on. 


## Data organization wihtin R

As we are moving from the basics to the actual project, let's see how we work *with* R. Working *in* R means which packages or code do we use, working *with* R means where do we put our code and our data. Let's start at the top level. Where do our scripts and data live?

### R projects

We will not just work on an R project, we will also work in one. Please have a look at the description of [R projects](https://r4ds.hadley.nz/workflow-scripts.html#projects) in this by now well known book. As we get closer to the __Group Work Project__ let's start with creating a place for our data and code.

::: {.rmdnote}

Create your own R project for this course. I suggest to make a folder called R within your Documents folder or wherever you store your research. In here, you could start to collect different R projects. 

:::

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button6" aria-expanded="false" aria-controls="button6"> Hint </button> <div id="button6" class="collapse">  
\
You can create a new R project by clicking File -> New Project... -> New Directory -> New Project. Now enter the name^[please no spaces], browse to the top folder you would like and press Create Project. If you want to keep your current R session open, tick Open in new session.
</div>

<button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#button7" aria-expanded="false" aria-controls="button7"> Additional info </button> <div id="button7" class="collapse">  
\
It may seem convenient to have this folder on the server of your lab, so it gets archived automatically, however, it sometimes gives you trouble and slows down your analysis. Copying the R folder from time to time seems like the practical solution for me.

</div>

\
Great, you created your first R project. You can identify in which project you are by the name of the window or as written in the top right corner. 

Before creating our first R script, we can set a folder structure within our R project. This can be done from the operating system's file explorer or with the function `dir.create`. I usually begin setting up my work directory like this:


```r
# All R and Rmd scripts will be in here 
dir.create("Scripts")
# All raw data can be stored here 
dir.create("Data")
# A separate folder for RData objects 
dir.create("Data/RData")
# All output like figures, tables etc. 
dir.create("Output")
```

Do this as you like :)

### Lists and .lists

Now our data has a tidy place to live in our operating system. Nice. But what about our data *in R*?

Everything in R lives in the `Global Environment`. You can read more about this [here](https://adv-r.hadley.nz/environments.html), but do this when there is some free time or you have specific questions. 

We previously touched on vectors and lists, with the main difference that vectors only take one kind of element and lists can store whatever you fancy. And that's what we want. 

Imagine you need to compute the following incredibly complicated numbers and want to store them for the meeting with your PI later:


```r
a <- 1 + 1
b <- 2 - 3
c <- 2 * Inf
d <- 1 / 0
e <- 2^2
f <- sqrt(2)
g <- exp(1)
h <- log10(3)
i <- log2(42)
j <- log(pi, base = pi)
k <- a > b
l <- a < b
m <- a == b
n <- a >= b
o <- a <= b
```

Omg, do you see how your Global Environment on the top right gets cluttered. Your PI won't like that. Let's tidy this up by using a list.


```r
# Directly store the first numbers in the list
important_numbers <- list(
  a = 1 + 1, 
  b = 2 - 3, 
  c = 2 * Inf, 
  # You can also use a string "d" to define the name, it's the same
  "d" = 1 / 0)

# Add the remaining numbers
important_numbers[["e"]] <- 2^2
important_numbers[["f"]] <- sqrt(2)
important_numbers[["g"]] <- exp(1)
important_numbers[["h"]] <- log10(3)
important_numbers[["i"]] <- log2(42)
important_numbers[["j"]] <- log(pi, base = pi)
important_numbers[["k"]] <- a > b
important_numbers[["l"]] <- a < b
important_numbers[["m"]] <- a == b
important_numbers[["n"]] <- a >= b
important_numbers[["o"]] <- a <= b
```

Click on `important_numbers` on the top right^[not the blue arrow, but try this out as well] and you can view the content of the list. This is equivalent to writing `View(important_numbers)` in your console or from your R script. 

Finally, let's clean up the mess by deleting all the previously created R objects named a, b, c and so on. This we can do with the `rm()` function. There are different ways to use it. 


```r
# Remove one object
rm(a)
# Remove multiple object 
rm(b, c)
# Or 
rm(list = c("d", "e"))
# To remove everything use the object() function
objects()
# and combine the two
rm(list = objects())
# Uups, everthing is gone. If you want to keep something add setdiff
a <- 1
b <- 2
.c <- 3
# Remove all but a
rm(list = setdiff(objects(), "a"))
```

One last trick. Did you notice how you never saw `.c` in your Global Environment. It was created as a hidden object with the `.` as a prefix. We can find it with `objects(all.names = T)` and remove it just the same. 

It is good practice to clean your environment at the end of an analysis chunk or at the end of each script to remove things you don't need anymore. If we are talking about gigabytes of data instead of those lousy numbers, try `gc()` after deleting the objects.^[If it does not help once, do this https://stackoverflow.com/a/1467334]


## Summary

Thanks for making it this far. This intro to __R Basics__ ended up quite extensive, but getting through it should give you all the tools to figure out most problems in R on your own. Not all examples are useful yet, but may come in handy later. Basically every piece of code has been used in my work at one point. 

There are a lot more functions to get to know, especially from the tidyverse, but we will cover them on the way. Please remember:

* Question everything you do not understand or that seems unclear.
* There is always more than one way to get to your goal, redundancy helps us understand things better.
* Let us know, if you have a different or better way to do something, we're here to discuss!
