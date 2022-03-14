# An Analysis of Kickstarter Campaigns

## Overview of Project

For this project we have received an excel spreadsheet containing information of crowdfunding companies. This excel file is a very popular tool to store information and perform calculations, as well as summaries and charts that is very often used to back up strategic decisions, analyzing results and allow to visualize and process large quantities of data.

### Purpose

The purpose of this project is to provide with data summaries and visuals from the data received in the **Kickstarter_Challenge.xlsx** file. We will provide with 2 new analysis for Louise's review. These 2 new analysis will be delivered to her as charts in order to allow her to know how different fundraising campaigns performed based on their launch dates and their funding goals.
---

## Analysis and Challenges

---
Crowdfunding has become a staple in order to fundraise for any kind of campaigns, in order to create a new campaign for any kind of event the following parameters are very important:
- the final amount of money needed to reach our funding goal
- when is the funding campaign starting
- the duration of the campaign

--- 
### Analysis of Outcomes Based on Launch Date

From the kickstarter excel sheet, we can find columns that have a column name related to dates: 
- deadline
- launched_at
---
The values inside of these columns doesn't seem familiar with date notations that are more practical to understand. The type of the column is also listed as a general field. 
---
Using the Excel Formulas DATE() and YEAR() applied to the columns we are able to obtain a date format that makes it easier to filter on and to create visuals to assess how long the most successful campaigns run for and if there is a possible relation of the launch date to the final outcomes of the campaign.

Functions used for Date Created Converted, Date Ended converted and Years:

```
=(((J2/60)/60)/24)+DATE(1970,1,1)

=(((I2/60)/60)/24)+DATE(1970,1,1)

=YEAR(S2)

```

![image of new date columns](/resources/Dates_ScreenShot.png)


By creating a summary table (pivot table) that presents only the concluded campaigns and their outcome. We can visualize that for the fundraising campaigns that are related only to THEATRE category and over all the years present in the Kickstarter data.

![image of chart Theatre outcomes based on launch dates](/resources/Theater_Outcomes_vs_Launch.png)


---

### Analysis of Outcomes Based on Goals
---

The main characteristic of crowdfunding campaigns if the actual money goal. If successful what seems to be the most common amount to fundraise for a specific product or even if it failed it is important to see how far was the campaign from their goal. 

The definition of money ranges for the campaign goal and percentages in order to visualize an optimal Money goal for theater-plays in order to increase the potential success by selecting a goal with the most present data of success was very important.
The conditional count based on the final outcome and the money range was achieve by the excel function COUNTIFS() making sure that the column references and the proper outcome selection was properly type was essential.

Samples of the functions used count using money ranges for the campaigns reported in the kickstarter data.

```

= COUNTIFS(Kickstarter!F:F,"successful",Kickstarter!R:R,"plays",Kickstarter!D:D,"<1000")
= COUNTIFS(Kickstarter!F:F,"successful",Kickstarter!R:R,"plays",Kickstarter!D:D,">=1000",Kickstarter!D:D,"<4999")
= COUNTIFS(Kickstarter!F:F,"failed",Kickstarter!R:R,"plays",Kickstarter!D:D,">=1000",Kickstarter!D:D,"<4999")
= COUNTIFS(Kickstarter!F:F,"canceled",Kickstarter!R:R,"plays",Kickstarter!D:D,">=40000",Kickstarter!D:D,"<44999")

```
---

Samples of the sum function and percentage columns
```
=SUM(B2,C2,D2)
=IFERROR(B2/E2,0)
```

![image of Outcomes based on launch date](/resources/Goal_ScreenShot.png)

While troubleshooting some of my values I found useful to also consult the Subcategory Statistics pivot table

![image of Outcomes based on launch date](/resources/SubcatStat_ScreenShot.png)

### Challenges and Difficulties Encountered

A constant difficulty was typos! I would find that I was modifying the values of the cells also while adding references to formulas. It did had a lot to do with lack of familiarity with Microsoft Excel, however I did find quite dangerous that the content of the cells could be modified so easily sometimes by only hovering over. Having worked in the past a database developer tool where the dataset can be locked to avoid those mistakes.

I also used some extra fields on the created pivot tables and referred to other summaries in order to validate some of the totals.


## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

At a very general glance at the chart it seems that the month with the lowest number of successful campaigns are  January-February-March and then September-October-November-December. It is tempting to assimilate these months with the Winter and fall seasons, however it is important to remember that the kickstarter spreadsheet contains data from multiple countries and some of them can be in the south hemisphere where the seasons are actually reversed.

As another observation the number of failed campaigns is also at it highest during the same period April to August.

In order to define where the highest values are, it was useful to add a Median function next to the pivot table and chart.Adding the median as a line to the chart could be potentially more useful.

![image of new date columns](/resources/addedMedian_ScreenShot.png)

As another observation, the user can also review the results year by year or by making the Years filtering to more recent campaigns, I found it interesting how different the graph looks if I focused only on the last 3 years of data available in the kickstarters data:

![image of new date columns](/resources/yearsFilter_ScreenShot.png)



- What can you conclude about the Outcomes based on Goals?

![image of Outcomes based on launch date](/resources/Otcomes_vs_Goals.png)

While Filling in the Total Projects column the simple addition of the 3 outcomes by row seemed maybe too simple of a calculation or parameter; by making sure that the total Project was meant for the Goal ranges and not the complete set of all the projects (I was tempted to make a SUM of all the number of successful outcomes column instead of only the row)

The graph has an interesting shape however it seems that it makes it very clear which GOAL ranges are the best suited for campaign goals.
Anywhere where the BLUE line (Percentage Successful) is above the Green line with the mist being the crossing points.
From the graph there are 2 ranges where the Successful line is above

From Goal less than 1000$ to GOAL 15000$ to 19999$ (this section seems also quite evident by looking at the resulting table, that is where the biggest numbers are populated in both columns Number Successful and Number failed)

The graph allows us to detect faster another range where the number os Successful Goals are also above the percentage failed:

From Goal 35000$ to 39999$ and From Goal 40000$ to 44999$ 


- What are some limitations of this dataset?

For me part of the limitations is how easy alterable this dataset is, I was finding myself clearing values unintentionally. 

- What are some other possible tables and/or graphs that we could create?

I found myself wanting to overlap median graphs to both charts and some conditional formatting allowing us tp located max and min values in a more efficient way. 

![image of new date columns](/resources/CategoryStat_ScreenShot.png)


