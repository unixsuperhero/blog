One thing about procedural thinking or service object syndrome is that things tend to be procedures for a specific task, and that task has business logic encoded in it and all sorts of stuff encoded in it. So it doesn't become very reusable. these tasks are vertical slices. But if you look at the responsibilities and you break them out horizontally, you will probably see a lot of room for shared code and reusability. 

another thing, coupling.
inputs and outputs tend to be tailored to what comes before and after it respectively.  because you know what's needed for things to work, there tends to be data manipulation and fragmentation and all sorts of weird choices made that take code that could be reusable and make it single purpose.

### example
an example of coupling and encapsulating is primitive obsession.  say you use a hash or object (key/val store, not a class) and you construct it in one method then pass it to another. if you rename or restructure that hash, you have to update both methods... coupling.

but, if you make a value object and encapsulate that hash, and expose it's values via methods, then it doesn't matter how often you change the internal structure, the method sig stays the same, the change is isolated to the one class, and anyone who uses that class is none the wiser.

even in the same object with atomic operations

### why extract value objects - data frag
one thing that is really common with procedural thinking is primitive obsession and data fragmentation, and a lot of upfront data manipulation to prepare values for the next step.

if you encapsulate data, you can pass the whole object and all of the context goes with it.

have you ever seen a method with a lot of args (code smell), and you figure out it needs another, so the list grows?  and you might notice that the source for half of the args is the same place. if that was wrapped in an object, the method signature wouldn't have to change.  just add a method to the object, *if it doesn't already exist*.  that is the beauty of objects... and especially pulling out data ([[code/separation]]) once you define how to get a data point, you never have to write that code again.

a lot of devs don't make mid level data objects. it tends to only be the models that mirror database tables.


# sicp
procedures are active, data is passive


# service object syndrome

## history lesson:

let's look at common issues that rails has had over time and how it was addressed.

1. in the beginning everyone put all their business logic in their controllers.  (fat controllers)
2. then they started moving business logic to models (fat models)
3. then service objects became popular (and POROs).  now people have been shoving all their code in service objects for over a decade.

people just keep moving their mess.  it's like everyone is always looking for one way to do things that works for everything.  that's just not how things are.

not only that, service objects come with their own set of issues.

#### issues

- hide useful things
	- hard to test/debug
- coupling
	- temporal and poorly separating the work
	- inputs/outputs are too aware of the internals of how they're used
	- tends to be the end of the road 
- data fragmentation/manipulation (LoA aren't separated)
- implementation/code is valued more than the interfaces
	- single purpose





i