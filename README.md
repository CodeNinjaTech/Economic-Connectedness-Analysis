# Economic Connectedness

In this assignment you will replicate partly two studies carried out on social capital. The studies appeared in the journal Nature:

* Chetty, R., Jackson, M.O., Kuchler, T. et al. Social capital I: measurement and associations with economic mobility. Nature 608, 108–121 (2022). https://doi.org/10.1038/s41586-022-04996-4.

* Chetty, R., Jackson, M.O., Kuchler, T. et al. Social capital II: determinants of economic connectedness. Nature 608, 122–134 (2022). https://doi.org/10.1038/s41586-022-04997-3.

Read the papers, locate, download, and familiarize yourself with the dataset provided by the authors. 

## Questions

### Q1: The Geography of Social Capital in the United States

You will replicate [Figure 2a of the first paper](https://www.nature.com/articles/s41586-022-04996-4/figures/2). But while the figure in the paper is static, you will create an interactive figure, like the one that is available online at https://www.socialcapital.org/. You can see an example of what you should do [here](economic_connectedness_zip.html).

In the figure, the social capital is represented by the Economic Connectedness (EC). Economic Connectedness is the degree to which people with low and high Socioeconomic Status (SES) are friends with each other. More formally, to define EC we start by measuring each individual's $i$ share of friends from SES quantile $Q$:

$$ f_{Q, i} = \frac{[\textrm{Number of friends in SES quantile}\ Q]_i}{\textrm{Total number of friends of}\ i} $$

Then we normalize $f_{Q,i}$ by the share of individuals in the sample who belong to quantile $Q$, $w_Q$ (for example, $w_Q = 0.1$ for deciles) to get the Individual Economic Connectedness (IEC):

$$ \mathrm{IEC}_{Q, i} = \frac{f_{Q, i}}{w_Q} $$

The level of EC in a community $c$ is the defined as the mean level of individual EC of low-SES $L$ (for example, below-median) members of that community, as follows:

$$ \mathrm{EC}_{c} = \frac{\sum_{i \in L \cap c}\mathrm{IEC}_i}{N_{Lc}} $$

where $N_{Lc}$ is the number of low-SES individuals in community $c$.

In the figure and in what follows, the EC is twice the share of friends with above-median SES among people with below-median SES; that follows from the above definitions for $w_Q = 0.5$.

The map is constructed using Plotly. The data are displayed per county. When the pointed hovers each county, it should display the name of the county and the state it belongs to, the code of the county, and the Economic Connectedness of the county. If there are no data for a particular county, it should be painted with a distinct color (in our example it is painted gold) and the economic connectedness should be given as "NA".

Data for social capital can be found at the [Social Capital Atlas Datasets](https://data.humdata.org/dataset/social-capital-atlas).

### Q2: Economic Connectedness and Outcomes

You will replicate [Figure 4 of the first paper](nature.com/articles/s41586-022-04996-4/figures/4). The figure is a scatter plot of upward income mobility against economic connectedness (EC) for the 200 most populous US counties. The income mobility is obtained from the [Opportunity Atlas](https://www.nber.org/papers/w25147), whose replication data can be found [here](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/NKCQM1). Your figure should look like the following one.

![household_income_economic_connectedness](https://github.com/CodeNinjaTech/Economic-Connectedness-Analysis/assets/143879796/675bb9ab-b3a6-4a26-8d1c-9be13eb6780b)

### Q3: Upward Income Mobility, Economic Connectedness, and Median House Income

You will replicate [Figure 6 of the first paper](https://www.nature.com/articles/s41586-022-04996-4/figures/6). The figure is a scatter plot of economic connectedness (EC) against median household income. You will need to compile data from replication package of the papers with data from the Social Capital Atlas Datasets. The color of the dots corresponds to the child's income rank in adulthood given that the parents' income is in the 25th percentile. The colors correspond to five intervals, which are the quintiles dividing our data. Your figure should look like the following one.

![upward_mobility_connectedness_parental_income](https://github.com/CodeNinjaTech/Economic-Connectedness-Analysis/assets/143879796/542539a1-e32d-486c-a73c-e45f16fdfdb4)

### Q4: Friending Bias and Exposure by High School

You will replicate [Figure 5a of the second paper](https://www.nature.com/articles/s41586-022-04997-3/figures/5). The figure depicts the share of students with high parental Socioeconomic Status (SES) against the friending bias of students of low parental SES, with data from the Social Capital Atlas Datasets. 

Note that to get the share of high-parental-SES students, which is the $x$-axis, you need to take the mean exposure to high-parental-SES individuals by high school and divide it by two. That is because the mean exposure to high-parental-SES individuals by high schools is defined as two times the average share of highp arental-SES individuals within three birth cohorts, averaged over low-parental-SES users.

Note also that both $x$ and $y$ axis are percentages and the $y$ axis is reversed.

In the end, your figure should look like the one below. Text placement might differ slightly. The annoted high schools are `00941729`, `060474000432`, `170993000942`, `170993001185`, `170993003989`, `171449001804`, `250327000436`, `360009101928`, `370297001285`, `483702004138`, `250843001336`, `062271003230`, `010237000962`, `00846981`, `00852124`.

![friending_bias_exposure](https://github.com/CodeNinjaTech/Economic-Connectedness-Analysis/assets/143879796/749d5eb2-1ab1-4e65-b085-7bb4bbe6021c)

### Q5: Friending Bias vs. Racial Diversity

You will replicate [Extended Data Figure 3](https://www.nature.com/articles/s41586-022-04997-3/figures/9) of the second paper. The figure depicts friending bias against racial diversity. Racial diversity is defined by the [Herfindahl-Hirschman Index (HHI)](https://en.wikipedia.org/wiki/Herfindahl%E2%80%93Hirschman_index), borrowed from investing. Translated here, it is $ 1−\sum_{i}{s_i}^2$, where $s_i$ is the fraction of race/ethnicity $i$ (Black, White, Asian, Hispanic, Native American).

As you can see, the figure contains two scatter plots with their respective regression lines, one for college data and the other for neighborhood data. Each of the two plots displays binned data (that's why you don't see loads of dots and diamonds). The bins are produced by dividing the $x$-axis into ventiles (i.e., 5 percentile point bins); then we plot the mean of the $y$-axis variable against the appropriate mean of the $x$-axis variable in each ventile. 

The mean of the $x$-axis variable, the HHI index, is the weighted mean of HHI:

* For the college plot, the weights are given by the mean number of students per cohort.

* For the neighborhood plot, the weights are given by the number of children with below-national-median parental household income.

The $y$-axis variable:

* For the college plot, it is the mean of the college friending bias.

* For the neighborhood plot, it is the mean of the neighborhood friending bias.

In the end, your figure should look like the following.

![friending_bias_racial_diversity](https://github.com/CodeNinjaTech/Economic-Connectedness-Analysis/assets/143879796/1d5c7f35-a898-4240-866e-2a1840fad7c4)

## Submission Instructions

You will submit a Jupyter notebook that will contain all your code, data, and analysis. Ensure that the notebook will run correctly in a computer that is not your own. That means, among other things, that it does not contain absolute paths. Remember that a notebook is not a collection of code cells thrown together; it should contain as much text as necessary for a person to understand what you are doing.

## Honor Code

You understand that this is an individual assignment, and as such you must carry it out alone. You may seek help on the Internet, by Googling or searching in StackOverflow for general questions pertaining to the use of Python,  libraries, and idioms. However, it is not right to ask direct questions that relate to the assignment and where people will actually solve your problem by answering them. You may discuss with your fellow students in order to better understand the questions, if they are not clear enough, but you should not ask them to share their answers with you, or to help you by giving specific advice.
