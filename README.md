# Business Understanding

Our MLB team wishes to improve upon our prior season's record in order to increase our chances of making a deep postseason run and winning the World Series next season. Our offensive production was a weakness during the prior season. We would like to use OPS to evaluate and predict the offensive production of MLB hitters. OPS combines on-base skills (OBP or on-base percentage) with power hitting skills (slugging percentage), to measure overall offensive performace. We will use this information to help build our roster for next season (evaluate our current under-contract players and possible trade acquisitions, as well as free agents). Targeting hitters with a high OPS this offseason will help our team score more runs, win more games, perform better in the postseason, win a championship, and improve fan sentiment, driving revenue and profits in the process.

# Data Understanding

Our dataset is part of the Lahman Baseball database and obtained from Kaggle, compiled by author and journalist Sean Lahman. It contains complete baseball statistics and data dating from 1871 to 2024. We will use one of many tables, the "batting" table, for our purposes of evaluating and predicting offensive production.

## Data Preparation

We dropped some irrelevant columns and dealt with null values.  We filtered to focus in on the mdoern baseball era since we want to make recommendations for current players.  Finally, we filtered for qualified hitters with a minimum of 125 at-bats to avoid basing our conclusions on the smallest sample sizes.

# Exploratory Data Analysis

We calculated OPS and and defined our target, OPS_next and looked at feature correlation.

Several offensive stats correlate with OPS, but age has an outsize impact.

<img width="720" height="576" alt="correlation" src="https://github.com/user-attachments/assets/fbf634f6-eeb9-4267-9549-4089bd75ae58" />



OPS peaks around age 28-30.

<img width="720" height="432" alt="agingcurve" src="https://github.com/user-attachments/assets/3fd4fafd-7867-4573-ace1-ea033d7f0cdd" />


# Modeling and Evaluation

We created some lag features to improve our model performance.  Lag features help better predict OPS as it exhibits strong year-to-year correlation and can improve our modeling. Lag features are an important technique in time-series fofrecasting modeling and are especially useful in predicting player performace in sport analytics.

We created a baseline Linear Regression model and then an XGBoost, and the tuned XGBoost performed best with a 0.068 mean absolute error.

The top 5 players with the highest predicted OPS in 2025 are Aaron Judge, Shohei Ohtani, Yordan Alvarez, Juan Soto, and Kyle Tucker.

<img width="864" height="576" alt="top 5 players" src="https://github.com/user-attachments/assets/eada1160-7d52-455e-8b13-fccf16fef19a" />

# Conclusion

1) OPS is somewhat correlated with other offensive stats like RBI and runs, but the most glaring relationship is the inverse relationship with age.
2) OPS peaks around age 28-30 and declines thereafter.
3) Aaron Judge, Shohei Ohtani, Yordan Alvarez, Juan Soto and Kyle Tucker have are the top 5 players with the highest predicted OPS.

## Limitations

The Lahman Baseball Database contains player salary information, but it does not contain player contract details. Acquiring the best players will typically involve a long, multi-year commitment. Those details and the total contract implications for the team might factor heavily into the decision to acquire a player, so adding that information to the data would be helpful.

## Recommendations

1) Consider the totality of offensive stats when making decisions to persue a player, but know that age has an outsize impact on OPS.
2) Since OPS peaks around age 28-30, bear this in mind when offering or acquiring long player contracts.
3) We should prioritize acquiring Aaron Judge, Shohei Ohtani, Yordan Alvarez, Juan Soto, and/or Kyle Tucker when possible. In reality, of these top 5, only Kyle Tucker is a free agent this offseason. He should be our top offseason priority, since the others in the top 5 are locked into long-term contracts with their respective teams and would require an absolute haul to trade for in the unlikely event that a trade is even on the table.

## Next Steps

1) Find a way to work player contract data into our calculations so that can factor into our recommendations. We may know these players contract situations off-hand as baseball nerds, but not everyone does.
2) We can work player salary data into the mix now since the Lahman Baseball Database contains salary information. Even though it will not take into acocunt the long-term affect on the team and its finances moving forward, it can give is an idea of ROI on a year-to-year basis.
