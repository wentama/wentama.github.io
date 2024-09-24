---
layout: page
title: Reddit Moods
description: a system for subreddits sentiment analysis
img: assets/img/reddit_moods/background.png
importance: 3
category: development
---
This project involved developing a system to predict the sentiment of posts in user-specified subreddits, utilizing an end-to-end architecture built on AWS and a machine learning-based NLP pipeline.

__Skills & Tools invovled:__ Python, AWS, TypeScript, Deep Learning, Model Selection, Data Curation, Data Validation

Reddit Moods is a web-based application designed to predict the overall sentiment of posts in user-specified subreddits. Built with a scalable serverless architecture using AWS Lambda, API Gateway, and a React-powered frontend, the system processes the top 25 subreddit posts and analyze their sentiment (positive, neutral, or negative) through pre-trained NLP models. The solution is optimized for efficient deployment while offering real-time sentiment insights.

<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0 mx-auto">
    {% include figure.liquid loading="eager" path="assets/img/reddit_moods/homepage.png" title="mainpage image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 1. Main Page.
</div>

The frontend utilizes three tools: TypeScript, React, and Chakra UI. And the backend consists of two main components: AWS API Gateway and AWS Lambda. All of them work together to have our application deployed through AWS CloudFormation. Our group consists of 4 members and I primarily worked on the backend and data pipeline to:
- design data ingestion pipeline for tokenization, preprocessing, and analysis 
- curate validation datasets for model evaluation
- assess deep learning model performances

__Skills & Tools invovled:__ Python, AWS, TypeScript, Deep Learning, Model Selection, Data Curation, Data Validation

### System Architecture

<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0 mx-auto">
    {% include figure.liquid loading="eager" path="assets/img/reddit_moods/workflow.png" title="workflow chart image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 2. Workflow showing overview of the data engineering system.
</div>

The system starts with the user, who will access our frontend web application to input a subreddit of interest. Upon submitting, it trigger a request sent to the AWS API Gateway. This then provide a secure and scalable entry point to AWS Lambda, which performs the modeling on data returned from real-time Reddit API call and fetch results to send back to Gateway. The outputs will then be returned to the user on our frontend. 

### Web Application

<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0 mx-auto">
    {% include figure.liquid loading="eager" path="assets/img/reddit_moods/output.png" title="workflow chart image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 3. Output showing the sentiment and confidence score.
</div>

Upons submitting subreddit input via the `Get Subreddit Mood` button as shown in Fig 1. The sentiment value (positive, neutral, or negative) of the subreddit is returned to the user along with a confidence score. A breakdown of the analysis is also included beneath the overall sentiment, showing the top 25 headings that were ingested along with their sentiment. 

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0 mx-auto">
    {% include figure.liquid loading="eager" path="assets/img/reddit_moods/analysis_breakdown.png" title="workflow chart image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 4. A breakdown of top headings by sentiment.
</div>

