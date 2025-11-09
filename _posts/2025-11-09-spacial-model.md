---
title: "Spacial Model of an App"
date: 2025-11-09
---
Okay, so I wanna talk about the spatial model of your app. This is maybe more conceptual and more how you think about your own app.

![Spacial Model]({{ site.url }}/images/spacial_model.png)

## bullet points

### general

- important related topics
	- separation: all rules
	- push complexity down
- rails history and service object syndrome
- a big part of good software is identifying/labeling/classifying code
### controllers

if your app isn't a web app, or doesn't follow mvc, then where code execution starts in your app might be different, but for classic backend web framework it's a controller.

this is where we take the data we receive and do something worthwhile with it.

it has one foot in the framework and one in your app
### service layer

your service layer should be thin and not do any heavy lifting.  I'll explain more later (see: [[procedural thinking|Procedural Thinking and Service Obj Syndrome]])

business logic and high level behavior should live here and be isolated here.

#### service object syndrome


### app core

...

### low level & inner boundary

this is where data models, stdlib, third party libraries, and third party wrappers live.

differentiate between code we control and don't control

the lowest level is about enabling and possibilities.  without limitations

## service object syndrome



### organization

One thing I wanted to point out is when we deal with a lot of web frameworks, let's say, it tends to be very CRUD-based and based on objects, right? Like everything is grouped by object.

And then this one time at a different company, as soon as you break free from that, what I would call the core app, I grouped it by responsibility. So document parsing, document generation, file sharing or whatever it is. And I think that's more useful and I think it was a nice shift or I think it's an important shift that can be hard to do in a lot of CRUD frameworks. 

tldr; your core app doesn't have to be structured like your externally facing api
