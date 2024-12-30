# AI Wikipedia Dataset Curation Agent

## Overview

This project involves building an AI agent that can autonomously curate a diverse and important dataset of 5,000 Wikipedia pages. The goal is to maximize diversity based on lexical, semantic, and categorical diversity, while respecting constraints such as a limited number of API calls. The agent uses Wikipedia's API to retrieve relevant pages based on seed queries, intelligently explores further pages based on diversity metrics, and ensures that the dataset is both diverse and important.

## Key Features

- **Lexical Diversity**: The agent uses lexical diversity as one of its main metrics, which measures the variety of vocabulary in each document.
- **Semantic Diversity**: The agent calculates semantic diversity by analyzing the similarity between document embeddings, ensuring that the dataset contains distinct topics.
- **Categorical Diversity**: The agent measures the diversity of Wikipedia categories to ensure that the dataset covers a broad range of topics.
- **API Constraints**: The agent operates within the limits of 6,500 API calls for fetching pages and searching for new pages.
- **Legal Page Constraints**: The agent is restricted to retrieving only legal pages according to the Wikipedia legal pages list.

## How the Agent Works

1. **Seed Queries**: The agent starts by fetching pages from Wikipedia using a set of predefined seed queries. These seed queries cover a broad range of topics like "science", "history", "technology", "medicine", etc.
   
2. **Initial Exploration**: The agent retrieves pages from the Wikipedia API based on the seed queries and calculates lexical diversity for each page.

3. **Intelligent Exploration**: The agent uses the lexical diversity score to prioritize pages with higher diversity. It continues exploring new pages while making sure it doesn’t exceed 5,000 pages in its dataset.

4. **Relaxing the Diversity Threshold**: If no high-diversity pages are found, the agent relaxes the threshold to fetch more pages. The agent ensures that it always respects the diversity of its dataset.

5. **Page Fetching Constraints**: The agent ensures that no more than 6,500 requests are made to the Wikipedia API for both fetching pages and searching for new pages.

6. **Final Dataset**: After retrieving 5,000 pages, the agent saves the dataset and calculates a final diversity score.

## Metrics Used

1. **Lexical Diversity**: Measures the ratio of unique words to total words in the documents. Higher values indicate more diversity.
   
2. **Semantic Diversity**: Calculated using cosine similarity of document embeddings. Lower similarity means higher diversity.
   
3. **Categorical Diversity**: Measures the diversity of Wikipedia categories across the dataset. It evaluates the overlap and coverage of categories.

4. **WikiRank**: WikiRank scores are used to calculate the importance of the pages in the dataset. The final score is a combination of diversity and WikiRank scores.

## Evaluation Criteria

- **Diversity Score**: The diversity score is calculated by combining the three diversity metrics (lexical, semantic, and categorical) with specific weights.
- **WikiRank Score**: The average WikiRank score of all the pages in the dataset.
- **Final Score**: The final score is calculated as the sum of the Diversity Score and the WikiRank score, normalized.

## Installation

pip install wikipedia
pip install sentence_transformers

## Dependencies

wikipedia: The Python library used for interacting with the Wikipedia API.
sentence_transformers: Used to generate sentence embeddings for calculating semantic diversity.
nltk: Utilized for tokenization during lexical diversity calculation.
sklearn: For calculating cosine similarity and other metrics.

## Results
The agent successfully curates a dataset of Wikipedia pages while optimizing for diversity across multiple metrics. The final output includes the 5,000 pages in the dataset, their respective diversity scores, and the calculated WikiRank score.

Lexical Diversity: 0.019
Semantic Diversity: 0.894
Category Diversity: 0.915
Overall Diversity Score: 0.637

## Conclusion
This project demonstrates the power of automated decision-making in curating a diverse and high-quality dataset for training AI models. By carefully managing API usage and prioritizing diversity, the agent is able to create a balanced dataset that can be used for various machine learning applications.
