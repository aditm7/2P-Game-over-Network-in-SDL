# IIT Delhi Politics: A Two-Player Strategy Game
## Introduction
In the heart of IIT Delhi, where academia meets ambition, the battleground of college politics unfolds. Take on the role of a student vying for the ultimate honor: the Presidency. Navigate the maze of campus life, from rallying support to facing off in epic duels. Will you rise as a beacon of change or be swallowed by the tide of campus intrigue?

## Theme
The game immerses players in the political landscape of IIT Delhi, combining strategy, campus exploration, and competitive duels.
![Alt text](img/report0.png)
## Design Decisions
- **Animations**: Added animations everywhere to improve the user experience (UX).
- **Sound Effects**: Incorporated appropriate and interesting sound effects to enhance the gaming experience.
- **Networking**: Used socketing to handle game interactions between players over the shared network.
- **Game Mechanics**: The game design involves strategic thinking and includes a thrilling old-fashioned sword battle face-off against your rival.
- **Development**: Built everything from scratch using Pygame.

## Game Structure
### Two-Player Game
The game is designed for two players to compete against each other.

### Two Rounds
1. **First Round – Campaigning**: Players navigate the campus, completing tasks, and spreading propaganda. The score accumulated in this round determines the resources and abilities available in the next round.
2. **Second Round – Duel**: The finalists face off in a showdown, armed with swords obtained based on their first-round performance. They engage in a duel until one player emerges victorious.

## How to Play
1. **Install Code**: Download the game code from GitHub and install Pygame.
2. **Set Up**: Server intialising and then joining
- To run the server on localhost
```
./scripts/run_server.sh
```
- To run the server on the wifi network
```
./scripts/run_server.sh wifi
```
- This will print the ip address of the server. Now we need to join the game at this ip address.

- Now to join the game Run the following command to join the game mentioning the ip address of the server and the alias of the player.
```
./scripts/run_game.sh ip_address alias_of_the_player
```
3. **Round 1**: Start playing Round 1, interact with entities, and complete tasks to build your candidature profile for the presidential elections.
4. **Wait**: After round 1 ends, wait for the other player to complete round 1.
5. **Final Showdown**: Play a final showdown with the other player to win the elections.
6. **Victory**: The last standing player wins!

## Round 1: Campaigning
Navigate IIT Delhi campus to complete campaigning tasks!
![Alt text](img/report1.png)
### Player Profile
![Alt text](img/report2.png)
- **Health**
- **Coins**
- **Score**
- **Instructions**
- **Timer**

1. Player moves to the next round if health goes to zero.
2. Round one ends if either player completes all tasks or the timer reaches zero.
3. Score is calculated using health, time left, and coins collected.

#### Health Recharge
- **Hospital (Press h)**: Recharges health to full at the cost of 40 points.
<img src="img/report3.png" alt="Alt text" width="75" height="50">

- **Outlets (Press f)**: Increases health by 20 at the cost of 10 points.
<img src="img/report4.png" alt="Alt text" width="75" height="50">
<img src="img/report5.png" alt="Alt text" width="75" height="50">


#### Dogs and Coins
- **Dogs**: NPCs that reduce player health by 5 units upon collision.
<img src="img/report7.png" alt="Alt text" width="75" height="50">

- **Coins**: Each coin is worth 50 points.
<img src="img/report6.png" alt="Alt text" width="75" height="50">

#### Yulu Riding
- **Press y**: Get on Yulu.
<img src="img/report8.png" alt="Alt text" width="75" height="50">

- **Bill**: Accumulates over time.
<img src="img/report10.png" alt="Alt text" width="75" height="50">

- **Press t**: Get off Yulu.
<img src="img/report11.png" alt="Alt text" width="75" height="50">

### Tasks
<img src="img/report12.png" alt="Alt text" width="400" height="25">
<img src="img/report13.png" alt="Alt text" width="400" height="25">
<img src="img/report14.png" alt="Alt text" width="400" height="25">
<img src="img/report15.png" alt="Alt text" width="500" height="25">
<img src="img/report16.png" alt="Alt text" width="500" height="25">
<img src="img/report17.png" alt="Alt text" width="500" height="25">
<img src="img/report18.png" alt="Alt text" width="400" height="25">
<img src="img/report19.png" alt="Alt text" width="500" height="25">


- **Fixed Time**: The round runs for a fixed time in which the player must complete as many tasks as possible.
- **Task Completion**: Each completed task earns points. After completing all tasks, the player moves to round two.
- **Score Calculation**: The sooner the player finishes all tasks, the higher the final score.

### Player Speed
- **Road**: Speed = 6, energy decreases at the fastest rate. 
<img src="img/report21.png" alt="Alt text" width="75" height="50">

- **Grass**: Speed = 2, energy decreases at a rate slower than the road.
<img src="img/report20.png" alt="Alt text" width="75" height="50">

- **Yulu**: Speed = 4, energy decreases at a fixed rate.
<img src="img/report22.png" alt="Alt text" width="75" height="50">

### Round 1 Results
The game keeps pinging the server to check the status of the second player.
![Alt text](img/report23.png)

## Round 2: Duel
- A duel between you and your competitor begins as soon as both players complete round one.
![Alt text](img/report25.png)

- **Better Sword**: Higher scores in round one result in better swords for the duel.

### Client-Server Architecture
- **Server**: Stores the profile data of both players.
- **Data Handling**: Overwrites the received profile data and sends the profile data of the opposite player. Prevents race conditions by ensuring one thread only reads and the other thread only writes to the location.
![Alt text](img/report26.png)

### Controls
- **Attack 1 (Key C)**: Light Attack (Lower cooldown).
<img src="img/report28.png" alt="Alt text" width="50" height="50">

- **Attack 2 (Key Z)**: Heavy Attack (Higher cooldown).
<img src="img/report29.png" alt="Alt text" width="50" height="50">

- **Defense (Key X)**: Block (Has cooldown, so you can’t block permanently).
<img src="img/report27.png" alt="Alt text" width="50" height="50">

Use arrow keys for the controls **Jump**, **Run Right** , **Run Left**

<img src="img/report30.png" alt="Alt text" width="200" height="100">

## Round 2 Results
- The final results of the duel determine the winner.
![Alt text](img/report31.png)