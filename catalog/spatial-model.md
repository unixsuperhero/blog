---
title: "Introduction: Spatial Model of an App"
---

A lot of the information you will find in the [Catalog]({{ site.catalog_page }})
is not new information.

However, these ideas have been lost for one reason or another.

Here, we will look at 2 simplified models of an app, specifically modeling a
traditional MVC web app.  However, these models can be applied to a lot of
non-web apps.  In that case, some of the sections should probably be renamed.

These models broadly represent how I think of an app spatially. They are not
meant to be exhaustive or precise.

At the top, you have the "entrypoints" into the code. For a web app, there are
other layers not represented here, but what we care about is the code that we
control.  So the parts of your web framework that handle things like
routing aren't included.

# The First Model

![]({{ site.image_url }}/spacial_model.02.png)

# The Second Model

![]({{ site.image_url }}/spacial_model.03.service_object_syndrome.png)

