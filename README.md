# SkillPrediction

In games, we would often like to rate players' skill and be able to match opponents of approximately equal caliber. It is also closely related to predicting team strength or win probability in sports. We can use probabilistic models to try to capture these concepts quantitatively.

One example of a probability model for online team sports is Microsoft's TrueSkillLinks to an external site, which uses approximate inference to produce estimates and uncertainty that can be used to match teams or predict outcomes.

Typically, we model the skill of each player as a variable, and use the game outcomes along with a simple model relating the players' skill to their probability of winning the match.  For example, for a two-player game, we might define a Gaussian random variable for each player to represent their skill level, and estimate the probability of one player winning over another as a logistic function of the difference in their skills -- a simple Stan model implementing this idea is provided in the code. Alternatively, using pyGM we could model skill as a discrete variable and construct a table of win probabilities given the two players' skills.

We compared the ability of model to predict the winner of new (unseen) games to simple approaches, such as fraction of games won, number of games played, etc.

We tried to evaluate how many games are required to accurately predict the players' skill levels / win probability by decreasing the amount of training data available and observing the performance. Also we tried to evaluate how quickly we can determine a new players' skill by either random game choices or carefully chosen games (matched based on estimated skill level).

We experimented with learning a more complex model, for example taking into account game features (player's selected character, for example; or a bias for the player who goes first in a turn-based game) or additional latent scores (such as offensive and defensive skill) along with a correspondingly more elaborate probability of win function.
