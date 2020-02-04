---
layout: post
title:      "What is Hoisting?"
date:       2020-02-04 21:31:37 +0000
permalink:  what_is_hoisting
---



In Javascript, hoisting is where variables and function declarations are moved to the top of their scope before code execution,  this is what allows you to call a function before they are written in your code.  When working with variables, hoisting only moves the declaration and leaves its assignment in place.

Hoisting differs slightly between var, let, and const:
	
	**var**: As stated previously, only the variable declaration is hoisted to the top of the scope, not it’s assignment. If you use this variable before declaring and assigning it, the variable will be undefined.

**	let and const**: In comparison to var, which allows us to create a locally scoped variable, let and const scopes a variable to the block, this could be a function, conditional blocks, and loops.  Let and const are still hoisted to the top of their scope but unlike var, where variables are initiated with undefined, let and const remain uninitiated. If you try to access these before they are initiated, a ReferenceError will take place.

	Hoisting also takes place with functions but differs between function declarations and function expressions. Function declarations are hoisted completely to the top, which enables you to invoke a function before declaring it.  However function expressions are not hoisted, so you cannot call a function before it is defined.

