# React useEffect Hook Memory Leak with setInterval

This example demonstrates a common mistake in React's `useEffect` hook when using `setInterval`.  Forgetting to return a cleanup function leads to memory leaks.

The `bug.js` file contains the erroneous code. The `bugSolution.js` file shows the corrected version.

## Bug

The `setInterval` function continues to run even after the component unmounts, causing a memory leak.  This is because the `useEffect` hook's cleanup function (returned from the effect function) isn't used to stop the interval.

## Solution

The solution involves returning a cleanup function from the `useEffect` hook. This function will be called when the component unmounts or when the dependencies change, ensuring the interval is cleared.