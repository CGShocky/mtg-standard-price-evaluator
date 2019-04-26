# mtg-standard-price-evaluator

The goal of the project is to use the 25+ years of mtg card price to estimate the expected return of buying new upcoming cards.

While a lot of approach might be used to accomplish this task, V1 is going to be a simple MLP to which we will feed card data collected manually , :( , on mtggoldfish.com . 

While an approach that would predict the maximum price a card would take in it' standard life might be useful, it presents challenge since absolute prices varies wildly in the history of magic (introduction of mythic card, shorter/longer print runs, increase/decrease in player base, inflation, etc). 

For that reason, the model will try to estimate the % change in a card price rather than the absolute cost. We will also simplify the task be giving a set buy date for the cards, so the model doesn't have to predict the optimal buy time.

The steps involve in the creation of the models will be:

1. Data collection
2. Making the model and make it training ready
3. Optimization
4. (If results are subpar) Different architectures exploration


