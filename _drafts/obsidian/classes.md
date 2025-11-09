This may seem crazy, but I feel like a lot of developers haven't learned basics about classes.  I don't want to get into the reasons why.  But, I think it's worthwhile to look at some basics and how I write and approach writing a class.

Of course, there are many different patterns, but the vast majority of the time, I'm approaching classes the same way.

### the bullet points
- a constructor just stores off attributes and the values it was given.  nothing more.
- i don't use setters
	- nothing should have direct access to another class's attributes/data (see: encapsulation)
- immutable state - depends on the pattern, but i strive for this unless it's something like a Builder
	- i will add state for the purposes of memoization, but i usually don't change shared values
- when i write methods
	- naming - don't start with verbs when dealing with data
	- the vast majority of the time i am just exposing data points
	- always thinking about how the class could be used and what data could be useful to something outside the class
	- never really concerned with achieving one specific goal for the class (see: procedural thinking)
	- atomic operations - a complete set if possible when trying to encapsulate a data structure that needs managed data that needs to be manipulated
- interfaces > implementation
	- it's always about the outside world and how it will use this class, not what this class needs to accomplish

#### service object syndrome

see: separation

- Workflow::GetService
- Workflow::TriggerService