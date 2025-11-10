---
title: "Introduction: Spatial Model of an App"
---

**NOTE:** This is still a draft.

A lot of the information you will find in the [Catalog]({{ site.catalog_page }})
is not new information.

However, these ideas have been lost for one reason or another.

Here, we will look at 2 simplified models of an app, specifically modeling a
traditional MVC web app.  However, these models can be applied to a lot of
non-web apps.  In that case, some of the sections should probably be renamed.

These models broadly represent how I think of an app spatially. They are not
meant to be exhaustive or precise.

We are starting the catalog with these models, because they will be a useful
visual and reference for later sections.

At the top, you have the "entrypoints" into the code. For a web app, there are
other layers not represented here, but what we care about is the code that we
control.  So the parts of your web framework that handle things like
routing aren't included.

# The First Model

![]({{ site.image_url }}/spacial_model.03.service_object_syndrome.png)

This model is not the ideal model, but it is what I've seen often.

### A Small History Lesson

Let's talk about Rails, for a minute.

Since Rails first became popular, Rails projects have seen the same issue over
and over in different forms.

First, it was Fat Controllers.  People were loading all of the app's logic in
the controllers.  As a result, controllers were painful to manage.

Then, the logic was moved from the controllers to the models.  As a result, Fat
Models became the new bucket where all the app's logic was store.

Finally, Service Objects became popular.  Ever since, services became the
pattern that houses everything.

I don't blame people for being told one thing and sticking to it.  But Service
Objects introduce their own flavor of issues.

# The Second Model

![]({{ site.image_url }}/spacial_model.02.png)

This is the model is more ideal.  We have 6 main sections in 4 groups.

1. Controllers
1. Service Layer
1. Core Application
1. Data Objects
1. Data Models
1. Third-party Wrappers

Controllers sit at the boundary between our framework and our app.

Services make up a **thin layer** of procedures that orchestrate
the components in our core application.

The Core Application is intentionally a big `fill-in-the-blank` section.  We
will look at it more closely in later sections of the
[Catalog]({{ site.catalog_page }}).  For now, just know that it will take
different shapes depending on the app and its problem domain.

Finally, we have Data Objects, Data Models, and Third-party Wrappers that
make up the final group.  These sections make up the boundary
between the app and its low-level dependencies like your language's stdlib
and the third-party packages your app relies on.



