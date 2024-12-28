# JavaScript Closure Issue in Loops with setTimeout

This repository demonstrates a common error in JavaScript related to closures and the use of `setTimeout` within loops.  The code intends to log numbers 0 through 9 with a one-second delay between each. However, due to how closures work with the loop variable, it unexpectedly logs the number 10 ten times.

## Problem
The issue stems from the fact that `setTimeout` is asynchronous.  By the time the `setTimeout` callbacks finally execute, the loop has already completed, and the value of `i` is its final value (10). Each callback, therefore, captures and uses the same final value of `i`.

## Solution
The solution involves creating a new scope for each iteration of the loop using an immediately invoked function expression (IIFE).  This ensures that each callback has its own copy of `i`, preserving the correct value at the time of scheduling.