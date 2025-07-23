# Music Recommendation System – Kaggle Competition

This repository contains a solution to a Kaggle-style music recommendation competition, where the objective was to predict user preferences by labeling track recommendations with binary ratings:  
- `1` for the **Top 3** most relevant tracks  
- `0` for the **Bottom 3** least relevant tracks  

Our solution earned **2nd place out of 12 participating teams**, showcasing a strong approach built on clean logic, iterative refinement, and intelligent rule-based scoring.

## Overview

The project is implemented in the Jupyter notebook `AAI_627HW_9.ipynb`. The goal is to identify the most and least relevant tracks for each user in a given test set and generate a submission file in the expected format.

## Methods Used

The code explored multiple scoring strategies for ranking tracks. Below is a summary of the methods implemented and tested:

### 1. **Frequency-Based Scoring**
Tracks that appeared more frequently across users were given higher scores. This method assumed popularity might reflect relevance.

### 2. **Artist & Genre Frequency**
Scores were computed using the frequency of artists and genres associated with each track, attempting to generalize preferences from a user’s past listening history.

### 3. **User-Specific Historical Patterns**
For each user, their interaction history was used to build a profile of preferred artists, genres, or specific tracks. Tracks were scored higher if they matched these patterns.

### 4. **Hybrid Weighted Scoring (Final Method)**
The final and best-performing method combined multiple heuristics:
- Track popularity
- Artist overlap
- Genre similarity
- User-specific history frequency

Each feature was assigned a weight, and a combined score was computed per track. This blended approach allowed the model to balance global popularity with personalized relevance.

## Why the Final Method Worked Best

The **final code block at the bottom of the notebook** implemented a weighted scoring system that accounted for both global trends and individual user preferences. This hybrid method performed the best because:
- It avoided overfitting to popularity alone.
- It better captured personalized interests by leveraging user history.
- It ensured diversity by not recommending only the most common tracks.

By aggregating multiple signals into a single relevance score, and ranking accordingly, this method consistently identified the most likely top and bottom tracks for each user — ultimately producing the most competitive submission.

## Code Breakdown

- **Data Loading**  
  Reads the test file (`test2_new.txt`) containing user-track pairs.

- **Preprocessing**  
  Groups the data by `user_id` and processes candidate tracks per user.

- **Scoring Logic**  
  Several scoring strategies were implemented. The final scoring method uses a hybrid of popularity, artist match, genre match, and personalized weighting.

- **Ranking and Labeling**  
  For each user:
  - The top 3 scored tracks are labeled as `1`.
  - The bottom 3 are labeled as `0`.

- **Submission Generation**  
  The output is written to a CSV file with the required format: `user_id, track_id, rating`.

## File Structure

- `AAI_627HW_9.ipynb`: Main notebook containing the entire pipeline.
- `test2_new.txt`: Input file with user and candidate track data.
- `submission.csv`: Final output file suitable for Kaggle submission.


