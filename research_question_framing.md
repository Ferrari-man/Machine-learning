# Project Lane

**Selected Lane:** Predictive Modeling / Binary Classification.


# The Core Research Question

Can we identify behavioral markers in a player's initial session metrics (match performance, win/loss ratios, session duration, and in-game progression friction) that correlate with an increased probability of early player churn (abandoning the game within 7 days)?*

## Unit of Analysis
**The Unit:** A single player's aggregated telemetry and performance data over their first 48 hours of account creation. Each row in the dataset represents one unique player profile.

## Decision, Output, and Actionable Outcome

-   **Model Output:** A calibrated probability score (0.0 to 1.0) indicating the likelihood that the player will abandon the game.
    
-   **The Decision:** Determining which players are experiencing extreme friction or frustration versus those who are naturally disengaging.
    
-   **The Action:** For players flagged with a high churn risk, the system dynamically adjusts the matchmaking queue algorithm to place them in a more balanced skill bracket, or triggers an automated in-game progression incentive (e.g., bonus resources or difficulty scaling adjustments) during their next login attempt.

## The Cost of a Wrong Recommendation (Risk Analysis)

-   **False Positives (Flagging a healthy player as churning):** The system may unnecessarily alter matchmaking or award unearned progression items to a highly engaged player. This risks degrading the competitive integrity of the game or inflating the in-game economy for players who would have stayed regardless.
    
-   **False Negatives (Missing a player who is actually about to quit):** The critical risk. Frustrated players receive no balancing intervention, leading to immediate player attrition and a direct loss in long-term player retention and potential lifetime value (LTV).

## Why This Problem Requires Machine Learning

This problem cannot be solved with a rigid, deterministic system like standard SQL queries or static `if/else` statements (e.g., `if losses > 3 then churn`). Player disengagement is multi-variable and non-linear. A player might tolerate a five-match losing streak if their individual performance metrics remain high, but they might quit after two matches if they experience extreme performance bottlenecks, long queue times, or highly imbalanced matchmaking.

A machine learning approach (such as a gradient-boosted decision tree framework) is necessary to capture complex feature interactions across hundreds of thousands of historical player profiles, adapting to subtle shifts in player behavior that human-authored rules would completely miss.
