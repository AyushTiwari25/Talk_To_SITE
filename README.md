# 🕸️ Welcome to the **Web Scraping Project**! 

This project is designed to showcase the capabilities of web scraping using **Python** and the **Scrapy** framework, focusing on extracting business details from [Yellow Pages Australia](https://www.yellowpages.com.au). The extracted data includes key company information, which can be leveraged for research, analysis, and more.

---

## 📋 Table of Contents
1. [Project Overview](#project-overview)
2. [Features](#features)
3. [Prerequisites](#prerequisites)
4. [Installation](#installation)
5. [Usage Instructions](#usage-instructions)
6. [Scrapy Code](#scrapy-code)
7. [Sample Output](#sample-output)
8. [Contact](#contact)

---

## 📖 Project Overview
This project automates the data extraction process for businesses listed on Yellow Pages Australia. Using **Scrapy**, a fast and efficient web scraping framework, the project collects:
- Business Name
- Phone Number
- Address

The output is stored in a structured format (JSON/CSV) for easy analysis and access.

---

## ✨ Features
- **Automated Data Collection**: Quickly scrape large datasets from Yellow Pages.
- **Targeted Queries**: Easily customize the search criteria to extract specific types of businesses or locations.
- **Export Options**: Save extracted data in formats such as JSON or CSV for further analysis.

---

## 🔧 Prerequisites

- **Python**: Ensure that Python 3.6 or later is installed on your system.
- **Scrapy**: This project relies on Scrapy for efficient data scraping.

---

## ⚙️ Installation

Follow these steps to set up and run the project on your local machine:

1. **Clone this repository**:
   ```bash
   git clone https://github.com/your-username/Hack2Skill_Web_Scrapping_Task.git
   ```

2. **Navigate to the project directory**:
   ```bash
   cd Hack2Skill_Web_Scrapping_Task
   ```

3. **Install required libraries**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Verify Installation**: Run the following command to confirm Scrapy is installed and working:
   ```bash
   scrapy
   ```

---

## 🚀 Usage Instructions

### Running the Scrapy Spider

1. **Execute the spider**:
   Run the following command to start the scraping process:
   ```bash
   scrapy crawl yellow_pages -o output.json
   ```
   This command runs the `yellow_pages` spider and saves the output to `output.json`.

2. **Customizing Search Terms**:
   - Edit the `start_urls` parameter within the spider file to specify a different business category, location, or any other criteria.
   - Example: Change the URL to retrieve data for "restaurants" instead of "plumbers."

3. **Data Output**:
   - By default, data is saved in JSON format, but you can specify a different format (e.g., CSV) by changing the output file extension:
   ```bash
   scrapy crawl yellow_pages -o output.csv
   ```

---

## 🧩 Scrapy Code

Here’s a detailed example of the Scrapy spider code. Feel free to copy and customize this code for your needs:

```python
import scrapy

class YellowPagesSpider(scrapy.Spider):
    name = "yellow_pages"
    # Starting URL: Update this with your preferred search term
    start_urls = [
        'https://www.yellowpages.com.au/search/listings?clue=plumber'
    ]

    def parse(self, response):
        for business in response.css('div.listing'):
            yield {
                'name': business.css('a.business-name::text').get(),
                'phone': business.css('span.contact-phone::text').get(),
                'address': business.css('span.contact-address::text').get(),
            }

```

> **💡 Note**: To adjust the scraping target, modify the `start_urls` with a specific category or location, like `'https://www.yellowpages.com.au/search/listings?clue=restaurant&location=Sydney'`.

---

## 📊 Sample Output

Here's an example of the data you can expect:

```json
[
    {
        "name": "John's Plumbing Services",
        "phone": "(02) 1234 5678",
        "address": "123 Main St, Sydney NSW 2000"
    },
    {
        "name": "Rapid Repairs",
        "phone": "(02) 8765 4321",
        "address": "456 Side Rd, Melbourne VIC 3000"
    }
]
```

The JSON file provides structured data, ready for analysis or integration into a larger system.

---

## 📞 Contact

If you have any questions, issues, or suggestions, please feel free to reach out:
- **Email**: 1017ayushtiwari@gmail.com

--- 
