---
layout: post
title:      "Variable Scope in Javascript "
date:       2020-02-04 21:52:40 +0000
permalink:  variable_scope_in_javascript
---


Like many new to writing code, knowing the scope of a variable or more often, not knowing the scope of a variable was a common hurdle in my day-to-day adventure in learning Javascript.  Here, I hope to breakdown variable scope as well as cement my own understanding of the topic.

Javascript has two scopes, *global and local*.  Any variable declared outside of a function belongs to the global scope, and is therefore accessible from anywhere in your code.  Local scope is created by functions and each function has its own "local" scope, therefore any variable declared within a function, can be used within that function or correlating nested functions. Local scope is often referred to as ** function scope** and with the addition of ES6 can be further divided to include **block scope**.  In ES6, const and let keywords allow developers to declare variables in the block scope, which means those variables exist only within the corresponding block. In general a block in Javascript is anytime you see "{curly braces}" like in a for loop, or when declaring a new function.

### Scope difference between var, let, and const

**Var**: var is globally scoped when declared outside a function, which means it is accessible for use in the whole window object. Var is locally scoped when declared within a function and can only be used within that function.

**Let**: Let is a block-scoped variable, when declared it can only be accessed and updated within its block “{ }” but unlike var cannot be re-declared within its scope. Because let is block scoped, you could have the same variable declaration defined in different scopes

**Const**: Like let, const is also block-scoped, with the difference being const cannot be updated within its scope, once declared it maintains a constant value.



