import random

class Character:
    def __init__(self, name, health):
        self.name = name
        self.health = health

    def attack(self):
        return random.randint(5, 15)

def battle(player, opponent):
    print(f"A wild {opponent.name} appears!")

    while player.health > 0 and opponent.health > 0:
        print(f"\n{player.name}'s HP: {player.health}\t{opponent.name}'s HP: {opponent.health}")
        input("Press Enter to attack!")

        player_attack = player.attack()
        opponent_attack = opponent.attack()

        print(f"\n{player.name} attacks {opponent.name} for {player_attack} damage!")
        opponent.health -= player_attack

        if opponent.health <= 0:
            print(f"\nCongratulations! You defeated {opponent.name}!")
            break

        print(f"\n{opponent.name} counter-attacks for {opponent_attack} damage!")
        player.health -= opponent_attack

        if player.health <= 0:
            print(f"\nOh no! {opponent.name} defeated {player.name}. Game over.")
            break

if __name__ == "__main__":
    player_name = input("Enter your character's name: ")
    player = Character(player_name, 100)

    # You can customize the opponent by changing the name and health
    opponent = Character("Enemy", 50)

    print("\nGet ready for battle!\n")
    battle(player, opponent)
