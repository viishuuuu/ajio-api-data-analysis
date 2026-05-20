AJIO API Data Analysis Project
A Python-based web scraping and data analysis tool that collects product data from AJIO e-commerce platform and performs comprehensive analysis on pricing, trends, and product information.
📋 Table of Contents

Overview
Features
Requirements
Installation
Usage
Project Structure
Data Output
Contributing
License


🎯 Overview
This project scrapes real-time product data from AJIO (a popular Indian e-commerce platform) and performs data analysis to extract insights about:

Product pricing patterns
Category trends
Product availability
Customer ratings and reviews
Inventory status

Target Audience: Data Analysts, Researchers, E-commerce Professionals

✨ Features

🔍 Web Scraping - Extracts product information from AJIO website
📊 Data Analysis - Analyzes pricing trends, categories, and product performance
📈 Visualization - Generates charts and insights from collected data
🔄 Automated Collection - Schedule regular data scraping
💾 Data Export - Export results to CSV/Excel formats
🎯 Filtering - Search by category, price range, ratings


📦 Requirements
Before you begin, ensure you have the following installed:

Python 3.8 or higher
pip (Python package manager)

Required Libraries:
requests>=2.28.0
beautifulsoup4>=4.11.0
pandas>=1.5.0
apify-client>=2.5.0
lxml>=4.9.0

🚀 Installation
Step 1: Clone the Repository
bashgit clone https://github.com/viishuuuu/ajio-api-data-analysis.git
cd ajio-api-data-analysis
Step 2: Create a Virtual Environment (Recommended)
bashpython -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
Step 3: Install Dependencies
bashpip install -r requirements.txt
Step 4: Set Up API Token (if using Apify)
Create a .env file in the project root:
APIFY_API_TOKEN=your_token_here
⚠️ Never commit your .env file to GitHub!

💻 Usage
Basic Scraping
pythonfrom apify_client import ApifyClient

# Initialize the client
client = ApifyClient("your_api_token")

# Run the scraper
run = client.actor("Zy4Zaho5EFXPY62j5").call(run_input=run_input)

# Get results
results = client.dataset(run["defaultDatasetId"]).iterate_items()
Data Analysis
pythonimport pandas as pd

# Load scraped data
df = pd.read_csv('ajio_products.csv')

# Analyze pricing
print(df.groupby('category')['price'].mean())

# Filter by price range
affordable = df[df['price'] < 2000]

📁 Project Structure
ajio-api-data-analysis/
│
├── README.md                  # This file
├── requirements.txt           # Python dependencies
├── .env.example              # Environment variables template
├── .gitignore                # Git ignore file
│
├── scripts/
│   ├── scraper.py            # Main scraping script
│   ├── analyzer.py           # Data analysis script
│   └── visualizer.py         # Data visualization
│
├── data/
│   ├── raw/                  # Raw scraped data
│   └── processed/            # Cleaned data
│
├── notebooks/
│   └── analysis.ipynb        # Jupyter notebook analysis
│
└── output/
    ├── reports/              # Generated reports
    └── charts/               # Visualizations

📊 Data Output
The project generates the following outputs:

CSV Files - Product data in spreadsheet format
JSON Files - Structured data for further processing
Charts & Graphs - Visual analysis of trends
Summary Reports - Key insights and statistics

Sample Output Format:
csvproduct_id,name,price,category,rating,availability
12345,Blue Cotton Shirt,1299,Men's Fashion,4.5,In Stock
12346,Black Jeans,2499,Men's Fashion,4.2,In Stock

⚙️ Configuration
Edit the config.py file to customize:
python# Search parameters
SEARCH_QUERY = "shirt"
PRICE_MIN = 500
PRICE_MAX = 5000
CATEGORY = "Men's Fashion"

# Scraping settings
MAX_PAGES = 10
TIMEOUT = 30

🔒 Security Notes
⚠️ Important:

Never commit API tokens to GitHub
Use environment variables for sensitive data
Keep your .env file in .gitignore
Rotate tokens regularly


🤝 Contributing
Contributions are welcome! Here's how you can help:

Fork the repository
Create a feature branch (git checkout -b feature/improvement)
Make your changes
Commit your changes (git commit -m "Add new feature")
Push to the branch (git push origin feature/improvement)
Open a Pull Request


📝 License
This project is licensed under the MIT License - see the LICENSE file for details.

📧 Contact & Support

Author: Navya Kanwar (viishuuuu)
Email: navyakanwar393@gmail.com
GitHub: github.com/viishuuuu

For issues and questions, please open an Issue on GitHub.

🙏 Acknowledgments

AJIO for the e-commerce platform
Apify for web scraping tools
The open-source community for amazing libraries


Happy Analyzing! 📊✨
