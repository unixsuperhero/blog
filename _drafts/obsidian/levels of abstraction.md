#spacial 
goes hand in hand with pushing complexity down

there aren't really any hard-defined levels of abstraction

it's all relative

but when i'm talking about LoA there are 2 general anchors and the gray area in-between.
1. Human Level - Highest Level
2. ...
3. Direct Data Manipulation - Lowest Level

at the lowest levels, you don't want to impose business logic or restrictions.
don't make assumptions about how it will be used.
don't impose or enforce limitations.

### examples
#### related to: composition

strings vs. an array of strings

a string, a primitive is a low-level data structure.
an array of strings is at a higher level of abstraction.  it's a structure that manages and oversees strings.

similar to how your app might have background jobs.  there is usually a system that lives above the jobs that is responsible for things like queuing jobs, running jobs, monitoring the status of jobs.

but the simples explanation is data composition.  if you have an object, whatever its attributes are, the object is at a higher level of abstraction than the attributes.
let's say you have an ecommerce store.  An Order class is a higher-level of abstraction than the products being ordered.  It's debatable whether a User/Customer is higher than an Order or vice-versa, maybe they live at the same level, or maybe it's both depending on the situation?