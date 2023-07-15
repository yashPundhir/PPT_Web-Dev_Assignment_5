# Assignment 5 - JavaScript

---

**Ans1.**
In JavaScript, the terms "synchronous" and "asynchronous" refer to different ways of handling and executing code. Here's the difference between the two:

Synchronous Execution:

1. In synchronous code, statements are executed one after another, in a sequential manner. Each statement must complete before the next one can begin.
2. Synchronous code follows a "blocking" behavior, where a statement or operation blocks the execution of subsequent statements until it finishes.
3. In synchronous execution, if there is a long-running task or operation, it can cause the entire program to freeze or become unresponsive until the task is completed.

Example of synchronous code:

```javascript
console.log("Start");
console.log("Hello");
console.log("End");
```

In the example above, the statements are executed sequentially, and each `console.log()` statement is completed before the next one begins. The output will be:

```
Start
Hello
End
```

Asynchronous Execution:

1. In asynchronous code, statements are not necessarily executed in the order they appear. They can be scheduled to run at a later time or triggered by events.
2. Asynchronous code follows a non-blocking behavior, allowing other statements to continue executing while an asynchronous operation is in progress.
3. Asynchronous code is commonly used for operations that involve I/O, network requests, timers, or callbacks.

Example of asynchronous code:

```javascript
console.log("Start");

setTimeout(function () {
	console.log("Async Task");
}, 2000);

console.log("End");
```

In the example above, the `setTimeout()` function is an asynchronous operation that schedules the provided function to run after a delay of 2000 milliseconds (2 seconds). While waiting for the delay to complete, the execution continues to the next statement. The output will be:

```
Start
End
Async Task (after 2 seconds)
```

The "Async Task" statement is logged after the delay, even though it appears in the code before the "End" statement. This demonstrates the non-blocking nature of asynchronous code.

---

**Ans2.**
In JavaScript, Web APIs refer to the collection of APIs (Application Programming Interfaces) provided by web browsers. These APIs expose various functionalities and services that allow JavaScript code to interact with web browser features and resources. Web APIs are implemented by the browser and are accessible to JavaScript code running within the browser environment.

Here are some commonly used Web APIs in JavaScript:

1. DOM API (Document Object Model): The DOM API provides methods and interfaces for manipulating the HTML structure of a web page. It allows JavaScript code to access, modify, and interact with HTML elements, attributes, and styles.

2. XMLHttpRequest (XHR): The XMLHttpRequest API enables JavaScript code to make HTTP requests to fetch data from servers asynchronously. It is commonly used for AJAX (Asynchronous JavaScript and XML) interactions and can be used to update parts of a web page without reloading the entire page.

3. Fetch API: The Fetch API is a modern and more flexible alternative to XHR for making HTTP requests. It provides a simple and powerful interface for fetching resources asynchronously, handling responses, and working with Promises.

4. Web Storage API: The Web Storage API allows JavaScript code to store data locally on the user's browser. It provides mechanisms such as localStorage and sessionStorage to store and retrieve key-value pairs persistently or for the duration of a browsing session.

5. Geolocation API: The Geolocation API provides access to the geographical location of the device running the web browser. It allows JavaScript code to retrieve the user's location information, enabling location-based services in web applications.

6. Canvas API: The Canvas API allows JavaScript code to draw and manipulate graphics, images, and animations dynamically. It provides a programmable drawing surface on which developers can create and manipulate visual content.

7. Web Audio API: The Web Audio API provides functionality for creating, manipulating, and controlling audio in web applications. It enables tasks such as audio playback, synthesis, effects processing, and audio visualization.

8. Web Speech API: The Web Speech API allows JavaScript code to integrate speech recognition and synthesis capabilities into web applications. It enables developers to process spoken language and generate speech output.

---

**Ans3.**
Both `setTimeout` and `setInterval` are functions provided by JavaScript for scheduling the execution of code at specified intervals. Here's an explanation of each:

1. setTimeout:
   The `setTimeout` function allows you to schedule the execution of a function or the evaluation of an expression after a specified delay (in milliseconds). It executes the code once after the delay and then stops.

   Syntax:

   ```javascript
   setTimeout(function, delay, param1, param2, ...);
   ```

   Example:

   ```javascript
   function greet() {
   	console.log("Hello!");
   }

   setTimeout(greet, 2000);
   ```

   In the example above, the `greet` function is scheduled to execute after a delay of 2000 milliseconds (2 seconds). After the specified delay, the function will be invoked, and 'Hello!' will be logged to the console.

2. setInterval:
   The `setInterval` function is used to repeatedly execute a function or evaluate an expression at a specified interval (in milliseconds) until it is cleared or the page is unloaded. It keeps executing the code repeatedly in intervals.

   Syntax:

   ```javascript
   setInterval(function, delay, param1, param2, ...);
   ```

   Example:

   ```javascript
   function printTime() {
   	const now = new Date();
   	console.log(now);
   }

   setInterval(printTime, 1000);
   ```

   In the example above, the `printTime` function is scheduled to execute repeatedly every 1000 milliseconds (1 second). It will continuously log the current time to the console until the `setInterval` is cleared or the page is unloaded.

Both `setTimeout` and `setInterval` return a unique identifier (a numerical value) that represents the timer being set. This identifier can be used to cancel or clear the scheduled execution using the `clearTimeout` or `clearInterval` functions, respectively.

---

**Ans4.**
Handling asynchronous code in JavaScript involves using various techniques and patterns to ensure that code execution continues smoothly despite the non-blocking nature of asynchronous operations. Here are some common approaches for handling asynchronous code:

1. Callbacks:
   Callbacks are a traditional way of handling asynchronous operations in JavaScript. A callback is a function that is passed as an argument to an asynchronous function and is executed once the operation completes.

   Example:

   ```javascript
   function fetchData(callback) {
   	// Simulating an asynchronous operation
   	setTimeout(() => {
   		const data = "Some data";
   		callback(data);
   	}, 2000);
   }

   function processData(data) {
   	console.log("Data received:", data);
   }

   fetchData(processData);
   ```

   In the example above, the `fetchData` function simulates an asynchronous operation and accepts a callback function. Once the operation is complete (after a delay of 2000 milliseconds), it invokes the callback with the retrieved data.

2. Promises:
   Promises provide a more structured way to handle asynchronous code. A promise is an object that represents the eventual completion (or failure) of an asynchronous operation and allows you to chain operations and handle success or error cases.

   Example:

   ```javascript
   function fetchData() {
   	return new Promise((resolve, reject) => {
   		// Simulating an asynchronous operation
   		setTimeout(() => {
   			const data = "Some data";
   			resolve(data);
   		}, 2000);
   	});
   }

   fetchData()
   	.then((data) => {
   		console.log("Data received:", data);
   	})
   	.catch((error) => {
   		console.error("Error:", error);
   	});
   ```

   In the example above, the `fetchData` function returns a Promise. Once the asynchronous operation completes, it resolves the Promise with the retrieved data. You can use `.then()` to handle the successful result and `.catch()` to handle any errors that occur.

3. Async/await:
   Async/await is a modern approach to handle asynchronous code that builds on top of Promises. It allows you to write asynchronous code in a more synchronous style, making it easier to read and maintain.

   Example:

   ```javascript
   function fetchData() {
   	return new Promise((resolve, reject) => {
   		// Simulating an asynchronous operation
   		setTimeout(() => {
   			const data = "Some data";
   			resolve(data);
   		}, 2000);
   	});
   }

   async function processData() {
   	try {
   		const data = await fetchData();
   		console.log("Data received:", data);
   	} catch (error) {
   		console.error("Error:", error);
   	}
   }

   processData();
   ```

   In the example above, the `fetchData` function returns a Promise, and the `processData` function uses the `async` keyword to define an asynchronous function. Inside the function, you can use `await` to pause execution until the Promise is resolved or rejected.

---

**Ans5.** Callbacks are a fundamental concept in JavaScript and are often used to handle asynchronous operations. In simple terms, a callback is a function that is passed as an argument to another function and gets executed once a certain operation or task is completed.

Callbacks are commonly used in scenarios like making AJAX requests, reading files asynchronously, or performing time-consuming tasks. They allow you to specify what should happen after an asynchronous operation finishes.

However, when dealing with multiple nested asynchronous operations, excessive use of callbacks can lead to what is known as "Callback Hell" or "Pyramid of Doom". Callback Hell occurs when you have multiple levels of nested callbacks, making the code difficult to read, understand, and maintain.

Here's an example of Callback Hell:

```javascript
asyncOperation1(function (result1) {
	asyncOperation2(result1, function (result2) {
		asyncOperation3(result2, function (result3) {
			// More nested callbacks...
		});
	});
});
```

In the example above, each async operation relies on the result of the previous operation and is executed within nested callbacks. As the number of operations and nested callbacks increases, the code becomes harder to read, and managing errors and control flow becomes challenging.

Callback Hell can lead to code that is difficult to debug, prone to errors, and hard to extend or refactor. It can hinder code readability and maintainability.

To mitigate the issue of Callback Hell, several alternative approaches have emerged in JavaScript, including Promises, async/await, and the use of libraries like async.js or Bluebird. These approaches provide cleaner and more structured ways to handle asynchronous code and avoid excessive callback nesting.

Promises, for example, allow you to chain asynchronous operations using `.then()` and `.catch()`, resulting in more readable and manageable code:

```javascript
asyncOperation1()
	.then((result1) => asyncOperation2(result1))
	.then((result2) => asyncOperation3(result2))
	.then((result3) => {
		// Code after all operations complete
	})
	.catch((error) => {
		// Handle errors
	});
```

In modern JavaScript, async/await provides an even more concise and synchronous-like way to handle asynchronous code:

```javascript
async function myFunction() {
	try {
		const result1 = await asyncOperation1();
		const result2 = await asyncOperation2(result1);
		const result3 = await asyncOperation3(result2);
		// Code after all operations complete
	} catch (error) {
		// Handle errors
	}
}
```

By utilizing Promises or async/await, you can escape the callback pyramid and write more readable and maintainable asynchronous code.

---

**Ans6.** Promises are an essential feature introduced in ECMAScript 6 (ES6) to handle asynchronous operations and provide a more structured and reliable way to deal with the outcome (success or failure) of an asynchronous task. A Promise represents a value that may be available now or in the future.

A Promise has three states:

1. Pending: The initial state of a Promise. It represents a promise that is still in progress and not yet fulfilled or rejected.

2. Fulfilled: The state of a Promise when it successfully completes its task. The Promise transitions to this state when it resolves with a value.

3. Rejected: The state of a Promise when it encounters an error or fails to fulfill its task. The Promise transitions to this state when it rejects with a reason or an error.

A Promise can have the following three methods to interact with and handle its outcome:

1. `then()`: The `then()` method is used to handle the fulfillment of a Promise. It takes two optional callback functions as arguments: `onFulfilled` and `onRejected`. The `onFulfilled` callback is executed when the Promise is fulfilled, and the `onRejected` callback is executed when the Promise is rejected.

   ```javascript
   myPromise.then(onFulfilled, onRejected);
   ```

   Example:

   ```javascript
   myPromise
   	.then((result) => {
   		// Handle fulfillment
   	})
   	.catch((error) => {
   		// Handle rejection
   	});
   ```

   In the example above, the `then()` method is used to handle the fulfillment and rejection of the `myPromise`. If the Promise is fulfilled, the `result` is passed to the fulfillment handler. If the Promise is rejected, the `error` is passed to the rejection handler.

2. `catch()`: The `catch()` method is used to handle the rejection of a Promise. It is similar to providing only the `onRejected` callback in the `then()` method.

   ```javascript
   myPromise.catch(onRejected);
   ```

   Example:

   ```javascript
   myPromise.catch((error) => {
   	// Handle rejection
   });
   ```

   In the example above, the `catch()` method is used to handle the rejection of the `myPromise`. If the Promise is rejected, the `error` is passed to the rejection handler.

3. `finally()`: The `finally()` method is used to execute code, regardless of whether the Promise is fulfilled or rejected. It allows you to specify cleanup logic that should be executed once the Promise settles (fulfilled or rejected).

   ```javascript
   myPromise.finally(onFinally);
   ```

   Example:

   ```javascript
   myPromise
   	.then((result) => {
   		// Handle fulfillment
   	})
   	.catch((error) => {
   		// Handle rejection
   	})
   	.finally(() => {
   		// Cleanup code
   	});
   ```

   In the example above, the `finally()` method is used to execute the provided callback function, `onFinally`, after the Promise settles (fulfilled or rejected).

---

**Ans7.** The `async` and `await` keywords are part of the ECMAScript 2017 (ES8) update to JavaScript and provide a more elegant and readable way to write asynchronous code. They work together to simplify the handling of Promises, making asynchronous operations appear more like synchronous ones.

1. `async` Keyword:
   The `async` keyword is used to define an asynchronous function. When a function is declared with `async`, it always returns a Promise. The `async` keyword allows the use of the `await` keyword within the function body.

   Example:

   ```javascript
   async function fetchData() {
   	// Asynchronous code using await
   	const response = await fetch("https://api.example.com/data");
   	const data = await response.json();
   	return data;
   }
   ```

   In the example above, the `fetchData` function is declared with the `async` keyword. This allows the use of `await` within the function to pause execution and wait for Promises to resolve before proceeding to the next line of code.

2. `await` Keyword:
   The `await` keyword is used inside an `async` function to pause the execution of the function until a Promise is resolved or rejected. It can only be used within `async` functions.

   Example:

   ```javascript
   async function fetchAndProcessData() {
   	try {
   		const data = await fetchData();
   		// Process the data
   		console.log(data);
   	} catch (error) {
   		console.error("Error:", error);
   	}
   }
   ```

   In the example above, the `await` keyword is used to wait for the `fetchData()` function to complete and resolve its Promise before proceeding to the next line of code. If the Promise is rejected, the code inside the `catch` block will be executed.

Using `async` and `await` together allows you to write asynchronous code that appears more like synchronous code, making it easier to read and understand. The `await` keyword suspends the execution of the function until the awaited Promise settles (either resolves or rejects). It then returns the resolved value or throws an error in case of rejection.

---

**Ans8.** The purpose of the `try` and `catch` block in JavaScript is to handle and manage potential errors or exceptions that may occur during the execution of code. It allows you to gracefully handle exceptional situations and prevent your program from crashing or behaving unexpectedly.

The `try` block:
The `try` block is used to enclose a section of code that might throw an exception. It defines a scope where you anticipate potential errors or exceptional situations. If an error occurs within the `try` block, the execution is immediately transferred to the corresponding `catch` block.

The `catch` block:
The `catch` block follows the `try` block and is used to handle and process the exception that occurred within the `try` block. It contains code that executes when an exception is thrown, allowing you to gracefully handle the error, log useful information, or take appropriate action.

Syntax:

```javascript
try {
	// Code that might throw an exception
} catch (error) {
	// Code to handle the exception
}
```

Example:

```javascript
function divide(a, b) {
	try {
		if (b === 0) {
			throw new Error("Division by zero is not allowed.");
		}
		return a / b;
	} catch (error) {
		console.error("Error:", error.message);
		return NaN;
	}
}

console.log(divide(10, 2)); // Output: 5
console.log(divide(10, 0)); // Output: Error: Division by zero is not allowed. NaN
```

In the example above, the `divide` function attempts to divide two numbers within the `try` block. If the divisor (`b`) is `0`, it intentionally throws an `Error` object. The `catch` block then catches the thrown error and logs the error message. It returns `NaN` as the result to indicate an invalid division.

Why do we need try-catch blocks?

1. Error handling: The primary purpose of `try` and `catch` blocks is to handle and manage errors in a controlled manner. They allow you to catch exceptions, log useful information about the error, and gracefully recover from exceptional situations.

2. Prevent program crashes: When an error occurs within a `try` block, the program flow is redirected to the corresponding `catch` block instead of causing an unhandled exception that could crash the program.

3. Graceful degradation: By catching and handling errors, you can provide fallback behavior or alternative paths when something goes wrong. This ensures that your program continues to run even when unexpected errors occur.

4. Debugging and logging: `try` and `catch` blocks provide a convenient way to capture and log error information. This aids in debugging and troubleshooting by providing insight into what went wrong and where.

---

**Ans9.** In JavaScript, the `fetch` function is a built-in method for making network requests and retrieving resources from a server using the HTTP protocol. It provides a modern and flexible way to perform AJAX (Asynchronous JavaScript and XML) requests and handle responses.

The `fetch` function returns a Promise that resolves to the `Response` object representing the response to the request made. You can use this `Response` object to access and handle the response data, such as reading the response body, checking the status, headers, etc.

Basic usage of `fetch`:

```javascript
fetch(url)
	.then((response) => {
		// Handle response
	})
	.catch((error) => {
		// Handle error
	});
```

Here's how `fetch` can be used and its key aspects:

1. Making a GET request:
   By default, `fetch` makes a GET request to the specified URL. You can pass the URL of the resource you want to retrieve as the first parameter.

   ```javascript
   fetch("https://api.example.com/data")
   	.then((response) => {
   		// Handle response
   	})
   	.catch((error) => {
   		// Handle error
   	});
   ```

2. Handling the response:
   The `fetch` function returns a `Promise` that resolves to a `Response` object. You can use methods on the `Response` object to handle the response, such as extracting the response body using `.json()`, `.text()`, or `.blob()`.

   ```javascript
   fetch("https://api.example.com/data")
   	.then((response) => response.json())
   	.then((data) => {
   		// Handle response data
   	})
   	.catch((error) => {
   		// Handle error
   	});
   ```

3. Sending additional request options:
   You can customize the request by passing an optional second parameter, an object containing additional request options such as headers, request method, request body, etc.

   ```javascript
   fetch("https://api.example.com/data", {
   	method: "POST",
   	headers: {
   		"Content-Type": "application/json",
   	},
   	body: JSON.stringify({ key: "value" }),
   })
   	.then((response) => {
   		// Handle response
   	})
   	.catch((error) => {
   		// Handle error
   	});
   ```

4. Handling errors:
   Any network errors or failed requests will cause the `fetch` Promise to reject. You can use `.catch()` to handle these errors.

   ```javascript
   fetch("https://api.example.com/data")
   	.then((response) => {
   		if (!response.ok) {
   			throw new Error("Request failed");
   		}
   		// Handle successful response
   	})
   	.catch((error) => {
   		// Handle error
   	});
   ```

---

**Ans10.** To define an asynchronous function in JavaScript using the `async` and `await` keywords, follow these steps:

1. Use the `async` keyword:
   Declare the function using the `async` keyword at the beginning of the function declaration. This keyword indicates that the function will perform asynchronous operations and will return a Promise.

   ```javascript
   async function myAsyncFunction() {
   	// Asynchronous code using await
   }
   ```

2. Use the `await` keyword:
   Inside the asynchronous function, use the `await` keyword before any expression that returns a Promise. The `await` keyword pauses the execution of the function until the Promise is resolved or rejected. It allows you to write asynchronous code in a more synchronous-like manner.

   ```javascript
   async function myAsyncFunction() {
   	const result = await myPromise;
   	// Code after the Promise is resolved
   }
   ```

   In the example above, `myPromise` is a Promise that might resolve with a value or reject with an error. The `await` keyword pauses the execution of the function until the Promise settles, and then the resolved value of the Promise is stored in the `result` variable.

3. Handle errors using try-catch:
   To handle any errors that might occur during the execution of the asynchronous function, wrap the `await` statement within a `try` block and use a `catch` block to handle any potential exceptions.

   ```javascript
   async function myAsyncFunction() {
   	try {
   		const result = await myPromise;
   		// Code after the Promise is resolved
   	} catch (error) {
   		// Handle the error
   	}
   }
   ```

   If the Promise is rejected or an exception is thrown within the `await` statement, the execution flow jumps to the `catch` block, where you can handle the error accordingly.

Here's a complete example illustrating the usage of `async` and `await`:

```javascript
async function fetchData() {
	try {
		const response = await fetch("https://api.example.com/data");
		const data = await response.json();
		return data;
	} catch (error) {
		console.error("Error:", error);
		throw error; // Optionally re-throw the error
	}
}
```

In the example above, the `fetchData` function is declared as an asynchronous function. It uses `await` to pause the execution until the `fetch` request is resolved and the response is parsed as JSON. If an error occurs during the request or parsing, it is caught in the `catch` block, where it is logged and optionally re-thrown.

---
