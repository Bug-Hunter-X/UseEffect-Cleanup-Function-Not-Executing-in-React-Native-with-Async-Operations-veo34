# useEffect Cleanup Function Not Executing in React Native with Async Operations

This repository demonstrates a common issue in React Native where the cleanup function in `useEffect` might not execute properly when dealing with asynchronous operations.  The problem arises when a component unmounts before an asynchronous task (like a fetch call) within `useEffect` completes. This can lead to memory leaks, race conditions, or other unexpected behavior.

## Problem

The provided `bug.js` file showcases this problem. The `useEffect` hook fetches data asynchronously.  The cleanup function logs a message indicating component unmounting.  If you quickly unmount the component before the fetch completes, the cleanup function will not run.

## Solution

The `bugSolution.js` file provides a solution using AbortController to gracefully handle the situation.  By creating an AbortController, we can abort the fetch request if the component unmounts before the response arrives. This ensures resources are cleaned up properly and prevents unexpected errors.