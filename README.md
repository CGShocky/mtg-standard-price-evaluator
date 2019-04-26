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

I'll write the developpement of each steps as I go.

#1

This is somewhat of a challenge, since we need to transform each cards into data that can be used by the model. While an RNN approach with the text of each cards would be interesting, i'm more inclined to start by writing every cards as a vector of properties. Since cards varies wildly, there will be some loss of information involve but I think we can get an accurate representation anyway. The basics of a card are pretty straight foreward to represent, but when it gets to weird mechanics(let's say dredge), it's not clear how to go about doing this. We could have a 'dredge' boolean, but then we might miss the connection of these cards to other similar effects. Also, since dredge will never be printed again, our dredge flag will also always be 0. This push us to not only assert things as they really are, but also to interpret certain mechanics. A 'dredge' bit might not be useful for our model, but a 'graveyard recursion' bit would transfer pretty well.

We will determine categories as we go. I will post the results here when finish, probably an .xls file. For now i'll focus on modern legal cards, though we might go back more if results are not good. The danger of going back is to fall into a game that was different from now and get fuzzy data.
