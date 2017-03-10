---
title: "lab_homework_week8.Rmd"
output: html_document
---

# Exercise 1 
```{r}
dat <- read.csv("~/Desktop/eeb-177/lab-work/exercise-8/Rgraphics/dataSets/EconomistData.csv")
head(dat)

# Create a scatter plot with CPI on the x axis and HDI on the y axis.

ggplot(dat, aes(x = CPI, y = HDI, size = HDI.Rank)) + geom_point()

```


# ggplot(dat, aes(x = CPI, y = HDI, size = HDI.Rank)) + geom_point()

```{r}
# Color the points blue.
ggplot(dat, aes(x = CPI, y = HDI, size = HDI.Rank)) + geom_point(color = "blue")
```

```{r}
# Map the color of the the points to Region.
region <- ggplot(dat,aes(x=CPI,y=HDI)) 
region + geom_point(aes(color = Region))
```

```{r}
# Make the points bigger by setting size to 2
region <- ggplot(dat,aes(x=CPI,y=HDI)) 
region + geom_point(aes(color = Region, size= 2))
```

```{r}
# Map the size of the points to HDI.Rank
region <- ggplot(dat,aes(x=CPI,y=HDI)) 
region + geom_point(aes(color = Region, size= HDI.Rank))
```

```{r}
# Exercise II

# 1. Re-create a scatter plot with CPI on the x axis and HDI on the y axis (as you did in the previous exercise).
ggplot(dat, aes(x = CPI, y = HDI)) + geom_point()

#2. Overlay a smoothing line on top of the scatter plot using geom_smooth.
ggplot(dat, aes(x = CPI, y = HDI)) + geom_point() + geom_smooth()

#3. Overlay a smoothing line on top of the scatter plot using geom_smooth, but use a linear model for the predictions. Hint: see ?stat_smooth.
ggplot(dat, aes(x = CPI, y = HDI)) + geom_point() + stat_smooth(method="lm")
?stat_smooth

#4. Overlay a smoothing line on top of the scatter plot using geom_line. Hint: change the statistical transformation.
ggplot(dat, aes(x = CPI, y = HDI)) + geom_point() + stat_smooth(method="lm") + geom_line()
?geom_line


#5. BONUS: Overlay a smoothing line on top of the scatter plot using the default loess method, but make it less smooth. Hint: see ?loess.
ggplot(dat, aes(x = CPI, y = HDI)) + geom_point() + geom_smooth() + loess(span = 0.50)
?loess

```

```{r}
# Create a scatter plot with CPI on the x axis and HDI on the y axis. Color the points to indicate region.
region <- ggplot(dat,aes(x=CPI,y=HDI)) 
region + geom_point(aes(color = Region))

# Modify the x, y, and color scales so that they have more easily-understood names (e.g., spell out "Human development Index" instead of "HDI").
region <- ggplot(dat,aes(x=CPI ,y=HDI)) 
region2 <- region + geom_point(aes(color = Region))
region2 + xlab("Corruption Perceptions Index") + ylab("Human development index")
# Modify the color scale to use specific values of your choosing. Hint: see ?scale_color_manual.

?scale_color_manual
colors <- c("green", "blue", "red","black", "purple", "pink")
region2 + scale_color_manual(values=colors)
region2

```


