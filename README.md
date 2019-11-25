# us-electoral-college-balancer
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/davidd8/us-electoral-college-balancer/master?urlpath=%2Fapps%2FElectoral-College-Balancer.ipynb)

A proof of concept IPython Notebook that runs linear optimizations for gerryneutering. The concept of Gerryneutering is described in detail at [David Ex Machina](https://www.davidexmachina.com/2019/11/gerry-neutering.html) and works as follows to neutralize gerrymandering and partisan redistricting:

1. Run a relocation program that pays a person 3 months of rent and moving costs to move to a swing state after proof of registering to vote in that state before the 2020 election. (Most states require 30d before becoming a resident, and voter registration can take up to 30d, plus 30d of buffer) 
2. Market the program to Democrats from blue strongholds (i.e. CA and NY). Potential slogans include: "move to save your country" or "bring economic growth to the midwest" and "make your vote count"
3. Let them vote!

The linear optimizations run using data from the 2016 Federal Election Results as well as the 2018 HUD report for Fair Market Rents, to solve for a (1) minimum budget to win the Electoral College and (2) a maximum number of Electoral College votes for a given budget. Both solvers output the budget spend, Electoral college result, and the set of states that flip.

## Assumptions and Caveats
- This is a historical optimization. The plurality delta for political demographics is based on the 2016 election and is not guaranteed to be the same in 2020. An improvement to the model would account for population shifts across the country as well as political sentiment, but that’s what [538](https://fivethirtyeight.com) and polls are for!

- The relocation costs assume to cover 3 months of rent for a 1 bedroom plus $2500 for movers and $250 one-way ticket to the city in question. 3 months was selected, as most states require 30d to establish residency and register to vote, so 3 months is a nice cushion. One could play around with the notebook to see how the costs would differ for different size rental units. A future improvement would link state residency requirements to match the relocation costs.

- Rental costs are also historical, and not predictive. It should also be mentioned that a large demand for housing in a state can change the housing market and potentially increase rental costs, especially if there’s not enough supply for housing.

- The optimizations solve for the minimum number of people, i.e. it leaves no room for error. If one were to implement this plan, one should add a buffer to the budget to increase confidence in a win. For example, if voters are 90% likely to vote, then the program should spend at least 10% more than the model suggests to lock in a win.

- The model does not account for states that have ranked choice or proportional electoral college votes, it counts them as a binary choice instead: blue pill or the red pill. Namely this is why Maine shows up as a flipped state in most model runs, though it is already a Democratic stronghold.

- The model does not tell you what states to target for outflow potential (i.e. people willing to leave “safe” states for “swing” states), but a simple implementation targeting blue strongholds like CA would probably go pretty far.
