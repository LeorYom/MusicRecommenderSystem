# Music Recommendation System – Kaggle Competition

This repository contains a solution to a Kaggle music recommendation competition. The objective is to predict user preferences by labeling track recommendations with binary ratings:  
- `1` for the **Top 3** most relevant tracks  
- `0` for the **Bottom 3** least relevant tracks  

## Overview

The code is implemented in a Jupyter notebook: `AAI_627HW_9.ipynb`. It processes a test dataset of user-track pairs and assigns binary relevance scores based on a simple scoring rule. The final output is formatted according to the competition's submission requirements.

## Code Breakdown

- **Data Loading**  
  The test set is read from `test2_new.txt`, which contains user IDs and associated track IDs to evaluate.

- **Preprocessing**  
  The data is grouped by user to identify all candidate tracks for each individual.

- **Scoring and Ranking**  
  A custom scoring function assigns numerical scores to each track for a user. Tracks are then sorted in descending order of score.

- **Label Assignment**  
  For each user:
  - The top 3 tracks (highest scores) are labeled with `1`
  - The bottom 3 tracks (lowest scores) are labeled with `0`
  All other tracks (if any) are not labeled or included in the submission.

- **Submission File Creation**  
  A DataFrame is built with `user_id`, `track_id`, and `rating` columns. This is exported as a `.csv` file for submission to the competition.

## File Structure

- `AAI_627HW_9.ipynb`: Main notebook containing the entire pipeline.
- `test2_new.txt`: Input file with user and candidate track data.
- Output file (e.g., `submission.csv`) is generated at the end of the notebook.
