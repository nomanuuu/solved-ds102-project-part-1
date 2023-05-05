Download Link: https://assignmentchef.com/product/solved-ds102-project-part-1
<br>
DS102 – Project Part 1

This is part 1 (of 2) of the project. The setting is the following:

<strong>Setup </strong>You’ve been hired by a stealth-mode start up company to analyze data related to the potential market-share and competing companies. The company can’t tell you yet exactly what they do, only that it has to do with scooters (the type in Figure 1).

Your job as a freelance data analyst is to look at this problem from several angles, and write up a report detailing your methods and your findings. This document details the questions the company would like answers to, as well as some questions you might investigate on your own to enhance the report.

<strong>Instructions </strong>We’ve provided an outline, including a set of prompts and subsections for you to fill out. Please <strong>do not alter the section numbers</strong>. If you wish to copy the outline into a different text editor (google docs, word), that’s fine, but please keep the section and subsection structure consistent.

Some of the prompts are mandatory, and some are optional open-ended questions (marked with a star, *). We expect you to answer all questions without stars, select a single starred questions depending on what interests you most.

Figure 1: A scooter. Also an example template for inputting figures in latex.

Remember that this is an independent project. While you can talk to others, your analysis (especially for open ended questions) should be from your own ideas. Please submit your filled-in report as a pdf on gradescope. You must also email any code you use in a zip file to <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="86ede7f4eaedc6e4e3f4ede3eae3ffa8e3e2f3">[email protected]</a> with files clearly named to match each section, and subject line “DS102 – project01”.

<strong>Grading      </strong>The major components of your grade are:

<ul>

 <li><strong>Content</strong>: in each part of the assignment there are structured questions for you to fill out, with point assignments given. There are also open ended prompts (denoted with *’s) that you can explore depending on which parts of the project interest you most. A full and correct set of responses for the non-starred problems will receive 80% credit; the remaining 20% will be assigned for open ended responses.</li>

 <li><strong>Completeness</strong>: For all parts of the report, carefully and completely describe what you did. As a rule of thumb, a reader who has taken DS100 but not DS102 should be able to reproduce your analysis without referring to any of your code.</li>

 <li><strong>Creativity</strong>: For the open ended problems, we expect to see a careful or creative integration of topics from class. This creativity takes effort, and you have the choice of which starred problems to put forth this effort on. Document why you’re approaching questions with certain techniques, and if things don’t work out as expected, that’s ok!</li>

 <li><strong>Professionalism and Readability</strong>: We expect full sentences with correct grammar and spelling. All axes in all figures should be labeled, with units when applicable.</li>

</ul>

<h1>Setup</h1>

You’ve been tasked with analyzing the public datasets released by three bike sharing companies in New York, Washington DC, and Chicago. Another data scientist has helpfully preprocessed the dataset for you in four files that can be found here: https://github.com/ds102/fa19/tree/master/project/bikeshare.zip.

The ny.csv, chicago.csv, and dc.csv each contain the bike rentals that occurred in 2016 in their respective cities with each row representing a single rental.

The day.csv dataset contains daily bike rental information between the years 2011 and 2012 in Washington DC. The original bike rental dataset has also been merged with weather information and holiday information using other data sources.

If you’re curious you can find the original datasets at the following links

<ul>

 <li>New York: https://www.citibikenyc.com/system-data</li>

 <li>Washington DC: https://www.capitalbikeshare.com/system-data</li>

 <li>Chicago: https://www.divvybikes.com/system-data</li>

 <li>Daily Summary: https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset</li>

</ul>

<h1>1        Preliminary Data Analysis</h1>

You decide to start by performing some exploratory analysis to see if you can find any interesting trends.

<h2>1.1       Demographic Information</h2>

In this section you should:

<ol>

 <li>Plot the distribution of male to female riders for chicago.csv.</li>

 <li>Plot the distribution of the gender column for ny.csv.</li>

 <li>Given the results in Chicago, make an educated guess as to the mapping from numerical value to Male/Female/Unspecified within the ny.csv dataset.</li>

 <li>Plot the distribution of the birth years of bike renters in Chicago and NY.</li>

 <li>Discuss the results you observed in the age plots and whether this fits with your intuition. Would you remove any data? If so, why?</li>

</ol>

<h2>1.2       Rental Times</h2>

In this section you should:

<ol>

 <li>Plot the three distribution of trip duration in minutes across all three cities.</li>

 <li>Are the plots you generated useful? If not, plot them again so that the visualization is more useful.</li>

 <li>Plot the start time of trips split by hour for all three cities.</li>

 <li>Discuss the results you observed in the start time plots. Do they fit your intuition?</li>

</ol>

<h2>1.3        Further Exploration</h2>

In this section you should:

<ol>

 <li>Visualize three more attributes.</li>

 <li>Discuss any insight you obtained from these three new visualizations.</li>

 <li>Pick one of the three attribute and plot its distribution if you haven’t already. Explore the data further to get a plausible explanation for the shape of the distribution. For example you could explore whether the attribute is correlated with another attribute.</li>

 <li>Given the insights you obtained from the data, write down a hypothesis that you think is important and how you would go about testing it.</li>

</ol>

<h2>1.4          Optional*: Creating a new dataset</h2>

You want to investigate the change in rental behavior from 2011 to 2016 and also the change in rental behavior between cities. To do this you want to transform ny.csv, chicago.csv, and dc.csv into three new datasets that resemble day.csv.

Read the attribute information section found at https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset. Now try to reproduce a few of the columns described there while using ny.csv, chicago.csv, and dc.csv as your data source. Submit the newly created files as ny daily.csv, chicago daily.csv, and dc daily.csv.

If you’re feeling particularly ambitious you can try to reproduce the columns describing weather but you’ll have to find an external dataset that has daily weather information for each city. This might be time consuming and isn’t compulsory.

Describe the dataset creation procedure you followed. Write about any interesting conclusions you made by comparing the three new datasets with day.csv, support your conclusion with graphs and statistics.

<h1>2       Hypothesis Testing</h1>

Suppose that, for privacy reasons, the company has to change its policy and make the indicator of whether each bike ride corresponds to a casual (customer) or non-casual (subscriber) user confidential. In the future the company will no longer have access to this feature. However, this feature is particularly useful, because depending on the type of user the company might want to give them different promotions and advertisement. Therefore, in this part we will design a test for whether the user is casual or not. We will also try to prevent too many false discoveries, i.e. falsely declaring a casual user as a non-casual one.

You will be given general guidelines for the problem below. However, there is no single correct solution. Feel free to use any additional Python packages, as well as any hyperparameters you might want to add. You can also reuse any code from previous homework/lab solutions.

Pick your favorite city among the three we have data from (New York, Washington DC or Chicago). In the rest of the problem, you will only use the data set corresponding to that city. Let <em>n </em>denote the total number of samples. For each <em>i </em>∈ {1<em>,…,n</em>}, denote by <em>Y<sub>i </sub></em>the indicator whether the user is casual (<em>Y<sub>i </sub></em>= 0) or non-casual (<em>Y<sub>i </sub></em>= 1). For <em>i </em>∈ {1<em>,…,n</em>}, let <em>X<sub>i </sub></em>denote the feature vector consisting of the following 3 features: trip duration, ride start time and ride stop time. As the start and stop time, simply take the <em>hour </em>of the corresponding time. For example, if the ride starts at 13:05, take 13 as the start time. Similar for stop time.

Split the data set into three uniformly-without-replacement randomly sampled subsets: <em>S</em><sub>1 </sub>(60% of the whole data set), <em>S</em><sub>2 </sub>(20% of the whole data set) and <em>S</em><sub>3 </sub>(20% of the whole data set). Recall that we need the model of the data under the null in order to compute p-values. We will use <em>S</em><sub>1 </sub>and <em>S</em><sub>2 </sub>to learn this model, and then compute p-values on <em>S</em><sub>3</sub>.

<ol>

 <li>Consider the logistic regression model</li>

</ol>

<em>,</em>

for some <em>θ </em>= (<em>θ</em><sub>1</sub><em>,θ</em><sub>2</sub><em>,θ</em><sub>3</sub>). Use <em>S</em><sub>1 </sub>to train a logistic regression model for predicting <em>Y<sub>i </sub></em>from <em>X<sub>i </sub></em>according to the above model. Denote by <em>θ</em><sub>∗ </sub>the learned value of <em>θ</em>. Consider using methods available in sklearn.

<ol start="2">

 <li>For each sample (<em>X<sub>i</sub>,Y<sub>i</sub></em>) in <em>S</em><sub>2</sub>, compute . For each (<em>X<sub>j</sub>,Y<sub>j</sub></em>) in <em>S</em><sub>3</sub>,</li>

</ol>

compute <em>s</em><sup>(3)</sup><em><sub>j </sub></em>analogously. Denote by <em>S</em><sub>2<em>,</em>0 </sub>the subset of <em>S</em><sub>2 </sub>that consists of casual users (<em>Y<sub>i </sub></em>= 0). For each sample <em>j </em>in <em>S</em><sub>3</sub>, compute a p-value as

<em>,</em>

where as usual we use | · | to denote the cardinality of a set. Plot two histograms: one of null p-values (<em>Y<sub>i </sub></em>= 0, casual riders) and one of non-null p-values (<em>Y<sub>i </sub></em>= 1, non-casual riders). What do you observe?

<ol start="3">

 <li>Now you should have |<em>S</em><sub>3</sub>| p-values. Run the Benjamini-Hochberg algorithm under level 0<em>.</em>2 on these p-values, and compute the false discovery proportion (FDP) and sensitivity. Repeat the whole procedure from above for 200 different randomly sampled <em>S</em><sub>1</sub><em>,S</em><sub>2 </sub>and <em>S</em><sub>3 </sub>(you don’t have to repeat the visualizations). You should have 200 sets of |<em>S</em><sub>3</sub>| p-values, and get 200 different false discovery proportions and sensitivities. Report the average FDP and sensitivity over these 200 trials. Is the average FDP above or below</li>

</ol>

0<em>.</em>2? Can you explain why it is or isn’t?

<h2>2.1          Optional*: Improving the Average Sensitivity</h2>

Try to improve the average sensitivity of the BH procedure by making the distribution of non-null p-values “smaller”. In other words, you want to make the histogram of non-null p-values more skewed “to the left”. Report the new average sensitivity, compare it to the old average sensitivity, and describe in detail how you achieved this improvement. One suggestion for this would be to pick different features, or transform them in some way (i.e. you might want to add some features on top of the three from above, or, for example, instead of trip duration you can look at <em>f</em>(trip duration), for some function <em>f</em>). You can also use a completely different way to generate p-values, but you need to make sure that they are valid, meaning that they are approximately uniform under the null and that BH controls FDR under 0.2. If you choose to use a different way to generate p-values, you have to include a plot of null p-values and non-null p-values.

<h1>3          Gaussian Mixture Models of Trip Durations</h1>

In the previous part you performed Hypothesis Testing to distinguish between Casual and Registered users of the bike sharing service. Moving forwards, you would like to understand the distribution of trip durations so that you can better choose the scooter your startup will use. You assume that the main factor influencing the length of the trip is whether or not a customer is a subscriber.

<ol>

 <li>Describe why it is reasonable to believe that should be a difference in the distributions of trip durations of subscribers and non-subscribed customers. Use figures from the data to back up your argument.</li>

 <li>Use the Expectation-Maximization (E-M) Algorithm to learn a mixture of two Gaussians that describes the distribution trip-durations of length <strong>less than one hour </strong>in the csv dataset. Run this multiple times from different initializations. Do your results change drastically depending on the initialization? What are the means and variances of the fitted Gaussians?</li>

 <li>Given the output of the E-M Algorithm, which of the distributions captures the behavior of the subscribed customers? For each customer, in the dataset, calculate the posterior probability that the customer is from this distribution.</li>

 <li>If you design a classifier which classifies a customer as a Subscriber if their posterior probability is greater that 0<em>.</em>5, what is the error of this classifier given the true User Types in the csv dataset?</li>

 <li>Use the classifier derived from the csv dataset on the ny.csv and dc.csv datasets. How does this classifier perform? How does the performance compare to that in the previous part? (Make sure that the data for each city is in comparable units.)</li>

</ol>

<h2>3.1           Optional*: Learning Mixtures of Bivariate Gaussians</h2>

In the previous section you learned a mixture of univariate that described trip durations in the chicago.csv dataset. In this optional part you will learn a mixture of bivariate Gaussians using the start-times of the data.

<ol>

 <li>Describe why it is reasonable to believe that the start-times of customers will help you distinguish between subscribers and non-subscribed customers. Use figures from the data to back up your argument.</li>

 <li>Use the Expectation-Maximization (E-M) Algorithm to learn a mixture of two bivariate Gaussians that describes the distribution trip-durations of length <strong>less than one hour </strong>and start-times in the csv dataset. Make sure that the start-times are in the form of minutes-past-midnight.</li>

</ol>

Run this multiple times from different initializations. Do your results change drastically depending on the initialization? What are the means and covariances of the fitted Gaussians? What do these numbers imply?

<ol start="3">

 <li>As before, design a classifier that classifies a customer as a Subscriber if their posterior probability of being from one of the Gaussians is greater that 0<em>.</em> How does this classifier perform compared to the one which used only the trip-durations? Why is the performance better or worse?</li>

 <li>Experiment designing classifiers based off of mixtures of different numbers of bivariate Gaussians. How well do these classifiers generalize to the other cities in the data? Why do you think the performance is consistent or inconsistent depending on the city?</li>

</ol>

<ul>

 <li><strong>Causality and Experiment Design.</strong>

  <ul>

   <li><strong>2SLS to estimate the effect of precipitation on #bike rentals.</strong></li>

  </ul></li>

</ul>

You would like to know more about what causes a higher or lower number of rentals on a given day. More specifically, you might want to determine the effect that weather conditions have on the number of bike rentals.

Using the daily UCI data, run a two stage least squares regression to calculate the effect of adverse weather (weathersit <em>&gt; </em>1) vs nice weather (weathersit = 1) on the total number of rentals.

Since we are given an observed data set, we will use instrumental variables analysis and 2 stage least squares regression. In particular, temperature is a potential confounding variable for weather and the number of bike rentals. To overcome this, use humidity as an instrumental variable.

<strong>4.1.1      The causal model.</strong>

In this section you should:

<ol>

 <li>Draw the graph of the causal model, with arrows between variables to denote causality. Your graph should include the following variables: temperature, weathersit, humidity, and number of rentals.</li>

 <li>Clearly describe the assumptions necessary for 2SLS analysis. For any assumptions you can check with the data set, do so. For the remainder of the assumptions, give your best guess as to whether they hold given the problem setting, and discuss how you would test them (this could mean collecting more data).</li>

</ol>

<h3>4.1.2       2 Stage Least Squares</h3>

In this section you should:

<ol>

 <li>Describe the 2SLS procedure, as it applies to the variables above. Describe the procedure at a level such that someone who has taken DS100, but not DS102, would be able to reproduce the analysis (without looking at your code).</li>

 <li>Report the resulting treatment affect of weathersit on the total number of bike rentals. Interpret this treatment effect estimate in terms of the variables of the problem.</li>

 <li>Report the resulting treatment affect of weathersit on the number of casual bike rentals, and on the number of registered bike rentals.</li>

</ol>

<h3>4.1.3      Discussion</h3>

In this section you should discuss the following:

<ol>

 <li>Give a three sentence summary of the question, how and why we tested it, and the results of the analysis.</li>

 <li>Interpret the treatment effect estimates that resulted for the number of casual rentals and for the number of registered rentals. Is the magnitude of the treatment effect higher for one group than another? Give at least one possible reason for the difference/similarity you find.</li>

 <li>Discuss the applicability of the chosen model (causal graph from above) to this problem. Are there any variables that might missing from the causal graph? Are there any arrows that are missing?</li>

 <li>If you had the opportunity to design your own study (and collect new data) to test the effect of adverse weather on the number of rentals, what would that study look like? Explain at a high level the design decisions you would make and why (keep your response to no more than 5 sentences).</li>

</ol>

<strong>4.2      Optional*:  Simulating Experiment Design Approaches via Sub-sampling.</strong>

Define a hypothesis that you’d like to test given the data at hand. Then, imagine this data set were not available to you, and you needed to collect new data to answer your hypothesis. In particular, you need to design and carry out an experiment. Use what we’ve learned about experiment design to formulate your sampling strategy. Then, using any of the data sets given, sample instances from these data sets to simulate running your experiment. (Note: this means you will have to pick a hypothesis and a sampling design that can be simulated by taking draws from the data given).

As an example, you could imagine testing whether there are more bike rentals on weekends or weekdays, on average. Your experiment design might randomly or deterministically pick certain days to observe the number of riders on that day. For every day of observation you must pay someone to count the number of rentals, thus each day of observations costs you data. You might define two strategies: spend half of your money sampling weekdays, and spend half of your money sampling weekends. Or perhaps you think weekend rental counts are more variable, so you spend more samples observing weekend days. To simulate the results of these methods, you would take subsets of the days from the <em>observed </em>data set which correspond to the strategy of your design. This sub-sampling of the data would need to simulate the sampling strategy you chose.

Such a simulation study could compare different strategies for picking these days, and the resulting inferences made. A good simulation study will also give a notion of variability due to any randomness in the design. In the discussion of your experimental simulation methodology, you may want to address sources of randomness, nuisance variables, or unobserved/uncontrollable variables that you sampling methodology does or does not account for.

This is an open-ended problem, so the choice of hypothesis and resulting experiment design are up to you. As a starting point, the following are good things to address if you choose to do this part of the project:

<ul>

 <li>Define the hypothesis you would like to test.</li>

 <li>Define the experimental design you would use to test this hypothesis.</li>

 <li>Describe a data sub-sampling experiment to simulate the effect of your experiment design. Potentially also describe how you evaluate success of the experiment.</li>

 <li>Carry out the sub-sampling experiment and report your findings. Give a brief discussion of the implications of your findings.</li>

 <li>Discuss the pros and cons of a sub-sampling simulation experiment to test your experimental design.</li>

</ul>

You should not feel limited to addressing only these things, nor should you feel obligated to do all of them if you focus on some parts more than others. The intent of this section is to use sub-sampling to evaluate your design, so it would be wise to pick a hypothesis and experiment that are amenable to this.