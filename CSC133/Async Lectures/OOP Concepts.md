## What is Object Orienting Programming?
- A way of representing ideas separate entities and using them to solve problems
	- Think of it representing real world objects as code
	- Your computer doesn't know what a Car or a Person is
	- However, a Car has properties like:
		- Year
		- Color
		- Model
	- And it has actions it can perform:
		- drive
		- reverse
		- park
		- honk
## Single Responsibility Principle (SRP)
- You want to design your system so each module is responsible for the needs of just one function
	- Gather the things that change for the same reason
	- Separate things that change for a different reason
## Classes and Objects
- **Class**: A Blueprint on how to create a specific object
	- The object's variables (instance variables) explain the internal state of the object
	- The object's methods specify the actions of that object
## Objects
- Definition: An independent entity that contains both data (instance variables) and behavior (methods)
- Objects come in a lot of different forms
	- Some may describe problem-domain concepts
	- Others can coordinate the interaction between other objects
## The OOP "A Pie"
- Four distinct OOP concepts make "A Pie"
![[Pasted image 20240130202025.png]]
## Abstraction
- Definition: Only show the *necessary details* of an object
	- Hide the complexity
- Analogy:
	- A car is a complex machine with parts like an engine, tranny, brakes, etc
	- *We don't care how all these parts work*. Only that the foot on the pedal makes the car move
- Same thing with our *objects*
	- We hide unimportant data from the user
## Encapsulation
- Definition: Group data (attributes) and methods that operate on the data into a single unit known as a class
- Benefits:
	- *Protect* sensitive data and restrict access to it
	- *Controls* access into the object
	- Promotes data hiding
- **Access Modifiers**:
	- *Private, Public, Protected, and Default* are access modifiers in Java
- **Private Fields**:
	- Declaring fields as private ensures that they are not directly accessible from outside the class
- **Accessors**:
	- Methods that provide controlled access to private files
	- These methods are often called *getters* and *setters*
## Encapsulation Modifiers
![[Pasted image 20240130202720.png]]
## Unified Modeling Language (UML)
- General purpose modeling language in the field of software engineering
- A set of diagrams to visually represent the design and structure of a system
![[Pasted image 20240130202835.png]]
## UML - Class Diagrams
- **Class Diagrams**: Represent the static structure of a system
	- Including classes, attributes, methods, and relationships between classes
![[Pasted image 20240130202923.png]]
## 