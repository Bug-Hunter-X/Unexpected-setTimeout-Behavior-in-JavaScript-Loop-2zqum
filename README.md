# Unexpected setTimeout Behavior in JavaScript Loop

This repository demonstrates a common JavaScript closure issue encountered when using `setTimeout` within a loop.  The expected behavior might be to print 0 through 9 sequentially after a 1-second delay. However, due to the nature of closures and how variables are captured, the output will be unexpected.

## The Problem

The issue lies in how `setTimeout` handles the `i` variable.  The callback function inside `setTimeout` doesn't create a new copy of `i`; instead, it captures a reference to the `i` variable. By the time `setTimeout` executes, the loop has already finished, and `i` will be its final value (9). Therefore, all callbacks will print 9.

## Solution

The solution involves creating a new scope for each iteration using an immediately invoked function expression (IIFE) or a `let` declaration inside the loop (as shown in the solution file). This ensures that each callback function has its own copy of the `i` variable at the time of its creation.