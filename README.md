# Probabilities & Statistics

# Question 1
### Andrew and Bob are playing a game. Bob's phone's battery is a positive integer 1-100, randomly distributed. Andrew will win if he guesses Bob's phone battery within a 5% margin of error. Additionally, Andrew is allowed to ask one yes-or-no question before guessing Bob's battery (i.e. Is your battery above 50%?). He is allowed one guess. Andrew and Bob both play optimally. What number should he ask above-or-below, and what is the following strategy for guessing the battery?

import random

wins = 0
trials = 0

for i in range(1000000):
    ind_var = 50

    battery = random.randint(1,100)
    if battery >= ind_var:
        guess = round(100/1.05,0)
        if abs(guess - battery) <= 0.05 * battery:
            wins += 1
        trials += 1
    
    if battery < ind_var:
        guess = round(ind_var / 1.05,0)
        if abs(guess - battery) <= 0.05 * battery:
            wins += 1
        trials += 1

percent = round(wins / trials * 100,3)

print(f"Win Percent: {percent}%")

# Answer:
#### Andrew will ask, "Is your battery above/below 88%/89%/90%/91% (any of the four)?" If Bob says his battery is above, Andrew will guess 96, which covers 9 solutions (92-100). If Bob says his battery is below, Andrew will guess 85, which covers 81-89 (9 solutions). Therefore, the maximum win percentage for Andrew is 18%. There are various different combinations that result in 18% here.  


# Question 2
### You start with zero points. You flip a coin maximum of ten times. If you get heads, you gain one point. If you get tails, you lose one point. What is the percent chance you reach 1 point within ten flips?

import random 

wins = 0
attempts = 1000000

for i in range(attempts):
    heads = 0
    for i in range(10):
        flip = random.randint(1,2)
        if flip == 1:
            heads+=1
            if heads == 1:
                wins += 1
                break
        elif flip == 2:
            heads -= 1
    
print(wins)
percent = wins / attempts
print(f"Win %: {percent} percent")

# Answer:
#### ~75.4% chance to win. This can be reframed mathematically. Let Sn be a simple random walk starting at S_0. This scenario is equivalent to P(max 1<=k<=10 Sk>=1). Using the Reflection principle to solve for the probability that the condition will not be fulfilled can be done as follows: P(never reach +1) = 
#### (10
#### 5)    / 2^10 = 1 - 252/1024 = 75.4%
