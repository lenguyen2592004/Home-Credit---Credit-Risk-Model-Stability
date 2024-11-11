# Home-Credit---Credit-Risk-Model-Stability
Link: https://www.kaggle.com/competitions/home-credit-credit-risk-model-stability
Overview
The goal of this competition is to predict which clients are more likely to default on their loans. The evaluation will favor solutions that are stable over time.

Your participation may offer consumer finance providers a more reliable and longer-lasting way to assess a potential client’s default risk.

Description
The absence of a credit history might mean a lot of things, including young age or a preference for cash. Without traditional data, someone with little to no credit history is likely to be denied. Consumer finance providers must accurately determine which clients can repay a loan and which cannot and data is key. If data science could help better predict one’s repayment capabilities, loans might become more accessible to those who may benefit from them the most.
Currently, consumer finance providers use various statistical and machine learning methods to predict loan risk. These models are generally called scorecards. In the real world, clients' behaviors change constantly, so every scorecard must be updated regularly, which takes time. The scorecard's stability in the future is critical, as a sudden drop in performance means that loans will be issued to worse clients on average. The core of the issue is that loan providers aren't able to spot potential problems any sooner than the first due dates of those loans are observable. Given the time it takes to redevelop, validate, and implement the scorecard, stability is highly desirable. There is a trade-off between the stability of the model and its performance, and a balance must be reached before deployment.
Founded in 1997, competition host Home Credit is an international consumer finance provider focusing on responsible lending primarily to people with little or no credit history. Home Credit broadens financial inclusion for the unbanked population by creating a positive and safe borrowing experience. We previously ran a competition with Kaggle that you can see here.
Your work in helping to assess potential clients' default risks will enable consumer finance providers to accept more loan applications. This may improve the lives of people who have historically been denied due to lack of credit history.

Evaluation
Submissions are evaluated using a gini stability metric. A gini score is calculated for predictions corresponding to each WEEK_NUM.

gini=2∗AUC−1

A linear regression, a⋅x+b
, is fit through the weekly gini scores, and a falling_rate is calculated as min(0,a)
. This is used to penalize models that drop off in predictive ability.

Finally, the variability of the predictions are calculated by taking the standard deviation of the residuals from the above linear regression, applying a penalty to model variablity.

The final metric is calculated as

stability metric=mean(gini)+88.0⋅min(0,a)−0.5⋅std(residuals)

Submission File
For each case_id in the test set, you must predict a probability for the target score. The file should contain a header and have the following format:

case_id,score
57543,0.1
57544,0.9
57545,0.5
etc.
