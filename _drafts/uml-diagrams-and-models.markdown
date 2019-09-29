---
layout: post
title: UML Diagrams and models
tags:
- english
- development
---

Something stomethign sometsingsfds fmdslkm introo.......

I've just finished updating our diagrams / models in the projekct I'm working on. We're using [PlantUML](http://plantuml.com/) and the [C4 model](https://c4model.com/) by [Simon Brown](http://simonbrown.je/), and I really like the look Simon have created. Up until now we've used [C4-PlantUML](https://github.com/RicardoNiepel/C4-PlantUML) which inlcude styling of the four levels in the _C4 model_. Today I needed to create a sequence diagram and the _C4-PlantUML_ project didn't have any styling for that.

A quick google search led me to the [PlantUML C4 Model](https://github.com/xuanye/plantuml-style-c4) project which also have styling for _activity_, _class_, _sequence_, _state_ and _use case_ diagrams. Perfect! So today I've switch over to using this project for all our diagrams, and added two sequence diagrams.

I've found one litle problem with the _PlantUML C4 Model_ and that is missing styling for _PlantUMLs_ _grouping_ syntax. The frame and the text have very similar colours. I might just fix that...