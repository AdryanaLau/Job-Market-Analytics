# Job-Market-Analytics

# Job Market Analytics

## Introduction

The Job Market Analytics project aims to gather valuable insights into active hiring trends in the analytics industry. Thousands of jobs are posted each day on platforms like Seek, yet this data remains largely inaccessible. This project seeks to bridge this gap by scraping job postings from Seek and presenting the data in a tabular format, providing benefits for both job seekers and the company.

## Tools Used

- **Python (Beautiful Soup):** Used for web scraping job postings from Seek.
- **Pandas:** Employed for data manipulation and transformation.
- **Power BI:** Utilised for visualisation, allowing the transformation of raw data into actionable insights.

## Architecture (ERD) 
<img width="412" alt="image" src="https://github.com/AdryanaLau/Job-Market-Analytics/assets/158017880/d2971e31-54ca-44fa-b51a-69c1fd0f9a25">

## Workflow

1. **Web Scraping:**
   - Utilized Python libraries such as BeautifulSoup for web scraping Seek job postings.
   - Explored alternatives like Scrapy and Selenium, highlighting their pros and cons.

2. **Data Transformation:**
   - Leveraged Pandas for data manipulation, extracting relevant information such as job titles, hiring companies, and posting dates.

3. **Visualisation:**
 <img width="452" alt="image" src="https://github.com/AdryanaLau/Job-Market-Analytics/assets/158017880/ad79e7d6-96a4-4253-8336-c08a6fad64e0">
 
 - The comprehensive visualisation presented above provides an overview of job postings categorised by companies, job titles, and posting dates. The dashboard showcases the aggregate number of job postings over the past 29 days, the average duration for postings across the SEEK Platform, and identifies the most prevalent job titles. Additionally, it delineates the job postings within the last 7 days and highlights the distribution of postings among various companies.

 - Through this visualisation, we gained insights into the high-demand job titles and the companies actively engaged in talent acquisition. Equipped with this data-driven intelligence, we can refine our strategies, prioritise job openings, and effectively match candidates with suitable opportunities. This, in turn, increases the company's efficacy in the realm of analytics recruitment.


## Challenges

- Handling dynamic web content and anti-scraping measures implemented by job search platforms.
- Ensuring data accuracy and integrity throughout the scraping and transformation processes.
- Optimising visualisation techniques to effectively communicate insights from the data.



