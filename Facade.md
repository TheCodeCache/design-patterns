It's classified as a structural design pattern.

"The idea is to make a complex system or subsystem or a set of subsystems easier to use" - Facade

The Problem:

1. Imagine, you enter an IT company main-gate and there is no reception counter. How would you feel? Can you sense a number of problems can appear?
    For ex: how would you move across the company's internal departments (HR, Engineering, RnD, Finance, Sales etc.),
    
    this is precisely the problem that is addressed through Facade Pattern
2. Imagine, you enter a bank and there is no reception counter again. How would go about knowing things, like where to collect the deposit form, or which is the loan counter,
    or where to submit the withdrawl form etc.
    
    this is precisely the problem that is addressed through Facade Pattern
    
Another problem:
    Suppose you are in an restaurant, but there is no menu, and no waiter, can you imagine the situation?
        this is exactly the problem that the Facade pattern tries to address,
        
    In this case, the menu acts the Facade between you and the food making & servicing sub-system,
    As a customer, we should not be worried about who cuts the veggies, who cooks the meal, what ingredients they use etc. 
    or even which of the many waiter serves you on the plate, you do not care about that, right! 
    all you need is a menu where you can just choose what to eat, and place order, and you are done!
    
    This is exactly the situation, where Facade pattern helps to resolve
    
Another example:

    We've got multiple caching solutions for ex: MemCache, Redis, etc. 
    and there functioning could be completely different and complex, and as an user you want to frequently switch b/w these solutions as per the need,
    
    in this case, your actual business logic will be mixed up with the initialization and invocation of these several different caching services,
    
    this is where, the Facade pattern comes to the rescue. it simplifies things up and provides an easy to interface by encapsulating several components and exposing simple APIs
    
    For Ex: "ScalaCache" is the "Facade" for many such caching solutions, It's easy to switch b/w these caching solutions, and the APIs are quite simple to use
    
Code: (https://github.com/TheCodeCache/Design-Patterns/tree/master/code)
    PFB 3 examples:
    1. AnimalFacade.java
    2. ShapeFacade.java
    3. Computer.java
    4. Food.java


Facade vs Abstraction:
    The relationship between the two: The Facade pattern is a subset of "layers of abstraction". A Facade is an added level of abstraction. Not all abstractions are Facades.
    The facade pattern is an simplified interface to a larger, possibly more complex code base. 
        The code base may be a single class, or more. The facade just gives you a simple interface to it.
    Abstraction, is used to represent a concept, but not to be bound to any specific instance. (Ie: An abstract class). 
        This doesn't imply simplifying (like the facade pattern does), but rather making a 'common' interface or representation.
    If you are simply forwarding one call to another class with the same interface, that is more accurately the Proxy pattern. 
        This is another type of abstraction layer.

general points:
    1. A facade can be created just out of a single class as well, provided the given single class is too complex to use it.
    2. Facade can be created for a group of co-related subsytems and provides a simple interface or expose set of simple APIs to the end user to use
    3. It, just like proxy pattern, is a subset of 'Abstraction' concept
    4. It hides the complexities of the system ad provides an interface to the client using which the client can access the system.
    5. This pattern falls under structural pattern, bcoz this pattern adds an interface to existing sytem to hide its complexities.
    6. It provides simplified methods required by the client and delegates calls to methods of existing system classes.
    7. Facade layer should not be forced and its always optional.
    8. We can always expose the subsytem directly through Facade, but that would be against the best practice, as the resultant code will look ugly
    9. Subsystems are not aware of the existence of facade. Only facade talks to the subsystems. it's unidirectional from Facade to its underlying subsystems.
    10. Subsystem may be dependent with one another. In such case, facade can act as a coordinator and decouple the dependencies between the subsystems.
    11. Translating data to suit the interface of a subsystem is done by the facade
    12. Facade design pattern is used for promoting subsystem independence and portability
    13. Facade provides a single interface
    14. GoF Definition: Provide a unified interface to a set of interfaces in a subsystem. 
        Facade Pattern defines a higher-level interface that makes the subsystem easier to use.

    
Common Mistakes People do while implementing Facade Pattern:

    1. just for the sake of introducing a facade layer developers tend to create additional classes. 
        Layered architecture is good but assess the need for every layer. Just naming a class as ABCDFacade.java doesn’r really make it a facade.
    2. Creating a java class and ‘forcing’ the UI to interact with other layers through it and calling it a facade layer is one more popular mistake. 
        Facade layer should not be forced and its always optional. 
        If the client wishes to interact with components directly it should be allowed to bypass the facade layer.
    3. Methods in facade layer has only one or two lines which calls the other components. 
        If facade is going to be so simple it invalidates its purpose and clients can directly do that by themselves.
    4. A controller is not a facade.
    5. Facade is ‘not’ a layer that imposes security and hides important data and implementation.
    6. Don’t create a facade layer in advance. 
        If you feel that in future the subsystem is going to evolve and become complicated to defend that do not create a stub class and name it a facade. 
        After the subsystem has become complex you can implement the facade design pattern.
    7. Subsystems are not aware of facade and there should be no reference for facade in subsystems.

Reference(s):
- https://en.wikipedia.org/wiki/Facade_pattern
- https://javapapers.com/design-patterns/facade-design-pattern/
- https://www.opencodez.com/java/facade-pattern.htm
- https://stackoverflow.com/a/2288682
