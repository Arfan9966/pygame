import random

class Player:
    def __init__(self, name, money):
        self.name = name
        self.money = money

class BetRoyaleGame:
    def __init__(self, players):
        self.players = players
        self.pot = 0

    def place_bets(self):
        print("Let's start betting!")
        for player in self.players:
            bet = int(input(f"{player.name}, enter your bet amount: $"))
            player.money -= bet
            self.pot += bet

    def reveal_winner(self):
        print("Revealing the winner...")
        winner = random.choice(self.players)
        winner.money += self.pot
        print(f"The winner is {winner.name}!")
        print(f"{winner.name} wins ${self.pot}!")

def main():
    num_players = int(input("Enter the number of players: "))
    players = []
    for i in range(num_players):
        name = input(f"Enter name for player {i+1}: ")
        money = int(input(f"Enter starting money for {name}: $"))
        player = Player(name, money)
        players.append(player)

    game = BetRoyaleGame(players)

    # First round of betting
    game.place_bets()

    # Second round of betting
    game.place_bets()

    # Third round of betting
    game.place_bets()

    # Reveal winner
    game.reveal_winner()

if __name__ == "__main__":
    main()
