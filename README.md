# Blackjack Labyrinth game

This is my first big Python project which involves the Kivy library. Initially, I did not plan to escalate it to an Android application so the project has plenty of room for improvements, but at this point, I do not plan to refactoring the code.


GENERAL INFO

Kivy library allows the building of cross-platform GUI apps. I decided to create my app for Android, but it can be easily implemented for other platforms such as Windows, Linux, iOS, etc.
All the materials used in the app are free licenses and some are created by myself and my friends. The theme of the application is inspired by a popular RPG game POE.
Google Play AAB file was compiled with Buildozer.
It is a free game and can be downloaded from Google Play - https://play.google.com/store/apps/details?id=org.blackjacklabyrinth.blackjacklabyrinth
Game Overview - https://www.youtube.com/watch?v=Wlm3dmHkQcg


GAME CONCEPT

The game idea is for a 1v1 (player vs computer) Blackjack card game. The general rules of the blackjack game apply. Here comes the inspiration from the mentioned RPG game so I tweaked the rules. My goal was to create an unpredictable dynamic increasing difficulty card game.


GAME INFORMATION:

1. Win-loss-tie
  - Blackjack (if the sum of two cards is 21) beats non-Blackjack 21 and any other hand value.
  - Win: the player or the dealer wins if one of them owns a higher hand value on the check. If the player wins, he receives the bet amount multiplied by the profit percentage.
  - Loss: the player or the dealer loses if busts (hand value exceeds 21) or owns a lower hand value on the check. If the player loses, the bet is lost.
  - Tie: if the check of the player's and dealer's hand value is equal, it means a tie. Beware - only two Blackjacks can be equal! If there is a tie, the player's bet is returned.
2. Dynamic difficulty adjustment (DDA)
  - The difficulty of the game increases as the player's held credits increase. When the difficulty goes up the player's bonus for all in and the starting value of profit percentage is reduced, and the curse event chance increases at the same time. There are two levels of difficulties D1 and D2. When game difficulty increases, a label (D1 or D2) appears.
3.  Profit percentage
  - Each new turn the profit percentage starting value is 1.5 (modified by the DDA!), but it can be increased or reduced by events and cards. Beware - the profit percentage can be reduced below 1!
4. Special events
  - Hit a card: each new card drawn by the player adds 0.1 to the profit percentage.
  - All-In: if player's all-in, 0.5 (modified by the DDA!) is added to the profit percentage. 'AI' (all-in) label appears on the player's side.
  - The first two cards are Aces: the sum of the two Aces card values becomes 10 (for both the player and the dealer) to allow more flexibility. If owned by the player (Player's 2ACE), 0.3 is added to the profit percentage. If owned by the dealer (Dealer's 2ACE), 0.3 is subtracted from the profit percentage.
  - Curse and bless: each player wins has a chance to be cursed or blessed. Chance for both events is equal until the player goes up in the game difficulty (curse chance is modified by the DDA!). If cursed, the profit percentage reduces by 30%. If blessed, the profit percentage increases by 30%.
5. Special cards
  - Aces: instead of the classic choices, the player's options are 1, 6, and 11. This provides more flexibility at the cost of the credit. The cost is taken from the player's credit on each selection and is added to the bet. If the player's credits are 0 or less, each selection reduces the bet.
  - Black Joker: can be owned by the player or the dealer and its card value is 0. Once the card is drawn 'BJ' (Black Joker) label appears on the owner's side and it shows that uses the card benefit. If the impact is on the player's side, the player receives a percentage from the sum of credits and the bet as bonus credits. If the impact is on the dealer's side, 
    the player loses credits as a percentage from the sum of credits and the bet. The impact lasts until the card owner loses or the other side draws a black joker.
  - Red Joker: can be owned by the player or the dealer and its card value is 0. Once the card is drawn 'RJ' (Red Joker) label appears on the owner's side and it shows that uses the card benefit. If the trick is on the player's side and wins, 0.15 is added for each owned card to the profit percentage. If the trick is on the dealer's side and the player wins, he 
    loses 0.15 profit percentage for each owned card. The trick applies when the player wins a turn, then it disappears.
6. Game over & ranking
  - The game ends when the player loses all of the credits or reaches the last rank.
  - There are 7 ranks. At the end of the game, it will be displayed the player's highest rank and credits achieved.
