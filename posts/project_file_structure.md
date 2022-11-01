---
title: Project file structure
publish_date: 2022-11-01
---

Firstly, it's essential to state that file structure is an important part of architecture. Folders and file names are like road signs which help not to go astray and stick to the architecture. That's why I sometimes use terms 'architecture' and 'file structure' interchangeably. Although, these road signs are important, they are not stopping a driver from crashing his car into a tree. Keep it in mind.

# The problem

Let's imagine that you're a new developer in a company and you've just got on a project. You open the project's source code and see this:

```
src
└───@types
└───HOC
└───assets
└───components
└───config
└───constants
└───context
└───helpers
└───hooks
└───schemas
└───services
└───styles
└───utils
|	App.tsx
|	index.tsx
```

Seems like a pretty reasonable file structure, isn't it?. Components go to the components folder, hooks to the hooks folder, utilities go to the utils folder... or... to the helpers?

The more questions new developer asks about project's architecture and file structure the more stressed and confused she/he gets, especially if it's a junior developer. Every time he/she wants to change something he/she goes to team members and distracts them with questions like "Should I place it here or there?", "Where can I find..." and so on and so forth.

Moreover, this kind of architecture tells nothing about business problems the product solves. Looking at these folders we can't say if its an online store, blog or something else. How can a developer do his best if he can't easily understand the product's purpose and, for example, its features?

# Feature sliced design to the rescue

That's how it looks:

```
src
└───app
└───processes
	└─auth
└───pages
└───widgets
	└─header
└───features
	└─add-comment
	└─delete-comment
	└─like-post
└───entities
	└─user
		└─ui
		└─model
		└─api
	└─post
	└─comment
└───shared
	└─components
	└─assets
	└─utils
```

There are many ways of structuring your project but feature sliced design is my favorite one because:

-   relations between layers of an app are well defined and lead to easy and isolated modifications
-   oriented to business and user needs
-   well documented
-   quite reusable
-   a project can be adopted to feature sliced design incrementally

I dont' want to retell [the docs](https://feature-sliced.design/) and I recommend you to read it by yourself. I will only point out the main ideas:

-   App consists of **layers** (shared, entities, features etc.), **slices** (user, post, comment etc.) and **segments** (ui, model, api)
-   Each layer has it's own responsibility
-   Modules on one layer can only interact with modules from the layers stricly below, for example: shared modules can't import anything from entities, while pages can be built using widgets, features and shared components.

Looking at feature sliced structure from the above a new developer can easily understand that it's a blog application where a user can add and delete comments, like posts etc. Also a project manager can describe a project using these terms too. It leads to better communication between team members and helps to overboard new people.

There are many more benefits of using feature sliced design which are well documented in [the docs](https://feature-sliced.design/). I highly recommend you to check it out and learn new ways of organizing your frontend project.
