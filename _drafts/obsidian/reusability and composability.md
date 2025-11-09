first, reusability and composability are basically the same thing.

in order for something to be Reusable and composable it needs to be able to be used in multiple contexts.  for that to happen, it needs to be free from tight coupling, or at least be selective with what it is coupled to.

this is also why it's good to understand levels of abstraction. 

if you can identify what is low level, make that atomic than any level above that can couple as much as it wants and it doesn't hinder reusability. 

When making a lib or a third-party wrapper like this, it can be tempting to put business logic and constraints on the methods or the API in general. But at this level of abstraction, the last thing you want is to impose restrictions. instead of thinking about situations you don't want to happen, this layer is about opening up possibilities and enabling anyone who uses it.

even if the one place that it is used is one class, that one class is the place you want to apply restrictions and anyone who needs those restrictions can call that class.