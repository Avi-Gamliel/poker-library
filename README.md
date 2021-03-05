# What is this? 

Texas Holdem Poker Library

# Installation

`npm i texas-holdem-library --save`

then...

` import {Round, Deck, Players, Player, solve, rank} from 'texas-holdem-library' `

# Create Players

```

const players = new Players();
players.createPlayer('name', '', 1000, 0,'', '')
players.sitPlayer('name', 1000, 1)
players.standPlayer('name')

```

* *createPlayer* - This method create a new player - *(name, hand, cash, chair,id,check)*
* *sitPlayer* - This method sit the player in chair - *(name, cash, chair)*
* *standPlayer* - This method stand the player from his chair - *(name)*


# Create Deck 

```

 const deck = new Deck();
 deck.createDeck();
 deck.shuffleDeck();


```

* *createDeck* - This method create a new deck
* *shuffleDeck* - This method shuffle the deck

# Create Cards for table and players

```

const round = new Round();
round.addPlayers(players.players);
round.dealCards(deck);
round.Flop(deck);
round.Turn(deck);
round.River(deck);


```

* *addPlayers* - This method add players to the round - notice that the players is the players that we create up above.
* *dealCards* - This method create a two cards for all the players - *make sure the you pass the deck you create.*

* *Flop* - This method create a 3 cards - *make sure the you pass the same deck*
* *Turn* - This method create a 1 card - *make sure the you pass the same deck*
* *River* - This method create a 1 card - *make sure the you pass the same deck*



# Optional for full Game or Round
 

```

const round = new Round();
round.addPlayers(players.players);
round.makeBigSmall(100, 50);
round.dealCards(deck);
round.SmallBig();
players.handleDealer();

round.updateStage('pre-flop');
round.activeBets();

if (round.bets) {
// make logic moves here
round.makeMove('name', 'raise', 200);
round.makeMove('name', 'call');
round.makeMove('name', 'fold');
round.makeMove('name', 'check');
}


round.Flop(deck);
round.updateStage('flop');
round.activeBets();

if (round.bets) {
// make logic moves here
}


round.Turn(deck);
round.updateStage('turn');
round.activeBets();

if (round.bets) {
// make logic moves here
}

round.River(deck)
round.updateStage('river');
round.activeBets();

// final

round.startGame(true)
const winner = round.checkWinner();
round.handleWinners(winner);
round.restartRound(players.players);


```

* *makeBigSmall* - This method create the big small to the game - *(Big, Small)*
* *SmallBig* - This method determines who is big and who is small.  ** the dealer is determined in players **
* *updateStage* - This method add the stage of the game - * 'pre-flop','flop','turn', 'river' *
* *activeBets* - This method active the bets so you can make your own logic.
* *makeMove* - This method make a move to the player - notice that only the raise need to pass with sum.


* *startGame* - This method get boolean that you can make your own logic
* *checkWinner* - This method check and return whte winner, *its return with side pot cash look into the round object*
* *handleWinners* - This method get the winner and handle with the cash for each player in this round.
* *restartRound* - This method restart the game. 








