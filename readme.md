# Using the {golem} package to convert existing PoC Shiny apps to production quality - lessons learned

This repo is intended to capture my thinking and lessons learned in converting an existing Shiny application to "production" standards using the {golem} package: https://thinkr-open.github.io/golem/.

## Background
I am a statistician by training and I work in the pharmaceutical industry where my statistical and clinical pharmacology / pharmacometrics colleagues are learning to use R and Shiny to develop applications that will help design trials, explore and visualize data, simulate outcomes from models (typically nonlinear, mixed effects models). These colleagues are *not* software developers and are typically not familiar with the principles of software development. The apps they develop can be viewed as "Proof of concept" and "fit for purpose" in their use - the help answer a specific question for a specific set of inputs and although they can inform decisions, they are not (yet) used in regulatory interactions. 

## Why bother with "productionising" (these) applications?
Given the context in which many of these Shiny apps were developed, there is little benefit to refactoring the code to "productionise" these apps. Refactoring every app would be resource intensive and the appropriate expertise to do so is not readily available. However, from time to time there are certain applications which go beyond this "Proof of concept" stage and would benefit a wider group of colleagues. In this case it makes sense to take the existing code, refactor, test and productionise it so that we can be more confident that the code base is correct and tested, better supportable for the future and optimised for a larger group of users than the original "Proof of concept". In these cases it pays to have a framework for productionising that the {golem} package offers.

## TL;DR - lessons learned
  
  * ***Plan first.***  Draw your application modules on paper (yes, paper and pencil)
    * *Modules.* Identify how they interact, what information must be passed between modules
    * *UI design.* Improve your UI so that it is more friendly to users.
    * *Naming conventions.* Naming for modules, objects to be passed between modules, functions. Lock it down ***before*** you start.
    * *Common code.* If you need it in many modules, make it a function. Using {golem} is a lot like writing an R package.
  * ***Passing information / objects between modules.*** NOW is the right time to learn about programming Shiny applications using modules and techniques for passing objects between modules, and knowing the when to use reactivity and when to use `observe` or `isolate`.
    * https://rtask.thinkr.fr/communication-between-modules-and-its-whims/ 
    * https://itsalocke.com/blog/shiny-module-design-patterns-pass-module-inputs-to-other-modules/
    * https://resources.rstudio.com/shiny-developer-conference/shinydevcon-reactivity-joecheng-part-1-1080p
    * https://resources.rstudio.com/shiny-developer-conference/shinydevcon-reactivity-joecheng-part-2-1080p
    > "Keep your side effects
    Outside of your reactives
    Or I will kill you" - Joe Cheng.

    