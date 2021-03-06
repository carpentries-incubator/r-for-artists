---
# Please do not edit this file directly; it is auto generated.
# Instead, please edit 02-dataframes.md in _episodes_rmd/
title: "Draw Many Rectangles"
teaching: 0
exercises: 0
questions:
- "How can I draw many rectangles without a lot of code?"
objectives:
- "Create a dataframe to store values (e.g. color) for each rectangle."
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---





Figure of dataframe structure from another lesson.

You can make a dataframe by manually entering the values you want to use
for each variable for each rectangle and then bind them together.


~~~
rect1 <- c(xmin = 1, xmax = 3, ymin = 10, ymax = 15, fill = "blue", alpha = 0.4, color = "black")
rect2 <- c(xmin = 2, xmax = 5, ymin = 3, ymax = 10, fill = "orange", alpha = 1, color = "black")

my_rectangles <- rbind(rect1, rect2)
~~~
{: .language-r}

This is also really repetitive and annoying if you have many rectangles. 
Instead of specifying all of the variable names, you can do this: 


~~~
rect1 <- c(1, 3, 10, 15, "blue", 0.4, "black")
rect2 <- c(2, 5, 3, 10, "orange", 1, "black")

my_rectangles <- rbind(rect1, rect2)
colnames(my_rectangles) <- c("xmin", "xmax", "ymin", "ymax", "fill", "alpha", "color")
~~~
{: .language-r}

Note to self: Neither of the above actually creates dataframes, so move intro of dataframe terminology to later. 

> ## Exercise
> Add two more rectangles to your data table.
> 
> 
> ~~~
> rect3 <- c(8, 15, 3, 10, "darkblue", 0.3, "black")
> rect4 <- c(1, 4, 6, 12, "purple", 0.5, "black")
> 
> my_rectangles <- rbind(my_rectangles, rect3, rect4)
> ~~~
> {: .language-r}
> {: .solution}
{: .challenge}


~~~
my_rectangles <- as.data.frame(my_rectangles)
~~~
{: .language-r}


~~~
ggplot() + 
    geom_rect(my_rectangles, mapping = 
                aes(xmin = xmin, xmax = xmax, 
                    ymin = ymin, ymax = ymax),
              fill = my_rectangles$fill,
              alpha = my_rectangles$alpha) + 
    theme_void()
~~~
{: .language-r}



~~~
Error in grDevices::rgb(col[1, ], col[2, ], col[3, ], alpha): alpha level 2, not in [0,1]
~~~
{: .error}

<img src="../fig/rmd-02-dataframes-rects-from-dataframe-1.png" title="plot of chunk rects-from-dataframe" alt="plot of chunk rects-from-dataframe" width="612" style="display: block; margin: auto;" />


{% include links.md %}
