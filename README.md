# SWENG_Group_27
Interactive Real Time Mixed Reality Application for HoloLens 2 

## Group members
| Name            | GitHub username |
|-----------------|-----------------|
| Cian Moriarty   | moriarci        |
| Dan Preda       | DanPreda90      |
| Darius Pop      | Dezu17          |
| Hannah Foley    | hannahfoley-1   |
| Ivan Puig       | ipuig           |
| Peter Rolfe     | pjhrolfe        |
| Steven Bondaruk | bondarus        |
| Steve Thomas    | stevethomas13   |
| Zehao Yu        | Zehao00         |

## CHIPSZ
Our application is an interactive real-time game utilising augmented reality technology. When the game starts, moving 
targets are constantly generated in front of the player. Players can fire projectiles to hit targets to earn points. 
The player can fire three types of projectiles: earth projectiles, fire projectiles and water projectiles. Different 
projectiles have different physical properties and launching conditions. When the countdown of the game reaches 0, the 
game ends and the player's stats are displayed on the finish screen.

## CHIPSZClassLibrary

### Projectiles
There are three type of projectile : earth projectile, fire projectile and water projectile. All three types of projectiles 
are made with shaders and they have different physics properties. Different projectiles have different launching conditions:

- earth projectile --> 'press the right mouse button' or 'grip right hand'
- fire projectile --> 'press the "F" key on the keyboard' or 'the speed of movement reaches a certain threshold when the hand is not clenched'
- water projectile --> 'press the "F" key on the keyboard' or 'the speed of movement reaches a certain threshold when the hand is not clenched'
(press the 'M' key on the keyboard to switch between fire projectile and water projectile)

To reduce the overhead associated with projectile creation and destruction, we use pooling. When the player launches the 
game, the game creates a pool of pre-allocated objects for each type of projectile. When the player is about to fire a 
projectile, a projectile object is taken from the corresponding pool.

### Targets
When the game starts, moving targets are constantly generated in front of the player. Targets move on a sin wave. When the 
projectile fired by the player hits the targets, the player will get a certain score. We also use pooling for targets. When 
the player launches the game, the game creates a pool of pre-allocated objects for targets. The target object is sequentially 
taken out from the pool over time.

### List timer
The List timer is used to show the remaining time of the game and end the game when the countdown reaches 0. At the beginning 
of the game, initialize the list timer to 90. Decrease the value of the list timer by one every second. When the value of the 
list timer becomes 0, the game ends.

### Score tracker
Score tracker is used to record the player's score. When the projectile launched by the player hits the target, the score tracker 
will increase by a certain value. 

### Audio
All the player's interactions with the game will be accompanied by audio. All audio is placed in the Sound folder under the Assets 
folder. There are different sound effects when the player clicks the button, when different types of projectiles are fired, and 
when they hit the target.

### Finish screen
When the game is over, the player will be shown a finish screen with various buttons. Clicking the 'Leave the game' button on the 
finish screen will directly exit the game. Clicking the 'Try again' button on the finish screen will restart the game. Clicking the 
'See game statistics' button on the finish screen will display the player's statistics.

## CHIPSZTest
In order to prevent mutual interference between the main project code and the test code, we created a new project for unit tests. The 
name of the Unit tests project is CHIPSZTest. We used the "Unit Test App (Universal Windows)" for our unit tests. We also make a 
"CHIPSZClassLibrary (Universal Windows)" project in our solution to hold the code that needs to be shared between the tests and the application.

## Continuous Integration
We have a functioning Continuous Integration check implemented on our GitHub repository. This was a very challenging task for the group. 

The CI includes installing the necessary software including .NEt and NuGet. Then the MSBuild is set up and the project is built. 

As we are working with UWP, we have had to implement our unit testing in a separate project. Below is a screenshot of the tests passing. 

We are currently figuring out a way to add the unit tests to our CI file. 

