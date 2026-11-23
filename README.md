# Student Survey Analysis (Power BI)
Exploratory data analysis (EDA) of a student survey, presented as an interactive Power BI report.

## Project overview
The goal of this project was to analyse responses of a survey from a student group (n = 26). The data was first collected using Google Forms and then presented  in a Power BI report.

The survey focuses on environmental and social issues, sustainable development, and personal life satisfaction. The analysis describes the profile of the group and explores how knowledge, attitudes, price sensitivity and social media use relate to each other.

## POWER BI report
### Structure
The structure of the report is presented below:

| Page | What it shows |
|---|---|
| Respondent profile | Group structure: gender, age, employment status, place of residence |
| Environmental knowledge | Distribution of knowledge scores (0-6), average score, share of correct answers per question, and a gender comparison |
| Attitudes and behaviours | Average agreement and distribution of answers for 12 statements (scale 1-5) |
| Barriers and willingness to pay | Barriers to buying eco-friendly products, acceptable price premium, factors increasing willingness to pay |
| Motivations and social media | Drivers of pro-environmental behaviour, frequency of eco content on social media, social media statements |
| Relationships | Knowledge, social media influence and price premium compared with the attitude index, plus a comparison by gender |

### Respondent profile
- The group has 26 students: 15 women and 11 men, with an average age of 22 (twenty one of respondents are aged 22).
- Most respondents (19 of 26) live in cities with over 250k inhabitants.
- Half of the group (13) combines studies with casual work, 9 people work in the field an 4 are currently not active.
![Respondent profile](screenshots/02_dashboard_profile.png)

### Environmental knowledge
- The average knowledge score is 3.38 out of 6, and only one student answered every question correctly.
- The best-known topics are the carbon footprint (81% correct) and the cause of climate change (73%).
- The weakest are household water use (38%) and the impact of drink packaging (42%).
- Women answered the climate-cause question and the carbon footprint question correctly more often than men.
- Women answered all the knowledge questions correctly more often than men (60% vs 52%)
![Environmental knowledge](screenshots/03_dashboard_knowledge.png)

### Attitudes and behaviours
- Low-effort habits get the highest score: e-tickets and e-documents (4.7 out of 5), reusable shopping bags (4.5) and reducing waste (4.5).
- Costly or effortful behaviours get the lowest: choosing an eco product despite a higher price (2.4) and checking whether a product is eco-friendly (2.4).
- Checking whether a product is eco-friendly besides general low score, has the most of "1" answers so it's completely not done by a part of group. 
- Pro-environmental attitudes are widespread, but they weaken when a behaviour costs money or time.
![Attitudes and behaviours](screenshots/04_dashboard_attitudes.png)

### Barriers and willingness to pay
- When it comes to choosing between buying an eco or regular product - 50% of respondents would choose the eco one because of habit or better quality. 38% would buy the eco only if the prices were similar, and 8% would always buy the cheaper one.
- "High price" is the most frequent barrier (17 mentions), followed by lack of time to check product information (13) and laziness (11).
- 14 of 26 respondents would pay at most 10% more for an eco-friendly product, and only 3 would pay up to 30%. Also 3 of respondents wouldn't pay no money for a an eco-premium product
- Factors that would change the responders minds are usually: Health of me and my family and Higher quality of eco product
![Barriers and willingness to pay](screenshots/05_dashboard_barriers.png)

### Motivations and social media
- The main drivers of pro-environmental behaviour are care for the environment (17), responsibility for future generations (17) and growing climate awareness (16). Eco-trends are not very important for the group (only 2 respondents)
- Government regulations are named by 12 respondents, family and friends by only 4.
- Respondents often read shared posts (4.2 out of 5), but most see eco content only sometimes (11) or rarely (8).
- Respondents usually don't think that eco content encourages eco actions (2.73/5), they also didn't learn from the eco initiatives online (2.42/5) and usually did not choose to buy products after social media ads.
![Motivations and social media](screenshots/06_dashboard_motivations.png)

### Relationships
>The attitude index is a single score per respondent that summarises their overall pro-environmental attitude. It is the mean of the answers to the 12 attitude statements (att_1 to att_12), each rated on the 1-5 Likert scale (1 = strongly disagree, 5 = strongly agree). A higher value means stronger pro-environmental attitudes and behaviours.
- Knowledge score and attitude index show almost no relationship.
- The attitude index rises with the acceptable price premium: 2.8 for respondents who would not pay more, 3.9 for those accepting 20-30%.
- The attitude index is higher among women (3.8) than men (3.3).
- The groups are small, so these relationships are exploratory only.
![Relationships](screenshots/07_dashboard_relationships.png)

A PDF version of the full report is available in [`dashboard`](dashboard/dashboard.pdf).

## Key findings

1. **Environmental knowledge is moderate.** The average score was 3.4 out of 6 and only one respondent answered all questions correctly. The best-known topics were the carbon footprint (81% correct) and the cause of climate change (73%). The weakest were household water use (38%) and the impact of drink packaging (42%). Women answered the climate-cause question correctly more often than men (93% vs 45%), and the carbon footprint question too (91% vs 73%).
2. **Low-effort habits are common, costly choices are not.** The highest-rated behaviours were using e-tickets and e-documents (4.7 out of 5), reusable shopping bags (4.5) and reducing waste (4.5). The lowest were choosing an eco product despite a higher price (2.4) and checking whether a product is eco-friendly (2.4).
3. **Price is the main barrier.** "High price" was the most frequent barrier (17 mentions), followed by lack of time to check product information (13) and convenience (11). 14 of 26 respondents would pay at most 10% more for an eco-friendly product and only 3 would pay up to 30%.
4. **Eco choice depends on price differences.** 10 respondents would choose the eco product if the price were similar, while 13 would stick to habit or quality regardless of ecology.
5. **Motivations are values-based.** The most frequent drivers of pro-environmental behaviour were care for the environment (17), responsibility for future generations (17) and growing climate awareness (16). Government regulations were named by 12 respondents, family and friends by only 4.
6. **Social media is widely used but has limited eco impact.** Respondents often read shared posts (4.2/5), but most see eco content only sometimes (11) or rarely (8). Posts influence their opinions (3.5/5) more than eco actions (2.73/5) or eco purchases (2.9/5).
## Methodology
Data preparation was done in Power Query:

- Renamed 63 survey columns to short English names grouped by topic (`know_`, `att_`, `val_`, `sci_`, `sm_`, `ps_`); the full mapping is in [`data/data_dictionary.csv`](data/data_dictionary.csv).
- Fixed mistakes in the table and unified inconsistent answer labels.
- Converted Likert answers to numbers (1 = strongly disagree ... 5 = strongly agree). Stress items use 1 = never ... 5 = very often.
- Reverse-scored the four positively worded stress items (6 minus value) and calculated a total stress score (10-50).
- Calculated a knowledge score (0-6) by comparing answers with an answer key; "don't know" counts as incorrect.
- Calculated age (2025 minus year of birth), an attitude index (mean of 12 statements) and a social media eco influence index (mean of 4 statements).
- Split multiple-choice answers (up to 3 options) into separate rows, which gives the tables `barriers_long`, `wtp_long` and `drivers_long`.
- Unpivoted knowledge, attitude and social media questions into long tables for charting.
- Translated answer labels into English.
- Removed columns that could identify respondents (timestamp, year of birth, weight, height).

Data model: `survey_scores` (one row per respondent) is related one-to-many on `respondent_id` to the long tables.
## Limitations
- Small sample (n = 26) from a single class group, so results are descriptive and cannot be generalised.
- Self-reported answers, which may be affected by social desirability.
- Narrow age range (21-23), small subgroups and no statistical significance testing.
- Multiple-choice questions allowed up to three answers, so counts refer to responses, not respondents.
- Questions on personal values, trust in science and perceived stress were prepared in the data but are not visualised in this version of the dashboard.

## Data and privacy
The survey data come from an in-class exercise and contain answers of individual students. To protect their privacy, the raw file and the Power BI file (which embeds the data) are not included in this repository. The repository contains the dashboard screenshots, a PDF export of the report and the data dictionary.

## Tools
Power BI Desktop (Power Query, data modelling, report design) and Excel (source file).

## Author
Bartosz Malinowski
