<h1 align="center">Design Patterns in use</h1>

## What are Design Patterns?

The concept of design patterns in software engineering was popularized in the early 1990s by the famous book **["Design Patterns: Elements of Reusable Object-Oriented Software"](https://amzn.to/3SKaa9x)** by Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides, collectively known as the "Gang of Four" (GoF). However, the roots of design patterns go back further, drawing inspiration from the field of architecture.

Architect Christopher Alexander introduced the idea of patterns in architecture in his 1977 book **"A Pattern Language,"** where he described solutions to common design problems in urban planning and building architecture. Alexander's work emphasized that each pattern solves a specific problem and is part of a more extensive design system. This approach resonated with software developers facing similar challenges in software construction.

Seeing the potential of Alexander's concepts in software development, the GoF adapted and expanded these ideas to object-oriented programming. Their book **introduced 23 design patterns categorized into Creational, Structural, and Behavioral patterns**, providing a standardized approach to solving common software design issues.

In software development, design patterns serve a similar purpose—**they provide templated solutions to recurring problems**, ensuring that you don't have to reinvent the wheel each time you encounter a familiar issue.

> **Software design pattern** - A general, reusable solution to a commonly occurring problem within a given context in software design. It is a description or template for how to solve a problem that can be used in many different situations.

## Design Pattern Types

Design patterns can be separated into three main categories:

* **Creational Patterns** - Object creation

    - **Singleton Pattern**: Ensures a class has only one instance and provides a global point of access to it. This is particularly useful for managing resources like database connections.

    - **Factory Method Pattern**: Defines an interface for creating an object but lets subclasses alter the type of objects that will be created. It's ideal when you have a superclass with multiple subclasses and you need to create an instance of one of these subclasses based on some initialization parameters.

    - **Abstract Factory Pattern**: Offers an interface for creating families of related or dependent objects without specifying their concrete classes. This pattern shines when you need to ensure that the created objects can work together without necessarily knowing their exact types.

    - **Builder Pattern**: Separates the construction of a complex object from its representation, allowing the same construction process to create various representations. This pattern is excellent for when you need to create an object with many optional or required components.

    - **Prototype Pattern**: Creates new objects by copying an existing object, known as the prototype. This is particularly useful in scenarios where the cost of creating an object is heavier than copying an existing one.

* **Structural Patterns** - Object assembly

    - **Adapter Pattern** (also known as Wrapper): Allows incompatible interfaces to work together. It acts as a bridge between two incompatible interfaces, enabling them to communicate without changing their existing code. This pattern is perfect when you need to integrate new features or libraries without disrupting existing code.

    - **Composite Pattern**: Enables you to treat individual objects and compositions of objects uniformly. It's ideal for representing part-whole hierarchies where you want to ignore the difference between compositions of objects and individual objects.

    - **Proxy Pattern**: Provides a placeholder for another object to control access to it. This is useful for lazy loading, controlling access, or logging, acting as an intermediary between the client and the actual object to add an additional layer of processing.

    - **Flyweight Pattern**: Minimizes memory use by sharing as much data as possible with similar objects; it's a boon for efficiency when working with a large number of objects that have some shared state.

    - **Facade Pattern**: Offers a simplified interface to a complex system of classes, library, or framework. By providing a higher-level interface, it makes the subsystem easier to use, reducing complexity and promoting decoupling.

    - **Bridge Pattern**: Decouples an abstraction from its implementation so that the two can vary independently. It's particularly useful when you need to extend a class in several orthogonal (independent) dimensions.

    - **Decorator Pattern**: Allows behavior to be added to an individual object, either statically or dynamically, without affecting the behavior of other objects from the same class. This pattern provides a flexible alternative to subclassing for extending functionality.

* **Behavioral Patterns** - Object interactions

    - **Strategy Pattern**: Allows you to define a family of algorithms, encapsulate each one, and make them interchangeable. Strategy lets the algorithm vary independently from clients that use it. This pattern is perfect when you have multiple ways to accomplish a task, and you want to select the method at runtime.

    - **Observer Pattern**: Defines a dependency between objects so that when one object changes its state, all its dependents are notified and updated automatically. It's ideal for implementing distributed event handling systems, where the act of changing one object's state needs to be reflected in another.

    - **Command Pattern**: Turns a request into a stand-alone object that contains all information about the request. This transformation allows you to parameterize methods with different requests, delay or queue a request's execution, and support undoable operations. It's particularly useful for operations that must be executed in a variety of different scenarios.

    - **Iterator Pattern**: Provides a way to access the elements of an aggregate object sequentially without exposing its underlying representation. This pattern is useful for collections of objects to provide a standard way to traverse them and potentially access a selection of elements without exposing the internal structure.

    - **State Pattern**: Allows an object to alter its behavior when its internal state changes. The object will appear to change its class. This is beneficial when an object's behavior depends on its state, and it must be able to change its behavior at runtime depending on that state.

    - **Memento Pattern**: Without violating encapsulation, capture and externalize an object's internal state so that the object can be returned to this state later. This pattern is useful for implementing undo mechanisms or for saving and restoring the state of an object.

    - **Mediator Pattern**: Reduces chaos between interacting classes by encapsulating the way disparate sets of objects interact and communicate with each other. By doing so, it helps to prevent the "spaghetti code" scenario where multiple classes communicate directly and in a complex way.

    - **Chain of Responsibility Pattern**: Passes the request along a chain of handlers. Upon receiving a request, each handler decides either to process the request or to pass it to the next handler in the chain. It's particularly useful for processing multiple types of requests in a decentralized manner.

    - **Visitor Pattern**: Lets you define a new operation without changing the classes of the elements on which it operates. Ideal for scenarios where you need to perform operations across a group of objects with different classes.

    - **Interpreter Pattern**: Provides a way to evaluate language grammar or expression. This is useful in the development of tools and compilers for new programming languages or scripting languages.

    - **Template Method Pattern**: Defines the skeleton of an algorithm in the superclass but lets subclasses override specific steps of the algorithm without changing its structure. It's beneficial when there's a multi-step process requiring flexibility while maintaining the overall structure.

![Types of Design Patterns](assets/DesignPatterns.png)

## Don’t fall into the Design Patterns trap

You should be warned that you will probably fall into **the Design Patterns trap** when you first learn design patterns. This means you will try to squeeze a pattern in every solution, and your codebase will become over-engineering and unusable very soon.

But we want to make our codebase as simple as possible, so Design patterns are not the silver bullet for all problems. We should not try to put them into every problem we have because they are solutions to problems, not tools that should be used everywhere. **If you can implement a simple solution without using a design pattern, do it!**

![Design Patterns Trap](assets/DesignPatternsTrap.jpg)

Image credits (@flaviocopes on Twitter)

---

In the rest of the article, we will go through all the important Design Patterns. During many years of using these patterns, I noticed that some are used often, some rarely, and some are not. Here, I will present only those patterns you need daily. 

Every pattern has an **[implementation in C# language](src)**. 

![Implementation in C#](assets/Solution.png)

## Creational Design Patterns

![Creational Design Patterns](assets/Creational.png)

### Singleton pattern

**Usage**: Use when a single instance of a class is needed. Some examples are logging and database connections. 

**Real-world example**: Only one CEO leads the company, making decisions and representing the entire organization, like a singleton providing global access and control.

**Remark about usage**: The Singleton pattern is regarded as **an anti-pattern**; hence, using them excessively is advised. Why? Using it, we tend to make procedural code with global variables.

![Singleton](assets/Singleton.png)

**[An implementation of the Singleton pattern in C#.](src/Singleton)**

> An important note about the Singleton pattern is that it poses a **significant issue for multithreading**, especially in a scenario where multiple threads may simultaneously attempt to create an instance of the Singleton class. This can lead to multiple instances if proper synchronization is not enforced, thus violating the core principle of the Singleton pattern that only one instance of the class should ever exist. There are multiple solutions to this problem, such as eager initialization, double-checked locking, or lazy initialization.

### Factory method pattern

**Usage**: Decouple object creation from usage. For example, you create different types of database connections based on configuration.

**Real-world example**: Think of a pizza joint with a "Pizza Factory" instead of chefs. Customers order "cheese" or "pepperoni," not knowing how it's made. Based on the order, this factory tells specialized "CheesePizza" or "PepperoniPizza" builders to get cookin'. Each builder adds signature toppings, keeping the creation logic separate but the ordering process smooth.

![Factory Method](assets/FactoryMethod.png)

**[An implementation of the Factory Method pattern in C#.](src/FactoryMethod)**

### Builder pattern

**Usage**: Constructing complex objects step by step. For example, if you need to create a complex domain object.

**Real-world example**: If we hire an architect to design our dream home, we don't need to know every construction detail. We need to tell the architect our preferences (number of rooms, style, materials), and they create a blueprint with those specifications. The architect acts as the "builder pattern," guiding us through the creation process with clear steps (foundation, walls, roof), ensuring correct order, and handling complex details. You make choices (fireplace or no fireplace?), and the builder incorporates them, constructing the house piece by piece until it's complete. 

![Builder](assets/Builder.png)

**[An implementation of the Builder pattern in C#.](src/Builder)**

Other exciting design patterns from this group are:

* **Abstract Factory**: Create families of related objects. For example, I build parsers for different file formats (e.g., JSON, XML, CSV). Check the **[implementation in C#](src/AbstractFactory)**.

* **Prototype**: Creating duplicate objects and reusing cached objects to reduce database calls. Check the **[implementation in C#](src/Prototype)**.

## Structural Design Patterns

![Structural Design Patterns](assets/Structural.png)

### Adapter pattern

**Usage**: Make incompatible interfaces compatible. For example, it integrates a new logging library into an existing system that expects a different interface.

**Real-world example**: Allows you to use your devices in different countries by adapting to the local power outlet (adapter mediates communication between incompatible systems).

![Adapter](assets/Adapter.png)

**[An implementation of the Adapter pattern in C#.](src/Adapter)**

### Composite pattern

**Usage**: Represent part-whole hierarchies. For example, graphic objects in a drawing application can be grouped and treated uniformly.

**Real-world example**: In the library, books are organized on shelves, but each shelf can further hold categories (fiction, history). These categories might even contain subcategories (romance, mystery). Each shelf acts as a composite, keeping both individual books (leaf nodes) and other categories (composite nodes).

![Composite](assets/Composite.png)

**[An implementation of the Composite pattern in C#.](src/Composite)**

### Proxy pattern

**Usage**: Control access to objects. For example, lazy loading of a high-resolution image in a web application.

**Real-world example**: Let’s assume you’re a CEO with a personal assistant who acts as a "proxy," handling requests and shielding you from unnecessary distractions. The assistant assesses each request, prioritizing the important ones, filtering out spam, and preparing relevant info. Only the filtered essentials reach the CEO, who focuses on big decisions, while the assistant handles the rest. 

![Proxy](assets/Proxy.png)

**[An implementation of the Proxy pattern in C#.](src/Proxy)**

### Decorator pattern

**Usage**: Dynamically add/remove behavior. For example, we are implementing compression or encryption on top of file streams.

**Real-world example**: If we want to make a coffee, we would start with plain coffee (the core object). Then, "decorate" it with cream (adds richness), sugar (sweetness), and cinnamon (extra flavor), each a "decorator" enhancing the base coffee without altering it. You can even combine them (multiple decorators) for unique creations like a creamy, sweet cinnamon latte!

![Decorator](assets/Decorator.png)

**[An implementation of the Decorator pattern in C#.](src/Decorator)**

> Another interesting design pattern from this group is the **Bridge pattern**. It is used to decouple abstraction from implementation. For example, I am separating platform-specific code from core logic. Check the [implementation in C#](src/Bridge).

## Behavioral Design Patterns

![Behavioral Design Patterns](assets/Behavioral.png)

### Strategy pattern

**Usage**: Define a family of algorithms. For example, they allow users to choose different sorting or compression algorithms.

**Real-world example**: Let’s plan a travel from city A to city B. You can choose a "transportation strategy" based on your needs: take a fast train (speed focus), a comfortable bus (comfort focus), or a budget-friendly carpool (low-cost focus). 

![Strategy](assets/Strategy.png)

**[An implementation of the Strategy pattern in C#.](src/Strategy)**

### Observer pattern

**Usage**: Maintain a consistent state by being notified of changes and, for example, notifying subscribers of events in a messaging system.

**Real-world example**: We can think of a breaking news app. Users subscribe to specific topics (sports, politics, etc.), acting as "observers." When news breaks in a subscribed topic, the "observer pattern" notifies all relevant users with personalized alerts. Sports fans get their scores, and political enthusiasts receive election updates without them needing to check actively. 

![Observer](assets/Observer.png)

**[An implementation of the Observer pattern in C#.](src/Observer)**

### Command pattern

**Usage**: Encapsulate a request as an object. For example, I implement undo/redo functionality in text or image editor.

**Real-world example**: Picture ordering food at a restaurant. You tell the waiter your wishes (pizza, extra cheese), creating an "order command." The waiter then acts as a messenger, carrying your "command" to the Chef in the kitchen (receiver). The Chef, receiving the "command," makes your pizza precisely as specified. This separation of ordering (command) from making (execution) lets you change or cancel easily.

![Command](assets/Command.png)

**[An implementation of the Command pattern in C#.](src/Command)**

### State pattern

**Usage**: Encapsulate state-specific behavior. For example, we are handling different states of a user interface element (e.g., enabled, disabled, selected).

**Real-world example**: The smartphone effortlessly transitions between states (on, off, silent, airplane mode) based on your actions. Each state (the "concrete state") has unique behavior: on allows calls and notifications, silent mutes them, and airplane mode blocks signals. The phone (the "context") doesn't manage these behaviors directly; it delegates to the current state object. When you press a button or toggle a setting, the phone transitions to a new state, seamlessly changing its behavior without requiring intricate logic. 

![State](assets/State.png)

**[An implementation of the State pattern in C#.](src/State)**

### Template method pattern

**Usage**: Define the skeleton of an algorithm in operation, deferring some steps to subclasses and implementing a base class for unit testing with customizable setup and teardown steps.

**Real-world example**: Let’s say we have a factory where every car (subclasses like Sedan, SUV, and Truck) follows the same basic steps: weld the frame, add the engine, install electrical components, and paint. This is the overall structure defined by the template method. However, each car type has specific variations: Sedans have smaller frames and engines, SUVs have higher clearance and different interiors, and trucks have reinforced frames and more significant engines. The template method ensures a smooth, organized process, allowing each car type to have unique characteristics through specific implementations within the overall flow.

![Template Method](assets/TemplateMethod.png)

**[An implementation of the Template Method pattern in C#.](src/TemplateMethod)**

## How to select the right design pattern

Choosing the correct design pattern in software engineering is critical to practical problem-solving. This guide simplifies the process, helping you decide between patterns based on specific needs. It offers concise descriptions and valuable use cases for each pattern, making understanding and applying them in real-world scenarios easier. 

To select a pattern, we must first go through the problem identification, as shown in the image below.

![Select Pattern](assets/SelectPattern.png)

> Design patterns are not the only kind of patterns we have. To learn more about other types of patterns, [check here](https://newsletter.techworld-with-milan.com/i/125894632/architecture-styles-patterns-and-design-patterns).

## BONUS: Design Patterns Cheat Sheet

![Design Patterns Cheat Sheet](assets/DesignPatternsCheatSheet.png)

## Resources to learn more

Here are some more resources if you want to dig deeper into the world of design patterns, you can check the following resources:

- **[Head First Design Patterns: A Brain-friendly Guide](https://amzn.to/3OxkE9P)** book.

- **[Design Patterns: Elements of Reusable Object-Oriented Software](https://amzn.to/3SKaa9x)** book by GoF.

- **[Awesome Software and Architectural Design Patterns](https://github.com/DovAmir/awesome-design-patterns)**, A curated list of software and architecture related design patterns.

- **[Design Patterns Library](https://www.pluralsight.com/courses/patterns-library)** Pluralsight course.

- **[Refactoring.Guru](https://refactoring.guru/)** website.

- **[Source Making](https://sourcemaking.com/design-patterns-and-tips)** website.