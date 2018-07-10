# 5.3 Lesson Review - Introduction to Statistics

## Overview

Today's class formally treats a number of topics from basic statistics, including measures of central tendency; variance; standard errors; and error bars.

### Objectives

* Students will be able to define **mean**, **median**, and **mode**, and choose which one is most appropriate to describe a given data set.
* Students will be able to explain the meaning of variance and standard deviation.
* Students will be able to describe standard error and the difference between a sample and a population.
* Students will be able to add error bars to their plots.
* Students will be able to fit lines to their data.

- - -

### 1. Statistics

* The **mode** of a data set is the **most frequently occurring element**.
  * For example, in a list like `[1, 1, 2]`, 1 would be the mode.
* The **median** of a data set is the middle element.
  * To find the median, we first sort the data, and select the middle element. In `[1, 2, 3]`, 2 is the median.
  * For even-length data sets, we have _two_ elements in the middle of the list.
* Generally we return the **average** of the two elements as the median of such a list.
* The **mean** of a data set is what is commonly called the _average_ of a data set.
  * To calculate the mean, we sum all of the numbers in the data set, and divide by the length of the data set.
* The purpose of each of these numbers is to allow us to describe an entire data set with a single number.
  * While each of these numbers allows us to describe a data set, they are not always equally descriptive.
* The median is a good choice for describing just about any data set.
  * Take, as example, these prices from a local department store: `[30, 31, 31, 32, 32, 40, 41, 41, 1000]`.
  * In this case, _most_ of the prices fall between 30 and 41.
  * The median, 32, is a reasonable description of the "average" price in the data set.
  * The mean, which works out to 142, does not describe the data very well — in fact, the mean is a different order of magnitude than _any_ of the prices in the data set!
  * This illustrates that the median tends to give relatively faithful descriptions even in the face of outliers, such as 1000.
  * In general, the median is more "resistant" to extreme fluctuations in data than the mean.
  * This property often makes the median a better choice than the mean, in spite of the fact that the mean is more common.
  * Students can [almost always safely use the median to describe their data](https://learnandteachstatistics.wordpress.com/2013/04/29/median/).
  * Median is particularly faithful for data sets that have a large number of values that are low, or a large number that are high.
  * Our price data fits this description: Most of it is low, but there is _one_ value that is high.
  * Data with this property is called _skewed_.
  * In these cases, the extreme values _outside_ of the cluster of typical values changes the mean disproportionately, but the median remains relatively unaffected, and still faithfully represents the data.
* Sometimes, we might have data where values cluster in _several_ places.
* Consider this longer list of prices: `[30, 31, 31, 32, 32, 40, 41, 41, 1000, 1210, 1210, 1567]`
  * In this case, the mean, 438.75, still differs from the typical price in either the low or high clusters by an order of magnitude.
  * The median, 40.5, also doesn't adequately describe the data.
  * _Most_ prices are close to 40.5, but a large number of them — 30% — are much higher.
* Data like this, which has two or more _clusters_ of data that are spread apart from one another, is often best described by the **mode**.
* This is because a data set can only have one median or mean, but multiple modes; and that the list of modes is likely to contain numbers from each cluster.
  * In this case, the modes are 31, 32, 41, and 1210, numbers which _do_ represent the spread of the data quite nicely.
* If this data set had included only one instance of 1210, this "trick" would not work.
  * This is a valid concern, but that in data sets of sufficient size — like most real-world data sets students will work with — "big clusters" will each often contain a mode.
  * If this is not the case, students can describe the data using the modes alongside the median.
* The **mean** is most useful for describing data that are close together.
  * Consider the list of only low prices: `[30, 31, 31, 32, 32, 40, 41, 41]`.
  * In this case, the mean, 34.75, _is_ an accurate summary of the price data.
  * Real data sets are often more "spread out" than this, and that it is difficult to guarantee that a data set does not contain extreme values that skew the mean.
  * If our data _does_ have this property, the mean is a useful descriptor.
  * The median remains a good default statistic, even in these cases, as it will be fairly close to the mean — for this data set, the median is 32, which is just as "accurate" a summary as 34.75.
  * One important potential advantage of the mean over the median is that it factors in _every value of the data set_, which the median and mode do _not_.

### 2. Variance and Standard Score

* While the mean, median, and mode allow us to summarize our data succinctly, there are important aspects of data that they do not reveal.

* One of the most important aspects that they fail to describe is how _spread out_ the data is.

* For example, consider these two lists: `[3, 4, 5, 6, 7]` and `[-1525, -200, 5, 745, 1000]`.

  * For both of these data sets, the mean and median are 5 — but they are _obviously_ different!

* These data sets are different in how _spread out_ the data is, something that the mean, median, and mode cannot capture.

* Important statistics that measure spread are **variance**, **standard deviation**, and **z-score**.

  * The **variance** of a data set is a single number that describes how "far apart" its values are.

  * Optionally, [display the formula for variance](http://davidmlane.com/hyperstat/A16252.html).

  * Variance is calculated by subtracting the mean of the data set from every number in the data set; squaring each difference; summing the squares; and then dividing the sum by the number of items in the data set.

* The more "spread out" a data set is, the higher its variance.

  * For the data set `[3, 4, 5, 6, 7]`, the variance is 2.

  * For the data set `[-1525, -200, 5, 745, 1000]`, the variance is 784,110.

  * This suits our intuition: The second data set _spreads_ more than the first, so its variance should be higher.

* The **standard deviation** is simply the square root of the variance.

* When we take the variance of data, it is measured in units _squared_.

  * The variance of a data set containing the heights of average Australians would be in units of inches (or centimeters) _squared_.

  * It is not natural to talk about how much a data set measured in inches spreads in terms of _square_ inches — it makes more sense to talk about how much data measured in inches spreads in terms of _inches_.

* This is one of the motivators for using the standard deviation instead of the variance: It is easier to interpret.

  * The standard deviation for the data set `[3, 4, 5, 6, 7]` is approximately 1.414.

  * The standard deviation for the data set `[-1525, -200, 5, 745, 1000]` is approximately 885.5.

  * These numbers intuitively make more sense relative to the data sets they describe than the variances do.

* NumPy, Pandas, etc., also provide functions for calculating the standard deviation of a data set.

* We often use the standard deviation as a unit to describe how far individual numbers in a data set are away from the mean.

  * Intuitively, the standard deviation tells us how far away from average any number in the data set is.

  * For example, consider the price data we had before: `[30, 31, 31, 32, 32, 40, 41, 41, 1000]`.

  * 1000 is very far away from average.

* If you run the numbers, 1000 would 2.83 standard deviations away from average, meaning it is _far_ above the mean.

  * For comparison, 41 is only -0.3 standard deviations away from average, meaning it is _just a little below_ the mean.

  * while 2.83 and -0.3 seem like somewhat arbitrary, numbers they fit our intuition — 1000 is further away from "normal", and so has a higher standard deviation.

* Finally, the variance and standard deviation are _single_ numbers that describe the _whole_ data set.

  * The **z-score** is a statistic that describes how far away from the mean any _single_ number in the data set is.

  * The z-score for a number in a data set tells us how many standard deviations away from the mean that number is.

  * The numbers we just calculated for our prices are z-scores.

  * Explicitly, the z-score for 1000 in our price data set is about 2.83, whereas for 41, it is -0.3.

* Do not remember formulas for calculating z-scores, as the libraries you work with — namely [SciPy](https://www.scipy.org/) — have them built-in.

### 3. Misleading Statistics & Quartiles

* Point out again that extreme values in a data set can skew descriptive statistics like the mean.

  * Extreme values are known as **outliers**.

* We do not necessarily have to keep these points — if it makes sense, we can _sometimes_ choose to ignore them.

* Extreme values often do not describe the data, and are the result of factors other than what we are trying to understand.

  * This is not _always_ the case, however, so we cannot remove _all_ extreme values _all_ of the time.

* It is okay to remove outliers if any of the following are true.

  * The data is due to bad measurements. If your data includes reaction time measurements, and one of the values is 1ms, you should probably remove it — human reaction times are _at least_ 100ms, so 1ms is clearly bad data.

  * If the outliers _create_ trends that wouldn't exist without them, you _should_ drop them.

    ![In this plot, the outlier creates a trend, and we should ignore it.](http://www.theanalysisfactor.com/images/graph-3.gif)

* The outliers do _not_ change your results. In this case, it is okay to drop them, but it is best to make a note of having done so.

  ![In this plot, the outlier does not change the line we draw.](http://www.theanalysisfactor.com/images/graph-1.gif)

* If your outlier _does_ change your results, you _should not_ drop it.

  ![In this plot, the outlier affects the line we draw, and so is significant.](http://www.theanalysisfactor.com/images/graph-2.gif)

* The above plots are from an article on removing outliers on [The Analysis Factor](http://www.theanalysisfactor.com/outliers-to-drop-or-not-to-drop/).

* Interesting data sets are generally to large to apply these rules by hand, but that they are good guidelines to use after graphing data to determine if there are any points that should obviously be considered for removal.

* While useful, these essentially graphical guidelines are a little "fuzzy".

* There are multiple ways to remove outliers from data sets that rely on "hard numbers".

  * The simplest of these relies on removing data that is "far away" from the median.

  * To quantify this, we need to understand the idea of **quartiles**.

* **quartiles** are a way to divide our data into well-defined regions.

  * that the median is the midpoint of a data set — it divides the list in two.

* We can think of everything above the median and everything below the median as two separate data sets.

* The median of the upper list is called the **upper quartile**, and the median of the lower list is called the **lower quartile**.

* A simple but common way to remove outliers is to throw away anything _above_ the upper quartile, and everything _below_ the lower quartile.

* Finally, subtracting the lower quartile from the upper quartile gives us the **interquartile range**, which is another measure of how "spread out" a data set is.

### 7. SEM and Error Bars

* Measures like the median, standard deviation, and interquartile range are meaningless if we cannot trust the data used to generate them.

* There are many ways to establish measures of trust in a data set.

* For now, we will focus on the notions of **standard error** and how well measurements of a section of a population (e.g., voting habits of Americans in cities) represent that population as a whole (e.g., all Americans).

* Consider the case of predicting election outcomes.

  * During election cycles, political scientists often make predictions as to who will win elections before the election is actually conducted.

* To do this, they use data about peoples' voting habits.

  * The data they use cannot be perfect — in other words, they cannot make a prediction by asking every voter who they will vote for.

  * This is impossible because they do not know exactly who will vote, nor can they realistically poll millions of people before an election.

  * This implies they have to ask a _subset_ of the voting population about their voting habits, and _extrapolate_ from those results.

* For example, we might ask 1,000 random voters whom they will vote for, and try to guess the winner of the election based on their answers.

  * In this example, the 1,000 random voters we poll are called the **sample**, while the entire voting population that they represent is called the **population**.

  * We can use the data collected from the _sample_ to predict how the _population_ will behave.

* This process can lead to imperfect predictions, and ask students to suggest a few reasons why.

  * Good answers include the fact that a small sample might not realistically represent a large population, and that even a large sample, if chosen poorly, might not describe the population at large.

  * For example, if we poll only college students and people who live in cities, we will almost certainly make bad predictions, because this sample does not represent the entire population.

* Students should always think about how well samples represent the populations they describe, but that, for today's purposes, we will assume the samples we discuss are well-chosen.

  * Given this assumption, let's say we read election predictions from two different sources.

  * One source made predictions from a sample of 1,000 people; the other made predictions from a sample of 10,000. Ask students which we would trust more, and why.

  * We would, of course, trust the second prediction more — all other things equal, a larger sample is more likely to represent the population than a smaller one.

* We can use statistics to make this intuition rigorous.

  * If we _could_ ask the entire voting population what decisions they will make, we would have a "perfect" data set.

  * This data set would have all the characteristics we have discussed so far — a mean, a variance, etc.

* Since we cannot poll the entire population, we cannot know these numbers precisely, even though they do exist.

  * Since the sample is itself just a data set, it _also_ has a mean, a variance, etc.

  * This is the motivation for polling _samples_: We can _estimate_ population statistics by _extrapolating_ from the sample's statistics.

  * The reason we trust a larger sample more than a smaller one is because it is intuitively obvious that it is more likely to produce good estimates of how the population behaves.

* Since a sample is just a subset of the whole population, we can poll _multiple_ samples to get more accurate estimates of how the population behaves.

  * For example, we might take one sample of 10,000 people, and find that 52% say they will vote Democratic.

  * Then, we might take another sample of 10,000 people, and find that 49% say they will vote Democratic.

  * We can use the numbers from these _different_ samples to guess how the whole population will behave more accurately than we could if we only had _one_ sample.

* If we take multiple samples, the collection of samples _themselves_ is a data set.

  * If we have 100 samples, we create a list of the samples' standard deviations.

  * We can use these numbers to calculate something called **standard error**, which is an estimate how well the samples represent the population.

  * Each sample's _standard error_ describes how far its mean is from the population's "true" mean.

  * The formula is unimportant — there is a [function in SciPy](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.sem.html) that does this for us.

### 13. Fits & Regression

* The final important piece of statistics for the day is the subject of **regressions**.

* That regression analysis allows us to take a data set and "reverse engineer" an equation describing it.

  * Measures like the median, variance, and IQR _describe_ data sets, but do not allow us to make _predictions_ with it.

  * It is tools like regression that allow us to predict where data points we _did not_ measure might end up if we _had_ collected more data.

  * It is such tools that allow us to predict house prices, stock market movements, and the weather — regression is a truly powerful tool.

* We will not dive into the mathematical details of regression — rather, we will focus on how to use SciPy to generate a regression line.

  * When finding regression in Python the first thing we do is generate fake data.

  * Next, we call `linregress` with `x_axis` and our fake data.

  * `linregress` returns a lot of values, most of which we throw away.

  * For our purposes, the most important are the slope and intercept values, which we use to define the regression line — the rest are discussed in the documentation linked above.

  * Finally, explain how we define the regression line.

  * Note that the equation for a line looks like: `line = slope * x_axis_values + y_intercept`.

  * Here, we create an array containing the points of the line by simply writing this equation directly, with the values returned by `linregress`.

- - -

### Copyright

Trilogy Education Services © 2018. All Rights Reserved.
