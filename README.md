# Job-Market-Analytics

# Job Market Analytics

## Introduction

The Job Market Analytics project aims to gather valuable insights into active hiring trends in the analytics industry. Thousands of jobs are posted each day on platforms like Seek, yet this data remains largely inaccessible. This project seeks to bridge this gap by scraping job postings from Seek and presenting the data in a tabular format, providing benefits for both job seekers and the company.

## Tools Used

- **Python (Beautiful Soup):** Used for web scraping job postings from Seek.
- **Python (Pandas):** Employed for data manipulation and transformation.
- **Power BI:** Utilised for visualisation, allowing the transformation of raw data into actionable insights.

## Architecture (ERD) 
<img width="1000" alt="image" src="https://github.com/AdryanaLau/Job-Market-Analytics/assets/158017880/d2971e31-54ca-44fa-b51a-69c1fd0f9a25">

## Workflow

## 1. **Web Scraping:**
   - Utilised Python libraries such as BeautifulSoup for web scraping Seek job postings.
   
**Imports**:
   ```python
   import urllib.parse
   import requests
   from bs4 import BeautifulSoup
   import json
   ```
   - The script starts by importing necessary modules: `urllib.parse` for constructing URLs, `requests` for making HTTP requests, `BeautifulSoup` for web scraping, and `json` for handling JSON data.
     
**URL Construction Function**:
   ```python
   def construct_url(job_title, location):
       base_url = 'https://www.seek.com.au/'
       encoded_job_title = urllib.parse.quote(job_title)
       encoded_location = urllib.parse.quote(location)
       url = f'{base_url}{encoded_job_title}-jobs/in-All-{encoded_location}'
       return url
   ```
   - The `construct_url` function takes `job_title` and `location` as parameters, URL-encodes them, and constructs a Seek job search URL.
     
**Load Jobs Function**:
   ```python
   def load_jobs(url):
       try:
           page = requests.get(url)
           page.raise_for_status()  # Raise an HTTPError for bad responses
           soup = BeautifulSoup(page.content, "html.parser")
           job_soup = soup.find_all("div", class_='_1wkzzau0 a1msqi6m')
           return job_soup
       except requests.RequestException as e:
           print(f"Error loading page: {e}")
           return []
   ```
   - The `load_jobs` function takes a URL, makes a request to the website, checks for errors, and returns a list of job elements found on the page.
     
**Extract Job Information Function**:
   ```python
   def extract_job_info(job_elem):
       title_elem = job_elem.find('h3', class_='your-title-class')  # Replace with the correct class
       company_elem = job_elem.find('span', class_='your-company-class')  # Replace with the correct class
       title = title_elem.text.strip() if title_elem else "No Title"
       company = company_elem.text.strip() if company_elem else "No Company"
       return {'title': title, 'company': company}
   ```
   - The `extract_job_info` function takes a job element, extracts the title and company information, and returns a dictionary.

**Main Function**:
   ```python
   def main():
       job_title = 'data-analyst'
       location = 'Perth-WA'
       url = construct_url(job_title, location)
       jobs = load_jobs(url)
       job_info_list = [extract_job_info(job) for job in jobs]
       titles = [job['title'] for job in job_info_list]
       companies = [job['company'] for job in job_info_list]
       result_dict = {'titles': titles, 'companies': companies}
       with open('job_info.json', 'w') as json_file:
           json.dump(result_dict, json_file)
       print("Titles and companies extracted and saved to 'job_info.json'")
   ```
   - The `main` function sets the job title and location, constructs the URL, loads job elements, extracts job information, creates lists of titles and companies, creates a dictionary, and saves the data to a JSON file.

**Main Function Execution**:
   ```python
   if __name__ == "__main__":
       main()
   ```

## **Web Scraping Options:**

### Scrapy

#### Pros:
- Efficient for scraping large amounts of data.
- Robust architecture for handling complex scraping tasks.
- Built-in support for handling asynchronous requests.

#### Cons:
- Steeper learning curve compared to simpler libraries like Beautiful Soup.
- Requires understanding of XPath and CSS selectors.
- Limited JavaScript support compared to Selenium.

### Selenium

#### Pros:
- Excellent for scraping dynamic websites with heavy JavaScript usage.
- Provides a real browser environment, allowing interaction with JavaScript-rendered content.
- Supports multiple browsers, enabling cross-browser compatibility.

#### Cons:
- Slower compared to other scraping methods due to browser automation.
- Requires setup of browser drivers for different browsers.
- Regular maintenance required to adapt to changes in web page structures or browser updates.

### Beautiful Soup

#### Pros:
- Easy to use and beginner-friendly.
- Great for parsing HTML and XML documents.
- Large community and extensive documentation for support.

#### Cons:
- Limited support for advanced web scraping tasks compared to Scrapy and Selenium.
- May not be suitable for scraping dynamic web pages with heavy JavaScript usage.
- Changes in page structure may affect reliability, requiring updates and maintenance.

**Conclusion:**

After exploring these web scraping tools, Beautiful Soup emerged as the preferred choice for the Job Market Analytics project due to its simplicity and suitability for straightforward scraping tasks. However, the choice of a web scraping tool ultimately depends on the specific requirements and complexities of each project.



## 2. **Data Transformation:**
- Utilised Python libraries such as Pandas for data transformation.

<img width="1000" alt="image" src="https://github.com/AdryanaLau/Job-Market-Analytics/assets/158017880/5dfdaf9b-080a-44d7-90f7-dbff872770e9">



## 3. **Visualisation:**
 <img width="1000" alt="image" src="https://github.com/AdryanaLau/Job-Market-Analytics/assets/158017880/ad79e7d6-96a4-4253-8336-c08a6fad64e0">
 
 - The comprehensive visualisation presented above provides an overview of job postings categorised by companies, job titles, and posting dates. The dashboard showcases the aggregate number of job postings over the past 29 days, the average duration for postings across the SEEK Platform, and identifies the most prevalent job titles. Additionally, it delineates the job postings within the last 7 days and highlights the distribution of postings among various companies.

 - Through this visualisation, we gained insights into the high-demand job titles and the companies actively engaged in talent acquisition. Equipped with this data-driven intelligence, we can refine our strategies, prioritise job openings, and effectively match candidates with suitable opportunities. This, in turn, increases the company's efficacy in the realm of analytics recruitment.


## Challenges

- Handling dynamic web content and anti-scraping measures implemented by job search platforms.
- Ensuring data accuracy and integrity throughout the scraping and transformation processes.
- Optimising visualisation techniques to effectively communicate insights from the data.



