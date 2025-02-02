# React 19 useEffect Dependency Issue

This repository demonstrates a common error in React 19's `useEffect` hook:  forgetting to include state variables in the dependency array.  This can lead to infinite render loops and unexpected behavior.

## Bug Description
The `MyComponent` component uses `useState` to track a count. The `useEffect` hook is intended to log the count after every render.  However, the initial implementation omits `count` from the dependency array. This causes the effect to run on every render, which leads to an infinite loop because `setCount` triggers a re-render, causing `useEffect` to run again, and so on.

## Solution
The solution involves adding `count` to the dependency array of `useEffect`. Now, the effect only runs when the `count` changes.