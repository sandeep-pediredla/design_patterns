## Design Patterns

These 26 can be classified into 3 types:

1. **Creational:** These patterns are designed for class instantiation. They can be either class-creation patterns or object-creational patterns.
2. **Structural:** These patterns are designed with regard to a class's structure and composition. The main goal of most of these patterns is to increase the functionality of the class(es) involved, without changing much of its composition.
3. **Behavioral:** These patterns are designed depending on how one class communicates with others.



## Behavioral:

Patterns that describe the way objects and classes interact and divide responsibilities among themselves.
A behavioral pattern abstracts an action you want to take from the object or class that takes the action. By changing the object or class, you can change the algorithm used, the objects affected, or the behavior, while still retaining the same basic interface for client classes.

Behavioral object patterns use object composition rather than inheritance

Some of these patterns describe how a group of peer objects cooperate to perform a task that no single object can carry out by itself. An important issue here is how peer objects know about each other. Peers could maintain explicit references to each other, but that would increase their coupling. In the extreme, every object would know about every other. The Mediator pattern avoids this by introducing a mediator object between peers. The mediator provides the indirection needed for loose coupling.

The key to understanding behavioral design patterns is communication.

The focus shifts from the objects and classes that make up a design pattern to the communication between objects and classes. In the truest form of composition, behavioral patterns are best understood in terms of how objects work together to perform tasks.

### Mediator Pattern:

A Mediator Pattern says that "to define an object that encapsulates how a set of objects interact".
Mediator pattern is used to reduce communication complexity between multiple objects or classes. This pattern provides a mediator class which normally handles all the communications between different classes and supports easy maintainability of the code by loose coupling.
Usage: message-based systems likewise chat applications

Mediator is a behavioral design pattern that lets you reduce chaotic dependencies between objects. The pattern restricts direct communications between the objects and forces them to collaborate only via a mediator object.

The decoupling process allows senders and requesters to be changed independently from each other.
There is one significant disadvantage to this pattern. Since the Mediator itself often needs to be very intimate with all the different classes, it can become extremely complex. This can make it difficult to maintain.

### Observer Pattern:
Potential pitfalls of implementing the Observer pattern.
You should be aware of a few potential pitfalls when implementing the Observer pattern:
Generally, you need to make sure that the change of state is complete and that the object has a consistent state before notifying observers of the change.
Be clear about whether the order in which Observer objects are notified is or is not predictable.
Do not let an Observer register itself twice with the same Observed object unless you are sure that is what it means to do

**Cons:**
Subscribers are notified in random order.

### State Pattern:
the class behavior changes based on its state. In State Pattern, we create objects which represent various states and a context object whose behavior varies as its state object changes.

The State pattern is closely related to the concept of a Finite-State Machine.
Use the pattern when you have a class polluted with massive conditionals that alter how the class behaves according to the current values of the class’s fields.

The State pattern lets you extract branches of these conditionals into methods of corresponding state classes. While doing so, you can also clean temporary fields and helper methods involved in state-specific code out of your main class.

**Pros:**

- Single Responsibility Principle. Organize the code related to particular states into separate classes.
- Open/Closed Principle. Introduce new states without changing existing state classes or the context.
- Simplify the code of the context by eliminating bulky state machine conditionals.

**Cons:**

- Applying the pattern can be overkill if a state machine has only a few states or rarely changes.
- State can be considered as an extension of Strategy. Both patterns are based on composition: they change the behavior of the context by delegating some work to helper objects.
- Strategy makes these objects completely independent and unaware of each other. However, State doesn’t restrict dependencies between concrete states, letting them alter the state of the context at will.

### Strategy:
lets you define a family of algorithms, put each of them into a separate class, and make their objects interchangeable.

**Pros:**

- You can swap algorithms used inside an object at runtime.
- You can isolate the implementation details of an algorithm from the code that uses it.
- You can replace inheritance with composition. Open/Closed Principle. You can introduce new strategies without having to change the context.

**Cons:**

- If you only have a couple of algorithms and they rarely change, there’s no real reason to overcomplicate the program with new classes and interfaces that come along with the pattern.
- Clients must be aware of the differences between strategies to be able to select a proper one.
- A lot of modern programming languages have functional type support that lets you implement different versions of an algorithm inside a set of anonymous functions. Then you could use these functions exactly as you’d have used the strategy objects, but without bloating your code with extra classes and interfaces.

Decorator lets you change the skin of an object, while Strategy lets you change the guts.

Template Method is based on inheritance: it lets you alter parts of an algorithm by extending those parts in subclasses. Strategy is based on composition: you can alter parts of the object’s behavior by supplying it with different strategies that correspond to that behavior. Template Method works at the class level, so it’s static. Strategy works on the object level, letting you switch behaviors at runtime.

**Rules of thumb:**

- Strategy is like Template Method except in its granularity.
- State is like Strategy except in its intent.
- Strategy lets you change the guts of an object. Decorator lets you change the skin.
  State, Strategy, Bridge (and to some degree Adapter) have similar solution structures. They all share elements of the 'handle/body' idiom. They differ in intent - that is, they solve different problems.
- Strategy has 2 different implementations, the first is similar to State. The difference is in binding times (Strategy is a bind-once pattern, whereas State is more dynamic).
- Strategy objects often make good Flyweights.

The Strategy pattern lets you do away with such a conditional by extracting all algorithms into separate classes, all of which implement the same interface. The original object delegates execution to one of these objects, instead of implementing all variants of the algorithm.

**Pros:**

- You can swap algorithms used inside an object at runtime.
- You can isolate the implementation details of an algorithm from the code that uses it.
- You can replace inheritance with composition.
   Open/Closed Principle. You can introduce new strategies without having to change the context.

**Cons:**
-If you only have a couple of algorithms and they rarely change, there’s no real reason to overcomplicate the program with new classes and interfaces that come along with the pattern.
-Clients must be aware of the differences between strategies to be able to select a proper one.
-A lot of modern programming languages have functional type support that lets you implement different versions of an algorithm inside a set of anonymous functions. Then you could use these functions exactly as you’d have used the strategy objects, but without bloating your code with extra classes and interfaces.

### Template Method:
Defines the skeleton of an algorithm in the superclass but lets subclasses override specific steps of the algorithm without changing its structure.

Use the Template Method pattern when you want to let clients extend only particular steps of an algorithm, but not the whole algorithm or its structure.

**Pros: **
 You can let clients override only certain parts of a large algorithm, making them less affected by changes that happen to other parts of the algorithm.
 You can pull the duplicate code into a superclass.

**Cons:**

- Some clients may be limited by the provided skeleton of an algorithm. 
- You might violate the Liskov Substitution Principle by suppressing a default step implementation via a subclass.
- Template methods tend to be harder to maintain the more steps they have.


Template Method is based on inheritance: it lets you alter parts of an algorithm by extending those parts in subclasses. Strategy is based on composition: you can alter parts of the object’s behavior by supplying it with different strategies that correspond to that behavior. Template Method works at the class level, so it’s static. Strategy works on the object level, letting you switch behaviors at runtime.

### Visitor:
Lets you separate algorithms from the objects on which they operate.

Imagine a seasoned insurance agent who’s eager to get new customers. He can visit every building in a neighborhood, trying to sell insurance to everyone he meets. Depending on the type of organization that occupies the building, he can offer specialized insurance policies:

If it’s a residential building, he sells medical insurance.
If it’s a bank, he sells theft insurance.
If it’s a coffee shop, he sells fire and flood insurance.

The Visitor pattern lets you execute an operation over a set of objects with different classes by having a visitor object implement several variants of the same operation, which correspond to all target classes.

**Pros:**

- Open/Closed Principle. You can introduce a new behavior that can work with objects of different classes without changing these classes.
- Single Responsibility Principle. You can move multiple versions of the same behavior into the same class.
- A visitor object can accumulate some useful information while working with various objects. This might be handy when you want to traverse some complex object structure, such as an object tree, and apply the visitor to each object of this structure.

**Cons:**

- You need to update all visitors each time a class gets added to or removed from the element hierarchy. 
- Visitors might lack the necessary access to the private fields and methods of the elements that they’re supposed to work with.

**Relations with Other Patterns**

- You can treat Visitor as a powerful version of the Command pattern. Its objects can execute operations over various objects of different classes. 
- You can use Visitor to execute an operation over an entire Composite tree.
- You can use Visitor along with Iterator to traverse a complex data structure and execute some operation over its elements, even if they all have different class