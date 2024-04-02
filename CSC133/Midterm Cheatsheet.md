# OOP Concepts
---
## Classes and Objects
- Blueprint for object
- Obj var's explain internal state of obj
- Obj methods specify action of obj

## The OOP Pie
![[Pasted image 20240309190051.png]]

### Abstraction
- Only show **necessary details** of object
![[Pasted image 20240309190210.png]]
### Encapsulation
- Attributes and methods that operate on the data into a single unit known as a class
- **Protects** sensitive data and restricts access to it
- **Controls** access into the object
- Promotes data hiding
- **Access Modifiers**
	- private, public, protected, and default are access modifiers
	- **Private** used for encapsulation
- **Private Fields**
	- Private fields not accessible outside the class. 
- **Accessors**
	- Methods that provide controlled access to *private* fields
	- Also known as *getters* and *setters*
![[Pasted image 20240309190606.png]]

### Inheritance
- Children classes can **inherit** parent classes functions/methods
- Allows for **method/constructor overriding** 
	- Can use `super()` to call constructor of the superclass (parent class)
- For encapsulation, we can use `protected` for our variables if you want to share the parent variables to the children and no one else.
- **Abstract Classes**
	- Classes which declare but don't define behavior
- **Abstract Methods**
	- Methods which don't contain implementations
![[Pasted image 20240309194322.png]]
![[Pasted image 20240309192657.png]]

### Polymorphism
- Types of Polymorphism
	- Compile-time (**Static**) Polymorphism
		- Method Overloading
	- Run-time (**Dynamic**) Polymorphism
		- Method Overriding
- Upcasting
	- Casting a child object to its parent type
	- Allows child obj to be treated as parent obj (generic)
	- ![[Pasted image 20240309204213.png]]
- Downcasting
	- Casting a parent object to its child type
	- Allows accessing child class-specific methods and properties 
	- ![[Pasted image 20240309204256.png]]
## Java Packages
- Used to group together classes belonging to the same category or providing similar functionality
## Associations
### Aggregation
- Represents "**has-a**" or "**is-part-of**"
![[Pasted image 20240309191555.png]]
### Composition
- **Exclusive** Ownership
	- Without whole, part can't exist
- **Required** Ownership
	- Without part, the whole can't exist
![[Pasted image 20240309191647.png]]

## UML
![[Pasted image 20240309191727.png]]

# Code Smells
---
## Martin Fowler's Smells
![[Pasted image 20240309195349.png]]

## More Code Smells
![[Pasted image 20240309200540.png]]

## Detection
- SAST Testing 
- Peer review

# Code Refactoring
---
## Refactoring
- Changing code to be cleaner
- We refactor to
	- Prevent design decay
	- simplify code
	- find bugs
	- better readability
	- code smells
- Refactor when changing existing code

![[Pasted image 20240309202140.png]]
![[Pasted image 20240309202201.png]]

![[Pasted image 20240309202206.png]]![[Pasted image 20240309202210.png]]

# Git
---
## Git Repo Files
![[Pasted image 20240309204622.png]]

## Setting up Global git 
- `git config --global user.name "Your Username"`
- `git config --global user.email "Your email"`

## Best Practices
- Use descriptive commit messages
	- What commit does
	- Why is was made
- Commit Small Chunks of Code
	- Small, logical units of work
- Regularly Pull
	- Pull or fetch from remote repo to be up-to-date and not cause merge conflicts