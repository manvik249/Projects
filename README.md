# this indicate comments
#Pig Dice Game Using Python
import random
def roll():
    min_value=1
    max_value=6
    roll=random.randint(min_value,max_value)
    return roll
value=roll()
print(value)

while True:
    players=input("enter the number of players from 2 to 4: ")
    if players.isdigit():
        players=int(players)
        if 2<=players<=4:
            print("valid number of players")
            break
        else:
             print("invalid number of players")
    else:
        print("Invalid number, please try again")

max_score=10
player_score=[0 for a in range(players)]#put 0 for every single player

while max(player_score)<=max_score:
    for player_idx in range(players):
        print("\nplayer", player_idx +1, "turn has just started")
        print("your total score is: ", player_score[player_idx],"\n")
        current_score=0
        while True:
            should_roll=input("would you like to roll? (yes): ")
            if should_roll.lower()!="y":
                break
            value=roll()
            if value==1:
                print("you roller 1, turn done!")
                current_score=0
            else:
                current_score +=value
                print("you roller a", value)
            print("your score is:", current_score)
        player_score[player_idx]+= current_score
        print("your total score is:", player_score[player_idx])
    max_score=max(player_score)
    winning_idx=player_score.index(max(player_score))
    print("the winning player is:", player_score[winning_idx])
    print("player number", winning_idx +1, "is the winner with a score of:", max_score)
