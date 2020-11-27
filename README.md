# Tower_of_Hanoi_2D

Platform: Unity

Files present: 2
1. Game Executable.rar : Contains .exe version of game
2. Project Folder.rar  : Contains Project Folder named "ToH2D" which can be opened in Unity

Main Features:
-2D Drag and Drop Game with 3 Towers and 5 disks
-I have implemented a Snapping Feature which makes sure that the Disks will snap to the appropriate tower if they are released. 
-This Feature makes sure that the disks do not fall in a random position on the screen when released.
-The Snap feature was implemented by using the geometric positions of the towers.
-The player has full control over the drag feature once they have removed the disk from its respective tower and are making their next decision.
-The Project has been designed to follow all of the rules stated by the problem:
    Only Topmost Disk of Each Stack is Draggable
    A larger disk cannot be placed on a smaller one
    The Player wins when they have replicated the entire stack on one of the 2 other towers
-If the player makes an invalid move, a prompt appears on screen which can be closed by a button and the move made is reversed.


Additional Features:
-A move counter and a game timer have been implemented and displayed on screen, both of which update in real time.
-Move counter is only updated when a change on the board is detected.
-For eg. if a disk is picked up from tower 1 and then placed back at tower 1 then this will not count as a move.
-The timer uses an elapsedTime variable incremented by deltaTime in each frame rather than using absolute Time so that features like 
 Pause/Resume/Restart game clock can be implemented.

UI
-Restart Button on the top right hand corner puts all the pieces back to their initial position, resets the move counter and resets the game timer.
-Undo Button rolls back to the previous turn's state
-This is achieved by making a copy of the previous state before updating to the next state
-The undo button is only limited to one previous move at a time after which it will be disabled until another valid move is made by the player.
-In short the player cannot trace back to their nth previous move (n>1)
-Quit Button closes the application.


Drag n Drop:
-When a dragable Object is clicked, its centre should not snap to the cursor's position as it feels robotic.
-Instead the distance between the Object's centre point and the cursor should be near constant to make the drag feature feel like a free hand experience.
   
   Problem:-
    whenDragged: currentObjectPostion = currentCursorPosition 
    ( makes the object's centre snap to the cursor's position )

   Solution:-
        Record the initial position of the object and then adding the amount the cursor has moved.
    currentObjectPosition = initialObjectPosition + cursorDisplacement 
    ( where cursorDisplacement = initialCursorPosition - currentCursorPosition )

-This results in a more natural feeling drag and drop which is an essential part of the project. 


Other Minor Problems faced:
-An unknown challenge was to only make one of the objects dragable at a time.
-Since multiple objects could be on top across the 3 piles, there were cases where if one object was being dragged and the cursor would hover over
 another object, the second object would also be picked up which was undesirable.
-To overcome this a mutex named dragLock had to be introduced which would make sure that if 1 object is being dragged, all the other objects were 
 locked and could not be picked up.
 
 
Regards:

-This was my first Unity project and I want to thank Inspirit since I had a lot of fun and got to learn a lot from this experience.
-This is also my first time writing a README so I apologize in advance for any mistakes.
