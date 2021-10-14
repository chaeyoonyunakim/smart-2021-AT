# smart-2021-AT_Answer_Type_Prediction
A system optimisation for the SeMantic AnsweR Type prediction task(SMART)

- Dataset: https://smart-task.github.io/2021/
- Evaluation script : https://github.com/smart-task/smart-dataset/blob/master/evaluation/dbpedia/evaluate.py

# Evaluation Results (Validation / Test)
|Version| Accuracy  | NDCG@5 | NDCG@10 | Accuracy  | NDCG@5 | NDCG@10 |
|:-----:| :-------: | :----: | :------:| :-------: | :----: | :------:|
|1      | 0.969     | 0.732  | 0.649   | 0.970     | 0.778  | 0.683   |
|2      | 0.973     | 0.735  | 0.656   | 0.981     | 0.839  | 0.739   |
|3      | 0.953     | 0.699  | 0.622   | 0.967     | 0.810  | 0.713   |
|4      | 0.973     | 0.737  | 0.658   | 0.984     | 0.836  | 0.737   |
|5      | 0.973     | 0.736  | 0.656   | 0.985     | 0.842  | 0.742   |
|6 `Best`| 0.973    | 0.736  | 0.738   | 0.984     | 0.842  | 0.854   |
</br>

***Configuration settings for submission versions***
|Version| Stopwords | Stemming | Lemma | Embedding | Iteration | Type |
|:-----:| :-------: | :-------:| :----:| :-------: | :-------: | :---:|
|1      | FALSE     | TRUE     | TRUE  | TF        | 100/10    | 5    |
|2      | FALSE     | TRUE     | TRUE  | TF        | 100/10    | 5    |
|3      | TRUE      | TRUE     | TRUE  | TF-IDF    | 100/10    | 5    |
|4      | FALSE     | TRUE     | FALSE | TF        | 200/20    | 5    |
|5      | FALSE     | TRUE     | FALSE | TF        | 200/10    | 5    |
|6 `Best`| FALSE    | TRUE     | FALSE | TF        | 200/10    | 10   |

- `Version 1`: The first submission was pushed as soon as we have test data on Oct 15, 2021. We trained the system using 80% of the original SMART 2021 training dataset and validated with the other 20% of the training dataset. Since we received the test results at the equivalent level with validation results, we could have been trusting the old experiments.
- `Version 2`: The second submission was made to confirm the effect of the additional data manipulation and cleaning process. Later this effect was integrated with the latest cleaner version of datasets.
- `Version 3`: The third version submission was to confirm how much the model performances will be depreciated if we apply the empirical negatives that couldn’t figure the causal theory. As a result, in comparison with the prior submissions, it dropped approximately 2% of every evaluation score and again we could confirm the correlation between validation scores and test scores. It included the stopwords' changes and TF-IDF embeddings which mean the system used Wh-terms question inputs in TF-IDF embeddings.
- `Version 4` and `5`: The fourth and fifth version submission was to check if our models had converged enough when they were trained. While the prior submissions used the default iteration 100 for the two LR models and 10 for the MLP model, this submission came out with doubled iterations in training. We’d thought the proportional relations between validation scores and test scores should be verified in a way of finding the feasible, best validation performance. As a result of the submission, we verified that all our training within the default iteration number is valid. </br>
From the third version to the fifth version, the contribution of performance gain is expected as the result of not applying lemma. The loss from the fifth to the fourth version is considered as the result of overfitting as explained to have a reverse trend on test results as opposite to the validation results.
- `Version 6`: The sixth version submission was the confirmation of our **best model**. The methods of modelling were same, but this trained the system with ten types of resource’s ontologies thereby the better performance in NDCG@10 was expected to output.
