# Node.js Server Unresponsiveness: Synchronous Operations

This repository demonstrates a common issue in Node.js applications: unresponsiveness due to synchronous operations within the request handler.  Long-running synchronous tasks can block the event loop, preventing the server from handling other requests.

The `bug.js` file shows a server that simulates a long-running task (using `setTimeout` to mimic a database query or other I/O operation).  This causes the server to become unresponsive during the 5-second delay.  The solution is demonstrated in `bugSolution.js`.

## How to reproduce

1. Clone this repository.
2. Navigate to the repository's directory.
3. Run `node bug.js`
4. Try to access the server (e.g., with `curl http://localhost:3000` or a web browser).
5. Observe the unresponsiveness.
6. Run `node bugSolution.js` and repeat steps 4 and 5 to see the improved responsiveness.

## Solution

The solution involves performing asynchronous operations using promises or async/await to prevent blocking the event loop.  The `bugSolution.js` file shows an example using promises.