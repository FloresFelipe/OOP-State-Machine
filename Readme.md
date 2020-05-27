## OOD LabVIEW State Machine

## State Design Pattern

I've gone really into Object-Oriented Design and Programming the last few years and learning the Gang o Four Design Patters is one my favorite subjects, since I believe they would put in a higher level whatever programming language I'm using.

>If you do not know about Gang of Four Design Patters, I recommend you to google __Design Patterns: Elements of Reusable Object-Oriented Software by Gang of Four__ and also dive into the articles of [Refactoring Guru](https:refactoring.guru) which I believe has the best explanation ever of Design Patterns. [This link](https://refactoring.guru/design-patterns/state) from Refactoring Guru describes how the state pattern works.

This project is my interpretation of the State Pattern by Gang of Four, implemented in LabVIEW. I wanted to translate the State Pattern UML Diagram into LabVIEW Code and as a result, implement an OOP State Machine. As a reference for me and other LabVIEW developers, the implemented example is analogue to the **Simple State Machine** LabVIEW Sample project.

![Simple SM](/Documentation/loc_simple_state_machine.png)

Here is the translation of it when I desined the example based on the State Design Pattern

![class diagram](/Documentation/StateDiagram.png)

One important aspect of this design pattern is that each state will be a class, inherited two methods form the **State.lvclass** abstract class:

* **doAction.vi:** performs core actions for the State
* **transition.vi:** performs the logic to decide which will be the next state in the context.

Specifically the Wait Event class implements a specific method called **Event UI.vi**, which is the Front Panel of the example. However, it is not called since the beginning of the code. The **doAction** of the Wait Event class launches the UI and waits for an response on the **transition.vi**. The method I used to synchronize the UI with the state machine code was a _Queue_. transition will wait until some event is triggered from the UI.

>There is probably a best way to do it. I'll work on it soon! I'm also not considering that the states will return data to the UI by wire.

Below you find an image of the Project LabVIEW Classes


![LabVIEW Classes](/Documentation/projectClasses.png)


## Next Steps
- [ ] Implementing default actions on the abstract methods such as error handling and execution logging. Those will be accessed by calling the **Call Parent Method** function.
- [ ] Queueing States
- [ ] Completely detach UI from the State Machine code so we can try different UIs in the future.


## Example Application

I built a project using this template. Check out the [Simon Game Project.](https://github.com/FloresFelipe/Simon)
