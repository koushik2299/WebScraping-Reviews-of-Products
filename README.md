# Project Report: Web Scraping and AWS Deployment for Customer Reviews

## Introduction

This report documents the process and outcomes of a project involving web scraping customer reviews for different products, storing the data in a MongoDB database using Flask, and deploying the Flask application on Amazon AWS using CodePipeline and Elastic Beanstalk.

## Project Overview

### Objectives

The primary objectives of this project were:

1. Collect customer reviews for various products from the web.
2. Store the scraped data in a MongoDB database.
3. Develop a Flask web application to display the collected reviews.
4. Deploy the Flask application on Amazon AWS for public access.

### Tools and Technologies Used

- Web Scraping: Beautiful Soup
- Backend Framework: Flask
- Database: MongoDB
- Deployment: Amazon AWS, CodePipeline, Elastic Beanstalk

## Project Details

### Web Scraping with Beautiful Soup

To collect customer reviews, I utilized Beautiful Soup, a Python library for web scraping. Beautiful Soup allowed us to parse the HTML structure of web pages and extract the desired customer reviews for multiple products. For example:

```python
# Sample Beautiful Soup code for scraping customer reviews
from bs4 import BeautifulSoup
import requests

url = "https://www.amazon.com/s?k=tv"
response = requests.get(url)
soup = BeautifulSoup(response.content, 'html.parser')
```

# Extract review elements
reviews = soup.find_all('div', class_='review')


**Data Storage in MongoDB**

The scraped customer reviews were stored in a MongoDB database. MongoDB is a NoSQL database that is well-suited for storing unstructured or semi-structured data. We created a database to hold the reviews, and for each product, a collection was created to store individual reviews.

**Flask Web Application**

A Flask web application was developed to serve as the frontend for users to access and view the collected reviews. Users could interact with the application by selecting a specific product or category of products, and the corresponding reviews would be displayed.

Here's an example of a Flask route to display reviews:

```python
@app.route('/product/<product_id>')
def product_reviews(product_id):
    # Retrieve reviews from MongoDB based on the product_id
    reviews = mongo.db.product_reviews.find({"product_id": product_id})
    return render_template('product_reviews.html', reviews=reviews)
```
**AWS Deployment**

The Flask application was deployed on Amazon AWS for public access. This deployment was achieved using Amazon Elastic Beanstalk, a Platform-as-a-Service (PaaS) offering that simplified the deployment process. Additionally, an AWS CodePipeline was set up to automate the build and deployment of the application.

**Conclusion**

This project successfully achieved its objectives of web scraping customer reviews, storing the data in a MongoDB database, developing a Flask web application, and deploying it on Amazon AWS. The deployed application provides users with access to customer reviews of various products.

The combination of Beautiful Soup for web scraping, Flask for the web application, MongoDB for data storage, and AWS for deployment proved to be an effective and efficient solution for this project.

**Future Improvements**

In the future, the project could be enhanced with the following features:

1. Implement user authentication for certain functionalities.
2. Add data visualization to provide insights from the reviews.
3. Use NLP to get a Review Score.

