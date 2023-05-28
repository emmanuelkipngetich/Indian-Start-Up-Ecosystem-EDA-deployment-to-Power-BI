# Indian-Start-Up-Ecosystem-EDA-deployment-to-Power-BI
1.0 Introduction
In this article, I provide a summary of my investigation into and analysis of funding for Indian start-ups from 2018 to 2021.
The goal was to use the data to explore the ecosystem, uncover insights, and recommend the best course of action to my fictional team that is attempting to enter the Indian start-up ecosystem.
To understand the business, I made use of the CRISP-DM framework. I also made use of the following project management activities:
Determine business objectives
Assess situation
Determine data mining goals
Produce project plan

1.1 The Data
The data for each year of funding was in a separate CSV file, meaning they had to be merged at a point. The shared columns in the files were as follows (column name: description):
Company/Brand: name of the company/start-up
Founded: the year the start-up was founded
Sector: sector of operation
About Company/What it does: description of the company
Founders: founders of the company
Investor: investors in the deal
Amount($): raised funds
Stage: round of funding
Headquarters: headquarters of the company

2.0 Ask Stage
At this stage, we bring the objective into view and put down the questions that we intend to answer at the end of the analysis process.
With the main aim of eventually recommending the team on what to do in entering the Indian ecosystem, I made the following hypothesis and set the questions below:
2.1 Hypothesis
Null Hypothesis: Having the most number of start-ups in a city doesn't mean having the highest amount of funding in the city.
Alternative Hypothesis: The higher number of start-ups in a city reflects the amount of funding the city receives.
2.2 Questions
For the hypothesis, the following questions were put forward to be answered:
How many start-ups are there per sector of the ecosystem?
What is the amount of funding per sector?
What is the trend of funding across the years?
How many start-ups were funded each year?
What is the distribution of start-ups per city?
Which city has the most funded start-ups?
What is the amount of funding per sector over the years?

3.0 Data Preparation and Processing
At this stage, we organize the data to make it fit for analysis. Cleanliness and consistency of data are the objectives here.
3.1 Loading packages
To start with, the basic packages for the analysis were loaded. These were:
Pandas: for data cleaning and manipulation
Numpy: for data cleaning and manipulation
Matplotlib: for visualisations
Seaborn: for visualisations
Re: for regular expressions
Warnings: to deal with the warnings

3.2 Notes from Previewing the DataFrames
The individual datasets were then loaded as Pandas DataFrames. The first note was the differences in the number of columns in the datasets: 2018 (6), 2019 (9), 2020 (10), and 2021 (9). Other observations from looking at the individual datasets are as follows
3.2.1 The 2018 DataFrame
The DataFrame has 526 rows and 6 columns.
The unknown values in the amounts column were replaced with 1.
The amounts in the 2018 DataFrame are a mix of Indian Rupees (INR), US Dollars (USD) and English Pound meaning they have to be converted into the same currency.
The industry and location columns have multiple information. A decision is to select the first value of each column.

3.2.2 The 2019 DataFrame
The DataFrame has 89 rows and 9 columns.
The data type of the "Founded" column is set to float64. It should be set to a string for uniformity.
The headquarter column has multiple information. A decision is to be made to select the first value before the separator(,) as the main value or representing that column.

3.2.3 The 2020 DataFrame
There is an extra column called "Unnamed:9", giving it a total of 10 columns. It should be dropped to ensure complete alignment with the other DataFrames for ease of concatenation.

3.2.4 The 2021 DataFrame
The data type of the "Founded" column is set to float64. It should be set to a string for uniformity.

3.2.5 General Notes
The columns in 2018 are different from those of 2019–2021, meaning they have to be renamed before concatenation.
The currency signs and commas have to be removed from each amount column for each DataFrame.
All the columns with amounts have to be set to float.
All the years of funding and the years founded should be converted to strings.
The respective years of funding have to be attached to each DataFrame before combining.

3.3 Assumptions
The average Indian Rupee (INR) to US Dollar (USD) rate for the relevant year will be used for currency conversions.
The first values of industry and location in the 2018 data are the primary sector and headquarters respectively.
Amounts without currency symbols in the 2018 dataset are in USD.
Imputations will not be made for undisclosed and/or unavailable (missing) amounts due to the uncertainties, risks of misstatements and possible misleading effects on the analyses.

3.4 Cleaning the Data
Given that this article is to present a summary, I will focus on the major activities performed on the DataFrames. The detailed functions will be found in the notebook, a link to which will be attached at the end of the article.
I applied string formatting to all columns except the amounts columns which were formatted as numerics.
I separated the values in the location and industry columns using a comma as the delimiter and selected the first value in the split column as the primary sector.
For the 2018 Amount column, I created two new columns to help with the currency conversion and then dropped them after standardizing the amounts.
I removed all commas and currency signs from the "Amounts" columns.
I replaced the "Undisclosed" text in the "Amounts".
I dropped the founders column as it did not form a part of my answers to my questions.
I replaced notable misplaced and/or erroneous values in the respective rows.
I dropped the extra unnamed in the 2020 DataFrame.
For each DataFrame, I appended a column indicating the year of funding

The columns in the 2018 DataFrame were renamed to match the other DataFrames, after which it was concatenated with the other DataFrames. I then brushed up with the following:
Reformatted all amounts as numerics and replaced nulls with zeros.
Formatted funding years and years founded as strings.
Dropped all duplicates and reset the index.
Did more column-specific cleaning (ref. notebook).

4.0 Answering the Questions
Here, I combine the "Analyse" and "Share" stages of the data analysis process through the code and visualizations.
4.1 How many startups are there per sector of the ecosystem?
From the graph, we can conclude that the IT & Engineering sector has the highest number of start-ups followed by the financial and commerce sector. The education sector come ins as the sector with the least start-ups.
4.2 What is the amount of funding per sector?
The financial sector comes in as the most funded sector with slightly above 1.6billion dollars in funding. The services sector come in second followed by IT & Engineering. The least funded sector is the Agriculture sector.

4.3 What is the trend of funding across the years?
As can clearly be seeen, as the years go by, the amount of funding increases. However, the funding drops in 2019 compared to in 2018.
4.4 How many start-ups were funded each year?
2021 was the year where most startups were funded followed by 2020 while 2019 had the least funded start-ups.
4.5 What is the distribution of start-ups per city?
Bangalore happens to be India's Silicon Valley as most start-ups seem to thrive in that particular city. Mumbai also seems to favor growth of start-ups. Haryana appears to be the least favorable cities of all.
4.6 Which city has the most funded start-ups?
Mubai has the most funded start-ups despite not having the most start-ups. Bangalore which has the most start-ups comes second. We could therefore be right to claim that most start-ups in Mumbai are in the financial sector.
4.7 What is the amount of funding per sector over the years?
The year 2020 had the sector with the most funding(Services), which received slightly below 0.8billion. The other years had close to uniform funding but in different sectors.

5.0 Deployment to Power BI.
Now that we have all the visualizations in the jupyter notebook, I decided to move them to Power BI using python scripter. The final visualization having added a pie chart and visualization cards looked like this:

5.1 Conclusion
Given that funding to startups over the period was more in Mumbai yet Bangalore was the city with the most start-ups, we fail to reject the null hypothesis.
5.2 Recommendations to the Team
Prioritise the IT & Engineering and Financial sectors for further studies into the possible establishment of the startup.
Prioritise Bangalore and Mumbai as the possible locations for the startup.
They are more likely to receive funding in the coming years as funding keeps increasing.
