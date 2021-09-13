# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 1: Standardized Test Analysis

### Problem Statement

The new format of the SAT was released in Mar 2016, as part of the team working in the College Board, we have been tasked by the Board to look at increasing SAT participation rates across the various states.The Board noticed that lower SAT test participation rates in comparison to our competitor, the ACTs, has impacted our revenue.
Hence, a good starting point would be to look at the current SAT participation rate in comparison to ACTs. As well as, the current demographics and what pain points they are facing. 

My problem statement is: 
How the College Board might work to increase the participation rate among high school students in taking SAT college entrance test in 3 states-Kansas, Minnesota & Massachusetts?

---

### Background
The SAT and ACT are standardized tests that many colleges and universities in the United States require for their admissions process. This score is used along with other materials such as grade point average (GPA) and essay responses to determine whether or not a potential student will be accepted to the university.

The SAT has two sections of the test: Evidence-Based Reading and Writing and Math ([*source*](https://www.princetonreview.com/college/sat-sections)). The ACT has 4 sections: English, Mathematics, Reading, and Science, with an additional optional writing section ([*source*](https://www.act.org/content/act/en/products-and-services/the-act/scores/understanding-your-scores.html)). They have different score ranges, which you can read more about on their websites or additional outside sources (a quick Google search will help you understand the scores for each test):
* [SAT](https://collegereadiness.collegeboard.org/sat)
* [ACT](https://www.act.org/content/act/en.html)

Standardized tests have long been a controversial topic for students, administrators, and legislators. Since the 1940's, an increasing number of colleges have been using scores from sudents' performances on tests like the SAT and the ACT as a measure for college readiness and aptitude ([*source*](https://www.minotdailynews.com/news/local-news/2017/04/a-brief-history-of-the-sat-and-act/)). Supporters of these tests argue that these scores can be used as an objective measure to determine college admittance. Opponents of these tests claim that these tests are not accurate measures of students potential or ability and serve as an inequitable barrier to entry. Lately, more and more schools are opting to drop the SAT/ACT requirement for their Fall 2021 applications ([*read more about this here*](https://www.cnn.com/2020/04/14/us/coronavirus-colleges-sat-act-test-trnd/index.html)).

---

### Datasets

#### Provided Data

There are 4 datasets included in the [`data`](./data/) folder for this project. 
* [`act_2017.csv`](./data/act_2017.csv): 2017 ACT Scores by State ([source](https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows))
* [`act_2018.csv`](./data/act_2018.csv): 2018 ACT Scores by State ([source](https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows))
* [`sat_2017.csv`](./data/sat_2017.csv): 2017 SAT Scores by State ([source](https://blog.collegevine.com/here-are-the-average-sat-scores-by-state/))
* [`sat_2018.csv`](./data/sat_2018.csv): 2018 SAT Scores by State ([source](https://blog.collegevine.com/here-are-the-average-sat-scores-by-state/))

For SAT, We have the 2017 & 2018 mean participation rate and mean SAT scores for 2 subjects:Evidence-Based Reading and Writing, Math, and the mean Total Score by states.
Each year's SAT data consists of 51 rows by 5 columns, each row represents an US state in relation to its individual columns. 

    - SAT Participation Rate
    - Average Evidence-Based Reading and Writing Score
    - Average Math Score
    - Total Average Score

For ACT, We have the 2017 to 2018 participation rate and mean ACT scores by states.
In 2017 ACT data, there is the mean participation rate and the breakdown of mean scores by all 5 subjects: English, Math, Reading, Science and Compiste. 
However in 2018 ACT data, there is the mean participation rate and mean scores for 1 subject: Composite.
Both 2 years ACT data has 52 rows, however US has 51 states only. We will further look at the data and do some necessary data examinations and cleaning before proceed on further analysis. 

    - ACT Participation Rate
    - Average English Score
    - Average Math Score
    - Average Reading Score
    - Average Science Score
    - Average Composite Score
    
#### Additional Data
From the dataset provided to this project, it is obviously an incomplete data (E.g. missing of ACT 2018 other subjects mean score other than Composite.) We've searched SAT and ACT participation rate and mean scores for all subjects for year 2017 & 2018 to compare with dataset provided to clear any data errors. Also through research, participation rate is highly impact on the states policies and whether they are required to take SAT or ACT exam. These are facts contribute to the surge of SAT participation rate, We would take into consideration of some additional data as a suppliment to the analsysis.

Additional 4 datasets-added into this project analyze:
* [`sat_or_act_requirements.xlsx`](./data/sat_or_act_requirements.xlsx): states required for SAT or ACT
* [`Census Bureau-designated regions and divisions(US_wiki).xlsx`](./data/Census-Bureau-designated-regions-and-divisions(US_wiki).xlsx): Census Bureau-designated regions and divisions of all US 51 States
* [`Average ACT Scores (Source)_compared.xlsx`](./data/Average-ACT-Scores-(Source)_compared.xlsx): 2017 & 2018 ACT mean scores by States(published by Digest of Education Statistics)
* [`Average SAT Scores (Source)_compared.xlsx`](./data/Average-SAT-Scores-(Source)_compared.xlsx): 2017 & 2018 SAT mean scores by States (published by Digest of Education Statistics)

---

### Data Dictionary
Blow has shown the data dictionary for the final dataset (consists of 2017-2018 SAT & ACT data):

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**state**|*object*|SAT/ACT|US states name, total 51 states|
|**sat_17_participation**|*float*|SAT|2017 SAT Mean participation rate, range: 0-1|
|**sat_17_ebrw**|*int*|SAT|2017 SAT-mean score of Evidence-Based Reading and Writing, range: 200-800|
|**sat_17_math**|*int*|SAT|2017 SAT-mean score of MATH, range: 200-800|
|**sat_17_total**|*int*|SAT|2017 SAT mean total score, range: 400-1600|
|**act_17_participation**|*float*|ACT|2017 ACT Mean participation rate, range: 0-1| 
|**act_17_english**|*float*|ACT|2017 ACT mean score of English, range: 1-36|
|**act_17_math**|*float*|ACT|2017 ACT mean score of MATH, range: 1-36|
|**act_17_reading**|*float*|ACT|2017 ACT mean score of READING, range: 1-36|
|**act_17_science**|*float*|ACT|2017 ACT mean score of SCIENCE, range: 1-36|
|**act_17_composite**|*float*|ACT|2017 ACT mean score of COMPOSITION, range: 1-36|
|**sat_18_participation**|*float*|SAT|2018 SAT Mean participation rate, range: 0-1|
|**sat_18_ebrw**|*int*|SAT|2018 SAT-mean score of Evidence-Based Reading and Writing, range: 200-800|
|**sat_18_math**|*int*|SAT|2018 SAT-mean score of MATH, range: 200-800|
|**sat_18_total**|*int*|SAT|2017 SAT mean total score, range: 400-1600|
|**act_18_participation**|*float*|ACT|2017 ACT Mean participation rate, range: 0-1| 
|**act_18_composite**|*float*|ACT|2017 ACT mean score of COMPOSITION, range: 1-36|
|**is_sat_required**|*object*|SAT/ACT|The state requires or not require SAT test, value: Yes/No|
|**is_act_required**|*object*|SAT/ACT|The state requires or not require ACT test, value: Yes/No|
|**region**|*object*|SAT/ACT|Regions for each state, total 4 regions|
|**division**|*object*|SAT/ACT|Divisions for each state, total 9 divisions|

---

### Exploratory Data Analysis
####  Summay of the EDA findings:

##### [Lowest Participation Rate] by Region-State
- 2017 SAT-0.02 (3 states): Midwest(2 states)-Iowa,North Dakota,South-Mississippi
- 2018 SAT-0.02 (1 state): Midwest-North Dakota
- 2017 ACT-0.08 (1 state): New England-Maine
- 2018 ACT-0.07 (1 state): New England-Maine

##### [Highest Participation Rate] by Region-State
- 2017 SAT-1 (3 states): Northeast-Connecticut, South-Delaware, Midwest-Michigan
- 2018 SAT-1 (5 states): West(2 states)-Colorado, Idaho, Northeast-Connecticut, South-Delaware, Midwest-Michigan
- 2017 ACT-1 (17 states): 
  - South(9 states)-Alabama,Arkansas,Kentucky,Louisiana,Mississippi,North Carolina,Oklahoma, South Carolina,Tennessee
  - West(5 states)-Colorado,-Montana,Nevada,Utah,Wyoming 
  - Midwest(3 states)-Minnesota, Missouri, Wisconsin
- 2018 ACT-1 (17 states): 
  - South(9 states)-Alabama,Arkansas,Kentucky,Louisiana,Mississippi,North Carolina,Oklahoma,South Carolina,Tennessee
  - West(6 states)-Colorado,Montana,Nevada,Utah,Wyoming,Nebraska, Midwest(4 states)-Ohio, Minnesota,Missouri,Wisconsin

##### [100% on a given test with rate of change year-to-year]
- SAT drops:    South-District of Columbia
- SAT increases: West(2 states)-Colorado, Idaho
- ACT drops: West-Colorado, Midwest-Minnesota
- ACT increases: West-Nebraska, Midwest-Ohio

##### [Above 50% participation on both tests either year]
- 2017-3 states: South(2 states)-Florida,Georgia, West-Hawaii
- 2018-5 states: South(5 states)-Florida, Georgia, Hawaii, South Carolina, North Carolina

##### [Year over Year increased]
- SAT-33 states:
  - South(13 states)-Alabama,Arkansas,District of Columbia,Georgia, Maryland，Mississippi，North Carolina，Oklahoma，South Carolina，Tennessee，Texas，Virginia，West Virginia   
  - West(9 states)-Alaska,California,Colorado,Hawaii,Idaho,New Mexico，Oregon，Utah，Washington
  - Northeast(7 states)-Maine，Massachusetts，New Jersey，New York, Pennsylvania，Rhode Island，Vermont
  - Midwest(5 states)-Illinois,Iowa,Minnesota，Missouri，Ohio  
- ACT-7 states:
  - West（3 states)-Arizona，New Mexico，Oregon
  - Midwest(3 states)-Iowa，Nebraska，Ohio
  - South(1 states)-Maryland

##### [Year over Year decreased]
- SAT-3 states:
  - West(2 states): Arizona,Nevada
  - South(1 state): Florida
- ACT-26 states:
  - West(6 states)-Alaska,California,Colorado,Hawaii,Idaho,Washington
  - Northeast(9 states)-Connecticut, Massachusetts, Maine,New Hampshire, New Jersey,Pennsylvania,New York,Rhode Island,Vermont     
  - Midwest(6 states)-Illinois,Indiana,Kansas,Michigan,Minnesota,South Dakota
  - South(5 states)-Virginia,West Virginia,Delaware,Florida,Georgia

---

### Data Visualization

- ACT 2017 participation and SAT 2017 participation are strong negatively correlated (-0.84). Possible reason could be states that participated in one test tends to forgo another. Similarly in 2018 as well (-0.87).
- SAT 2017 participation and SAT 2018 participation are strong positively correlated (0.87). States who participate in SAT 2017 tends to participate in 2018 as well. Similary for ACT test, states who take part in ACT in 2017 will also likely take part in 2018 (0.92).
- ACT 2017 subjects english, math, reading, science and composite generally negatively correlated to ACT 18 participation. Possible reason could be a drop in participation compared to 2017. On the other hand, ACT 2017 subjects have positve relationship with SAT 2018 participation. This could be because, states who participate in ACT 2017 are switching to SAT in 2018.
- SAT 2018 participation and SAT 2018 subjects ebrw (-0.76), math(-0.79), total(-0.79) are generally negatively correlated. This means higher participation leads to lower score, vice versa, lower participation leads to higher score.

---

### Conclusion & Recommendatations

The 3 states located Midwest region Kansas & Minnesota, and at Northeast region the Massachusetts state are chosen to provide suggestions by College Board. According to American School and University, Kansas was ranked top 6 in student to population ratio, Minnesota was ranked top 9 and Massachusetts at top 10. It would be a great boost if SAT can win them over. Moreover, they are states sitting on the fence, they do not favour either SAT or ACT. 

My suggestions based on the marketing 4ps are as follows:

* Price: 
   - Provide free test preparation materials and review lessons by partnering up with study platforms (eg. Khan academy) 
   - Lower the entry barrier for low-income students by offering testing fee waivers

Our strategy for SAT is to increase participatin rate, however from one of above scatter plots there's a strong negative correlation between participation rate and total score. But when doing the research, We also found an interesting part that rich students got better score in the SAT test.One reason wealthier students get higher SAT scores is because they can afford to take the test several times, which has been known to increase a students’ score.

The cost to take the SAT during the 2018-2019 school year was about 47.5USD for the basic test and 64.50USD to take the test with the full essay section. To take an SAT subject test, students must pay a 26USD registration fee, 22USD for each additional test and 26USD for each language test.These costs can be prohibitively expensive for many students. 

The College Board can try to increase SAT participation through fee waivers for low-income students, and by taking steps to identify eligible students and automatically giving them the fee waiver benefits. Also by parternership with study platforms, e.g. Khan Academy students is able to get free test preparation materials and review lessons to help get more familiar with the test, build up their confidence and work on a higher test score eventually. 

* Product:
   - Improve testing convenience by allowing remote arrangements to be made.
   - Allow exam candidates to reschedule their examination date 

Due to Covid 19, US Nationwide, more than 1,550 colleges have made the test optional for admissions, increasing about 50% since 2020, that's about two-thirds of all colleges nationwide according to Akil Bello of the National Organization for Fair and Open Testing. Many schools decided either just before or right after the start of the coronavirus pandemic, said Bello, who is senior director of advocacy and advancement. This is a big challenge to College Board.

In this current unprecedented time, how College Board could provide the most oppotunity for the greatest number of students is one of our key considerations, We want to ensure that all students have the best opportunity to persue higher education. Also We know that many students have had difficulty taking a standadized test due to cancellations. By revising the policies and giving the options to select for remote test arrangement, also allowing students to reschedule their examination date, these actions allow for more flexibility and eliminate a potential barrier.  

* Place: 
   - Target states with bigger college students population and also which have not made the SAT a mandatory high school graduation requirement (Kansas, Minnesota & Massachusetts)
   - To collaborate with school districts on offering more SAT School Days.

Gerneally our target are states which have not made the SAT a mandatory hight school graduation requirement, and we sugguest to work focus on the prompt SAT exam for the 3 states-Kansas, Minnesota & Massachusetts, as they have higher student populations. It would be a big success and contribute to our revenue a lot if we could win them over. 

The College Board can try to cllaborate with school districts on offering more SAT School Days. By breaking down barries to access, SAT School Days can have a profound impact, it generally includes a free SAT exam offered during the school
day to make student participation as convenient as possible.

Again, We talk about the convience, students don't have to worry about locating or getting to the testing site, School Days testing also won't disrupt weekend plans, jobs or family time. School Days also improve the comfortability for students to take the test in familiar surroundings with people & place they know. Giving students an equal platform to score better well would be a better strategy than only looking at how to increase the participation rate.

* Promotion:
   - Team up with the states' education leaders to roll out college‐ and career‐readiness initiatives so that the students are more encouraged to think about their future
   - Provide college entry assistance to students who take the SAT exam.

College Board can team up with the states' education leaders to roll out college-and career-readiness initiatives so that the students are more encouraged to think abou their future. For instance, transforming the notion that "attending college is an option" to "attending college is an expectation", indirectly leads to the desire to succeed and a drive to attend college. Understanding students' opinions and knowledge about college, as well as their vision for the future will help to
establish a culture of college and career readiness, utimately increase SAT preparation and participation.

---

### Future Work & Data Collection Considerations

There are other data We could explore further in future analysis and improvement:

1. The population, race and geographic data for each state in the test taken year. Some states may face aging problem, or with low income might contribute to low or high participation rate on the test, or different race might have preference towards one tet (SAT or ACT).
2. The types of schools (private or public) that participated in SAT or ACT, this might show some trends on participation rate and average score. 
3. High school students family income, to analyze if there's any correlation the higher partication rate with certain groups of family income. This could help us to target on the students family group and provide any free test/test fee waiver to other family income groups.  
4. Parents education background--there's a possible pattern we could find if with this data, that higher educated parents have a higher influence on their children to achieve a higher test score.
