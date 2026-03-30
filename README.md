<div align="center">

![UiPath](https://img.shields.io/badge/UiPath-Studio_Web-FA4616?style=for-the-badge&logo=uipath&logoColor=white)
![Google Gemini](https://img.shields.io/badge/Google_Gemini-AI-4285F4?style=for-the-badge&logo=google&logoColor=white)
![Regex](https://img.shields.io/badge/Regex-Data_Cleansing-007396?style=for-the-badge)
![LINQ](https://img.shields.io/badge/LINQ-Data_Filtering-512BD4?style=for-the-badge)

</div>

# 🤖 UiPath RSS Aggregator & AI Content Filter

This project is an automated Robotic Process Automation (RPA) workflow built entirely on **UiPath Studio Web**. It automatically aggregates content from various RSS feeds, sanitizes the data, evaluates the articles using **Google Gemini AI** based on specific user interests, and exports the filtered results directly into a Spreadsheet.

## 🚀 How It Works (Process Workflow)

1. **Data Extraction:** Sends an `HTTP Request` (GET) to target RSS XML URLs to fetch the latest feeds.
2. **XML Parsing:** Uses the `Deserialize XML` activity to convert raw data into structured variables (Title, pubDate, Link, Description).
3. **Data Cleansing (Regex):** Strips out unwanted HTML tags and formatting from the description text using Regular Expressions (`Regex.Replace(..., "<.*?>", "")`) to get plain text.
4. **AI Integration:** Converts the cleaned data into JSON format (`Serialize JSON`) and sends it to the **Google Generative Language API (Gemini 1.5)** via a POST request with a custom prompt.
5. **Data Merging & Filtering:** Parses the AI's JSON response (`Deserialize JSON`) and uses advanced **LINQ (Group Join)** queries to merge the AI's approval status with the original raw data.
6. **Reporting:** Writes only the AI-approved, highly relevant content into a Google Sheets / Excel file for easy reading.

## 🛠️ Built With
* **Platform:** UiPath Studio Web
* **Core Activities:** HTTP Request, Serialize/Deserialize JSON, Deserialize XML
* **Data Manipulation:** Regex (Regular Expressions), LINQ, Generate Data Table From Text (Custom Separator)
* **Artificial Intelligence:** Google Generative AI (Gemini)

---

## ⚙️ Setup and Installation

This project is packaged as a `.uis` file, designed to be easily imported directly into your UiPath Studio Web environment. 

Please follow these steps to set up the project:

1. **Import Project:** In the UiPath Studio Web dashboard, click the **"Create New"** button and select the **"Import"** option.
2. **Upload .uis File:** Select the downloaded **`.uis`** file (`rss_reader 1.uis`) from your local machine to upload and restore the entire automation workflow.
3. **Initialize Workflow:** After the import is successful, open the **`Main.xaml`** file to configure your Google Gemini API keys in the HTTP Request activity and authenticate your Spreadsheet connections.
---

## 📄 Documentation

For a detailed look into the process architecture, business rules, and technical specifications, please refer to the **`PDD_RSS_AI.pdf`** (Process Definition Document) included in this repository.
