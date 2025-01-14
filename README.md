# React setInterval Memory Leak
This example demonstrates a common mistake in React: using `setInterval` inside `useEffect` without proper cleanup.  This leads to a memory leak because the interval continues even after the component unmounts.

The `bug.js` file shows the incorrect implementation.  The `bugSolution.js` file provides the corrected version, showing how to use `clearInterval` to prevent the leak.

## How to reproduce the bug:
1. Clone the repository.
2. Run `npm install`.
3. Run `npm start`.
4. Observe the counter in the browser.  Even after unmounting the component (e.g., navigating away), the counter will continue to increment in the console because the interval persists.

## How to fix the bug:
The solution involves returning a cleanup function from `useEffect`.  This function will be executed when the component unmounts, allowing us to clear the interval using `clearInterval`. This prevents memory leaks.