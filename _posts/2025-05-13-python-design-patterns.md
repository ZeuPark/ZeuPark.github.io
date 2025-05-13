---
title: "Applying Design Patterns and Structure in Python: Singleton, Modules, Packages"
date: 2025-05-12
layout: single
tags:
  - python
excerpt: "How I used singletons and modular structure to better organize larger Python projects."
---


## What I Learned

### Singleton Pattern
- Guarantees only one instance exists.
- Useful for shared state like configurations.

### Modules and Packages
- Modules are `.py` files that group functions and classes.
- Packages are directories with `__init__.py` that hold modules.

## What I Thought About

When I split a project into modules, it became easier to think about "who does what." It reduced the mental load. The singleton pattern also reminded me how to control object creation and prevent bugs from multiple initializations.

It helped me think more like a system designer — not just a coder writing line by line.

## What I Want to Do Next

- Build a config manager with singleton logic.
- Make a mini library from some functions and import them with proper packaging.
- Study other patterns like Factory or Observer and practice in small projects.

