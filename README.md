# SBIR-Investment-Scope

## Databases used : PostgreSQL, Neo4j, MongoDB

The datasets used are private: 
patentdb : dataset of the patents filed in the US
sbir_award_data : similar dataset can be downloaded from https://www.sbir.gov/sbirsearch/award/all

The SBIR program is a highly competitive program that encourages small American companies to engage in federal R&D projects that could lead to commercialization. The awards allow small companies to explore their technological potential, thereby allowing the US to promote high-tech innovation. Additionally, the technologies that these companies work on could play a pivotal role in their respective fields. Consider a company that invests in small businesses, analyzing this data would facilitate better business decisions. Furthermore, if the product addresses a government need, there is a pretty good chance that it meets a commercial need in commercial markets, too and this can serve as an attraction point for future investors.

### Some questions that can be answered - 
- Identify the activity trends in different technology sectors (patentdb)
- Identify companies and the number of SBIR projects under their wing
- Identify the trend of the investment by government agencies and branches for these SBIR companies.
- Should commercial companies keep an eye on SBIR companies, based on the investments in SBIR companies?

Relevant Columns in the SBIR Dataset:

<img width="510" alt="Screen Shot 2024-03-13 at 9 35 39 AM" src="https://github.com/sagarikasardesai/SBIR-Investment-Scope/assets/21274244/3cd5cd9e-e665-46e0-98aa-156698b77c8f">

Relevant Columns in the PatentDB Dataset:

<img width="495" alt="Screen Shot 2024-03-13 at 9 36 50 AM" src="https://github.com/sagarikasardesai/SBIR-Investment-Scope/assets/21274244/0fe8cbb7-3825-472a-821c-f71035cda2a7">

#### Data Cleaning
Data cleaning was needed to be done since the data obtained from the source was unclean and not suitable for further processing and analysis. For the patentdb dataset, the information was extracted for US-based patents by using the patentids that began with 'US'. 

<img width="706" alt="Screen Shot 2024-03-13 at 9 41 01 AM" src="https://github.com/sagarikasardesai/SBIR-Investment-Scope/assets/21274244/51872b33-8222-43af-a3f5-fb86a0bf7a47">

For sbir_award_data dataset, PostgreSQL was used to clean up the data. Firstly updated all the null values of the dataset to ‘NA’. Converted the type of award_amount to int, and replaced ()- in the phone numbers to ‘NA’ as this would give a cleaner format. Also concatenated address1 and address2 as a single address. These were cleaned for ease of graph creation in Neo4j.

<img width="874" alt="Screen Shot 2024-03-13 at 9 40 37 AM" src="https://github.com/sagarikasardesai/SBIR-Investment-Scope/assets/21274244/c1324516-901d-47a5-ad66-c4c4f84eb79b">

#### Graph Creation
Using the sbir_award_data, graphs using Company, Agency, Branch, Award_Year, and Record_Id have been created in Neo4j. The relations are AWARDED (Branch awarding the
Company), AWARDED_IN( year in which the company is awarded), and IS_PART_OF(Branch within the Agency). Using the cypher query language,
- Found the number of awards for each company and the unique branches that are awarding each company.
- Year-wise analysis of the number of times a branch, or agency are awarding companies.
  
<img width="555" alt="Screen Shot 2024-03-13 at 9 43 08 AM" src="https://github.com/sagarikasardesai/SBIR-Investment-Scope/assets/21274244/7f17e3fd-2f4a-404a-a299-07068f74cc90">

<img width="927" alt="Screen Shot 2024-03-13 at 9 43 31 AM" src="https://github.com/sagarikasardesai/SBIR-Investment-Scope/assets/21274244/967612aa-28d6-45fc-8515-16f0b225829d">

#### Web Scraping for Recent News
From the results of the previous queries, the data related to SBIR companies that had the most number of awards was webscraped, to find some keywords using XPath and beautifulsoup.

### Insights

● As the years have progressed the SBIR Award Amount has increased. 
● The two companies who have benefitted the most are Physical Optics Corporation and CREARE LLC.
● The most used technologies by the companies over the years were Physics and Electricity, so we can invest in the small companies working on them, which can be seen in the SBIR data results.

