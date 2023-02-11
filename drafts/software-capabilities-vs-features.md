There's a lot of work invisible to end-users in software.
A big time sink is extending the software's capabilities, which are non-user-visible technical infrastructure that allow the software to do more stuff.

<a href="https://imgs.xkcd.com/comics/tasks.png"><img alt="" href="https://imgs.xkcd.com/comics/tasks.png"></img></a>
_Obligatory XKCD on this_

As somebody who works with or depends on software engineers, asking for time estimates on building new things can be a nerve-wracking experience.
You can get a bunch of estimates back that are on the orders of hours or days, and then a surprise one that's weeks or months.

# Use these terms

The confusion comes from a knowledge gap between the software engineers and everybody else.
The onus is on the engineers to explain the difference between **capabilities** and **features**.

**Capability**: New infrastructure that can be used to build lots of features on top of.
Usually fairly expensive to add.

**Feature**: A new thing that users can see and notice.

**Features** are built on top of **capabilities**, and usually the first feature, or first few, that require a capability take significantly longer than the ones that follow.

![You might think you're asking for a simple feature, and be surprised that it requires a new capability - or several](/images/capabilities.png)

# Example: Updating some legacy desktop software

**Feature**: We sell desktop photo-editing software that allows users to share their photos in the cloud.
We want this to work like Google Docs - changes should be visible, immediately, to all other users viewing a photo.

**Some new capabilities this might require**:
* A service that supports push notifications to clients (backend service)
* Clients need to be able to refresh photos currently being viewed without any user action (background polling)
* What if the clients get out of sync? Do we need a history of all edits so we can slot in user A's edits with user B's?

None of these are user-visible, but all of them are required new technical capabilities the engineering team will have to implement along with the actual feature.

# If you are an engineer

Talk to your customers/coworkers about what's actually possible cheaply, and what's not.

Explain which features require new (expensive) capabilities.

Try to come up with alternative versions of those features that use existing capabilities, and suggest them as cheaper alternatives.

# If you are somebody asking an engineer for something

Ask how to order feature delivery by smoothing out which capabilities are added when.

You'll need to have new capabilities to deliver the most interesting features, but you don't want to pay for all the new capabilities up front.

And the longer an existing capability is in your system, the cheaper it gets to build on top of.
