



# **Introduction**

The purpose of this project is to illustrate the development and implementation of a Java program that simulates vehicles navigating through an intersection. The goal of this project, which is the second component of the course assessment, is to show that we may apply design patterns, thread-based programming, and agile development methods.

![Picture 1](https://github.com/Parthvi579/ASE_Traffic-Simulator-/assets/72267232/e455481f-2a3e-4e56-9894-e6f214196a44)



## Figure 1: - _Format of Traffic Simulation_

Figure 1 shows how we have interpreted the intersection and its various components. Intersection has 4 segments namely S1, S2, S3 and S4. Each segment has 2 phases, for instance Segment S2 has two phases, namely P3 and P8. We have considered that every segment has two lanes and will move together. As shown by arrows, vehicles in phase P8 will move to LEFT and vehicles in phase P3 will move either STRAIGHT or RIGHT. Within a segment, both phases can have different time, so light will remain Green for the phase with maximum time. For example, if P3 has a duration of 40 seconds and P8 has a duration of 30 seconds, the green light will be active in S2 for 40 seconds. During this time, vehicles in P8 will continue moving for 30 seconds, while vehicles in P3 will keep moving for the full 40 seconds. When time for green light is over for one segment, it will stay orange for 5 seconds and then green light will be on for next segment and vehicles in that segment will start to move. Once light is green for all four segments, one cycle will be completed.

# **Program Specification**

- At start-up, the application reads details of the intersection (Phase number and its duration) and details of existing vehicles.

- All added vehicles are in queues to cross the intersection, with one queue per phase. The vehicles are positioned at the end of the queue, at a certain distance from the intersection, and their positions are tracked.

- As shown in Screenshot 1, an ArrivalProcess.java thread class randomly generates vehicles and allocates them to Intersection which then assigns them to respective lane in segment. New vehicles are registered with their preceding vehicle. In our simulation we did not create separate classes for central controller instead Intersection.java is acting as a central controller as well.



##  _ArrivalProcess.java random vehicles creation after random time_

- vehicle position is being set according to the lastVehicle and length of the vehicle being added. Also, total waiting time for new added vehicle gets set according to the number of vehicles waiting in the lane, which is used to display Average waiting time for the vehicles which have crossed in the GUI.



##  _Intersection.java addNewVehicle() method_

- The traffic control cycle is continuously repeated, with each cycle consisting of a sequence of phases. Vehicles cross to their destination during each phase, with each segment having a specific time duration for vehicles in lanes to cross.

- We have considered Intersection.java as a traffic controller for traffic signal (red, orange, green) as per phase duration and did not implement separately any class for traffic signals.

- For each segment, there are two different phases that control the traffic flow. During each phase, only one vehicle can enter the intersection at a time. However, since there are two phases controlling the traffic in each segment, there can be two vehicles from different phases entering the intersection at the same time in each segment.

- The GUI is updated with changes that happen to the vehicles, including whether they crossed, they are still waiting, and their total waiting time.

- The total emission, average waiting time, and total waiting length are then updated and displayed.

- The simulation stops when the user pushes the exit button and generates a log file with records of events as they happen, such as a vehicle crossed, a vehicle was added, and a signal status changed.

To make sure that our application is effective, scalable, and maintainable, we used a structured software engineering approach, agile methodologies, threading, design patterns, suitable packaging, and version control techniques.

# **Software Engineering Requirements**

- We made the decision to use an agile technique when creating our application. We focused on the features that would be developed in each iteration of our development process as we planned our iterations. Without considering features in later iterations, we separately planned, designed, produced, and tested each iteration. We refactored our code at the conclusion of each iteration to make sure it was high-quality and prepared for the following one.

- We experimented with agile methods including pair programming, stand-up meetings, and time-boxing during the development process. Though we struggled a lot, these strategies improved our ability to work together efficiently, communicate properly, and keep our attention to the subject at hand. We consequently made the decision to include these methods in our development process.

- To make our application effective and scalable, we also used threads. Our program was created using a thread for each vehicle. We coordinated the flow of vehicles through the intersection using a shared resource as SharedObject.java class. We ensured that our threads were synchronized where necessary to avoid interference with one another.

- Our program was created using a number of design patterns, including the Singleton pattern for our log class and the MVC and observer patterns for our GUI. To properly organize our code and make it simple to maintain, we used packages. To keep track of changes and cooperate efficiently throughout the development process, we used version control.

- The last step was to export our application as a JAR file, which contains all required resources like text files. This makes it simple to run the program on any platform.  

**Details about how we developed our program using agile processes.**

Our team got a functional application quickly and effectively because to the agile methodology, which also made sure that the needs of the coursework are always kept in mind. Here are some ways in which our team have applied agile practices and techniques:

● **Iterative development:** Our team used an agile iterative approach to development, where we built the application in small, manageable increments rather than trying to create the entire application at once. Each iteration included a set of features assigned before moving on to the next iteration. However, we faced a challenge with bugs and errors in the code during the development process. For example, in the first iteration, we attempted to move existing vehicles that were in the queue for only one segment in the intersection, without generating random vehicles. In the next iteration, we improved this feature by adding random vehicles being generated by ArrivalProcess class. After that, we applied signal to each segment and tried to change the signal status. Finally, we created a shared object for the vehicle buffer for intersection processing and in the last GUI and Logging part was done.

By taking an iterative approach, we were able to implement, test, discard not working things and came up with the working code quickly.

- **Pair programming:** Our team used pair programming to improve code quality, reduce errors, and facilitate knowledge sharing. In pair programming, two developers work together at one computer, with one developer writing the code while the other reviews it, catches errors, and suggests improvements. In our application, we used pair programming to apply threading in the development process. We used MS Teams to collaborate on screenshare rather than meeting physically. One team member worked on the code for the threads in the Vehicle, Intersection, and SharedObject object, while the other verified the output generated by the thread code. However, one of the challenges we faced was that each team member had a different schedule, which made it difficult to work at the same time. We had to coordinate our schedules effectively to ensure that we could work together as much as possible, but we also had to be flexible and work independently when necessary.

- **Stand-up meetings:** Our team held weekly once or twice sometimes stand-up meetings to discuss progress, identify roadblocks, and plan the work. Stand-up meetings were short, usually lasting 15 minutes or less, and each team member answered three questions: What did I do yesterday? What am I doing today? Do I have any blockers? However, the differences in schedules for each team member posed a challenge when we tried to work at the same time. To overcome this challenge, we used Microsoft Teams to schedule online meetings primarily to discuss progress and address any issues or concerns.

Despite the scheduling challenge, our daily stand-up meetings were a valuable tool for keeping our team on track and ensuring that everyone was working towards our common goals.

- **Time-boxing:** Our team used time-boxing to ensure that work was completed within a specified time frame. Time-boxing involves setting a fixed amount of time (e.g., two weeks) to complete a set of features. At the end of the time box, the team reviews progress and adjusts the plan for the next time box. In our application, we divided the development process into multiple chunks to make it more manageable. For example, we set a deadline of 3 days for developing the feature that moves existing vehicles in the intersection, followed by 5 days for developing the segment signal and shared buffer object of the intersection. Next, we set another 5 days for generating random vehicles in the intersection and enabling vehicle notification by the preceding vehicle for traveling distance. In the final stages, we allocated 3 days for GUI update, 3 days for calculating total emission, average waiting time, and total waiting length of vehicles, and 2 days for log file generation. We kept the last 2 days for correcting any errors in the code.

Despite dividing our tasks evenly among team members, we initially faced some challenges in connecting each component of the project to ensure that they work in tandem with each other. This led to several bugs and errors during the development of the code, which sometimes caused delays in meeting our time-box deadlines. As a result, we had to update our time box based on our last execution of the progress to ensure that we could stay on track and complete the project successfully.

## An explanation of how and where threads are used in our application

Threads played a critical role in the development of this application, as it allowed for efficient and effective simulation of traffic flow and intersection management. Here is, an explanation of threads which are applied in our application:

**Controller thread:** We considered intersection as a central controller and implemented as a separate thread, allowing for efficient coordination and communication between different components of the simulation.

To manage the behavior of each waiting vehicle at the intersection, a new thread is created for each waiting vehicle. Each vehicle object implements the Runnable interface, which means that it has a run () method. This method manages the vehicle's movement through the intersection. In the intersection thread's run () method, calls to Thread. Sleep () are used to pause the execution of the thread for a specified period of time. This allows the waiting vehicles to move through the intersection and the signal to change. Therefore, by using threads, the code was able to simulate the behavior of waiting vehicles at an intersection, with each waiting vehicle being managed by a separate thread and the intersection thread using Thread. Sleep() to control the timing of the signal changes.

**Vehicle threads:** thread is used to simulate the arrival of vehicles at the intersection by generating random vehicle parameters and adding them to the Intersection object at random intervals. In our code, a new thread is created by implementing the Runnable interface in the ArrivalProcess class. The run () method contains an infinite loop that generates a random number and sleeps the thread for that amount of time. This is done using the Thread.sleep() method. After sleeping, the thread generates random vehicle parameters and adds them to the Intersection object using the addNewVehicle() method. The thread is started by creating a new Thread object and passing an instance of ArrivalProcess as the Runnable. The start () method is then called on the Thread object, which begins the thread's execution.

**GUI threads:** In Stage1, we used TableModel, DefaultTableModel and we implemented GUI in the end. We faced the issue of table being updated with new vehicles being added by ArrivalProcess.java and we were short of time, so we implemented normal GUI using StaffList example from the lectures. TrafficGUI.java class for GUI implements Runnable but there is nothing much happening in run () method.

**An explanation of how and where design patterns are used in our application.**

**Packages:** We used packages in our application as it helps to organize the code and make it more maintainable by grouping related classes together in a logical manner. We have used Model, View, Controller, LoggerPackage and Main packages to organize classes, Screenshot 3.

**Design Patterns:**

**Singleton pattern** used in MyLogger.java class ensures that only one instance of the class can exist at a time, Screenshot 4. This pattern is used to guarantee that all log entries are written to the same file and avoid any potential conflicts that could arise from multiple instances trying to write to the same file at the same time. By using this pattern, we were able to ensure that our log entries were consistent and accurate.

**The Model-View-Controller (MVC) pattern** is used in the application. This pattern separates the concerns of data, presentation, and user interaction, making it easier to develop and maintain the code. The Model represents the Intersection class, Vehicle, ArrivalProcess class with threading and other associated classes, the View represents the GUITraffic class code, and the Controller represents the SimulationController class.

**The observer pattern** is also used in the GUITraffic.java to notify the View when there are changes in the Model (Intersection.java that implements Subject interface). Intersection.java implements Subject interface and GUITraffic.java implements observer interface and attached itself as an observer to Interface class.

**Simulation** – We have run the simulation by creating some vehicles by reading vehicles.csv and then ArrivalProcess.java creates 100 vehicles randomly after every few seconds randomly. Two screenshots attached, first one when the simulation began and the next one when simulation ends.

![SC8](https://github.com/Parthvi579/ASE_Traffic-Simulator-/assets/72267232/6ab8d886-5f96-4a65-9606-befd997e0dad)
