wn - they need your help! 

Every year the team tracks the jolly man as he makes his way across the world delivering presents on Dec 24th. 
We’ve enlisted 8 friends from across the globe to provide updates, and our 1 view app will show his progress.

Getting Started

To begin this lab, create a new JavaFX project named according to the lab guidelines, and create the following:

Main.java - in the application package
MainController.java - in the application.controller package
Main.fxml - in the application.view package
Person.java - in the application.model package
PersonTask.java - in the application.model package
App Design

Your program will show a view similar to the one shown in attached file AppView1.png when the app is run. 
This view displays a label with images on it, a map of the Earth, a key listing friend names with color icons, and a date/timestamp of the last update. 
This view will be Main.fxml and it will be the only view in the app.



Colored dots will indicate the location of a friend (Person) on the map.

If a user clicks on the colored dot on the map, information should be populated about the selected Person
- see AppView1-example1.png for an example. 
The white arrow in this image indicates that the user click occurred on the navy dot on the map (the white arrow represents the mouse, 
it is not a GUI component). If the user clicks another person, the data should be updated to show that person’s information instead.



Once Santa has delivered presents to a friend, we will change their color icon to black, both in the map and in the key listing below
- see AppView1-example2.png for an example where Nicole and Jane have been updated. 
At this time, clicking on their icons should show their activity as “asleep” - see AppView1-example.png for an example.



Finally, our app will update every 10 seconds, in order to reflect changes as Santa moves between locations. 
A timestamp at the bottom of the view will show when it was last updated, 
and the colored icons/dots on the map will change color if a person has been updated.

Making it Work



Main.java will launch the application and show Main.fxml.

MainController.java will be the EventHandler for this fxml.

MainController will start a PersonTask on another thread in your app.



The Model

The model of this application include Person.java and PersonTask.java.



A Person has a name, a current activity, a color code, and a latitude & longitude location. 

The color code defines the color of their dot on the map (as well as the corresponding key below the map).

The latitude and longitude are positive integer values corresponding to the x and y coordinates on the map image.



Note that the Persons listed will not change - the labels at the bottom of the view can be hard-coded if necessary, 
as we will not add or remove any from the app. 
The provided data.csv contains their information, formatted as:

name,color,latitude,longitude



For each person’s current activity before Santa has visited them, randomly select from the activities.txt file provided. 
Note that this is a txt file and not a csv - reading it will be different! Each line denotes 1 activity. 
Once Santa has visited, their activity should be “asleep”.

Threads



PersonTask.java will be responsible for handling the app updates every 10 seconds. 

At this interval:

The date/timestamp at the bottom of the app should be updated. 
There is a chance that Santa has visited the next person on his list.
Randomly decide if the next person has been visited, using a random number generator.
If someone has been visited, update their color icons on the map and in the key to black. Otherwise, no map updates are required.
Clear any information shown about a person the user clicked on (see example in AppView2.png).


While it might be possible to implement this app without the use of threads, it does not make for a good user experience. 
To get started, create the basic functionality of the full app - add the new view, controller, and model class. 
Ensure your app shows the map image, and investigate showing the other GUI components required. 
Once that is complete, start to consider threads and tasks in JavaFX.



Your submission must leverage threads to color the location dots, at minimum. 
It is recommended an additional thread is used to help keep time.

Hints & Help:

JavaFX provides a javafx.scene.shape.Circle class which might be helpful if you aim to draw the circles onto the world map.



For any “random” events, investigate random number generation in Java - you may use the java.util.Random class:

https://docs.oracle.com/javase/8/docs/api/java/util/Random.html 



While debugging and testing your code, you might find that updating every 5 seconds (or even 1 second!) is useful. 
Be sure to set this to 10 before submitting your lab though!

Rubric:

(25pts) Correctness - app functions as described. Your submission will be tested by running the app and assessing the output.
(10pts) MVC - app is implemented as described, and therefore adheres to the MVC design pattern.
(30pts) PersonTask
(15pts) Person
(10pts) UML Diagram (includes fxml)
(10pts) Comments - Javadoc comments on all classes (does not include fxml)
(-50pts) Threads - any submission which does not leverage threads to accomplish the tasks of this lab will be reduced 50 points.
