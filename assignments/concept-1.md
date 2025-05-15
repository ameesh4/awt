# Concept Review.

### 1. HTTP Methods

- GET
  The specified resource's representation is requested by the GET method. Only data should be retrieved by GET requests; no request content should be included.
- HEAD
  HEAD request is similar to GET but no response body exist.
- POST
  When an entity is submitted to the designated resource via the POST method, the server frequently experiences side effects or a change in state.
- PUT
  The request content is substituted for all existing representations of the target resource using the PUT method.
- DELETE
  This method is used to request the removable of specified resource.
- CONNECT
  This method create a tunnel to the server identified by the target resource.
- OPTIONS
  This method is used to describe communication criteria for the target resource.
- TRACE
  This method is used to perform a message loop-back along the path to the target resource.
- PATCH
  This method is similar to PUT but only applies partial modification to a specified resource.

### 2. HTTP Response Codes

##### Informational responses

- 100 - Continue.
- 101 - Switching Protocol
- 102 - Processing
- 103 - Early Hit

##### Successful responses

- 200 - OK (Success)
- 201 - Created (Successful resource creation)
- 202 Accepted (May fail after further processing)
- 203 - Non-Authoritative Information
- 204 - No Content
- 205 - Reset Content
- 206 - Partial Content
- 207 - Multi-Status
- 208 - Already Reported
- 226 - IM Used

##### Redirection responses

- 300 - Multiple Choices
- 301 - Moved Permanently
- 302 - Found
- 303 - See Other
- 304 - Not Modified
- 305 - Use Proxy
- 307 - Temporary Redirect
- 308 - Permanent Redirect

##### Client error responses

- 400 - Bad Request
- 401 - Unauthorized
- 403 - Forbidden
- 404 - Not Found
- 405 - Method Not Allowed
- 406 - Not Acceptable
- 407 - Proxy Authentication Required
- 408 - Request Timeout
- 409 - Conflict
- 410 - Gone
- 411 - Length Required
- 412 - Precondition Failed
- 413 - Payload Too Large
- 414 - URI Too Long
- 415 - Unsupported Media Type
- 416 - Range Not Satisfiable
- 417 - Expectation Failed
- 418 - I'm a teapot
- 421 - Misdirected Request
- 422 - Unprocessable Entity
- 423 - Locked
- 424 - Failed Dependency
- 425 - Too Early
- 426 - Upgrade Required
- 428 - Precondition Required
- 429 - Too Many Requests
- 431 - Request Header Fields Too Large
- 451 - Unavailable For Legal Reasons

##### Server error responses

- 500 - Internal Server Error
- 501 - Not Implemented
- 502 - Bad Gateway
- 503 - Service Unavailable
- 504 - Gateway Timeout
- 505 - HTTP Version Not Supported
- 506 - Variant Also Negotiates
- 507 - Insufficient Storage
- 508 - Loop Detected
- 510 - Not Extended
- 511 - Network Authentication Required

### 3. CSS Selectors

CSS selectors are used to "find" (or select) the HTML elements you want to style.

i. Element Selector:
The element selector selects HTML elements to apply css styles on.

```css
h1 {  
	text-align: left;
	color: white;
}
```

ii. Id Selector
The id selector uses the id attribute of a HTML element to apply css styles. It is unique within a page. A # is used a prefix to define an id selector. Example:

```css
#para1 {  
	text-align:left;
	color: white;
}
```

iii. Class Selector.
The class selector uses the class attribute of a HTML element to apply css styles. It can be used multiple times within a document. A dot(.) is used as prefix to define a class selector. Example:

```css
.center  {
  text-align: left;
  color: white;
}
```

iv. Universal Selector.
The universal selector (\*) selects all HTML elements on the page.

```css
* {  
	text-align:left;
	color: blue;
}
```

### 4. Git Basics

1. Initialise a git repository.

```sh
git init
```

After running the above command, git creates a hidden folder(.git) inside the path the command is ran at. Git uses this folder to store necessary information to track changes and sync with remote repository.

2. Staging Changes.

```sh
git add <file> # Stage a file
git add --all or git add -A # Stage all changes
git status # See what is staged
git restore --staged <file> # Unstage a file
```

Staging is used to tell git which files to include in your next commit.

3. Git Commit.

```sh
git commit -m "message" # Commit staged changes with a message
git commit -a -m "message" # Commit all tracked changes (skip staging)
git log # See commit history
```

It records a snapshot of your files at a certain time, with a message describing what changed. It is like a saving point in your project.

4. Pushing Changes.

```sh
git push <branch name> # branch name is optional if default push branch is specified
```

When we have made changes locally, we want to update our remote repository with the changes. Transferring our local changes to our remote is done with a `push` command.
This is used to sync remote repository with local repository.

5. Pull Changes.

```sh
git pull
```

It is used to pull all changes from a remote repository into the branch you are working on. Basically it syncs local repository with remote repository.

6. Git Clone.

```sh
git clone <repository-url>
```

The `git clone` command is used to create a copy of a remote repository on your local machine. It downloads all the files, commit history, and branches from the remote repository. This is typically the first command you use when you want to start working with an existing project. The command creates a new directory with the repository name and initialises a git repository inside it.

7. Git Branch.

```sh
git branch <branch-name> # Create a new branch
git branch # List all local branches
git checkout <branch-name> # Switch to a branch
git checkout -b <branch-name> # Create and switch to a new branch
```

Branches in Git are used to create separate lines of development. They allow you to work on different features or fixes without affecting the main codebase. The main branch is typically called 'main' or 'master'.

### 5. Callback & Higher Order Function.

A callback function is a function that is passed as an argument to another function and is executed after the main function has finished its execution. This pattern is commonly used in asynchronous operations and event handling.

```javascript
function processUser(name, callback) {
  console.log("Processing user: " + name);
  callback();
}

processUser("John", () => {
  console.log("User processing completed");
});
```

Output:

```sh
~/> node callback.js
Processing user: John
User processing completed
```

Higher-order functions are functions that either:

- Take one or more functions as arguments
- Return a function as their result

```javascript
function multiplyBy(factor) {
  return function (x) {
    return x * factor;
  };
}

const multiplyByTwo = multiplyBy(2);
console.log(multiplyByTwo(4));
```

```sh
~/> node higherOrderFunc.js
8
```

In callback-based APIs, the API consumer provides a function that will be executed by the API provider at an appropriate time. The API provider (caller) is responsible for:

- Executing the callback function
- Passing the correct parameters to the callback
- Handling the return value from the callback to determine subsequent actions

### 6. Array Methods.

1. filter.
   The `filter()` method creates a new array with all elements that pass the test implemented by the provided function. It doesn't modify the original array.

```javascript
const numbers = [1, 2, 3, 4, 5, 6];
const evenNumbers = numbers.filter((num) => num % 2 === 0);
console.log(evenNumbers);
```

Output:

```sh
~/> node filter.js
[2, 4, 6]
```

The filter method takes a callback function that should return `true` to keep the element or `false` to exclude it. It's commonly used to select a subset of items from an array based on certain conditions.

2. map.
   The `map()` method creates a new array with the results of calling a function for every array element. It transforms each element in the array without modifying the original array.

```javascript
const numbers = [1, 2, 3, 4, 5];
const doubledNumbers = numbers.map((num) => num * 2);
console.log(doubledNumbers);
```

Output:

```sh
~/> node map.js
[2, 4, 6, 8, 10]
```

The map method takes a callback function that defines how to transform each element. It's commonly used when you need to transform each item in an array into something else.

3. forEach.
   The `forEach()` method executes a provided function once for each array element. Unlike map, it doesn't return a new array and is used when you want to perform an action for each element.

```javascript
const fruits = ["apple", "banana", "orange"];
fruits.forEach((fruit, index) => {
  console.log(`${index + 1}. ${fruit}`);
});
```

Output:

```sh
~/> node forEach.js
1. apple
2. banana
3. orange
```

The forEach method is commonly used when you need to perform side effects (like logging or updating DOM) for each element in an array. It's similar to a traditional for loop but more declarative.

4. push.
   The `push()` method adds one or more elements to the end of an array and returns the new length of the array. It modifies the original array.

```javascript
const fruits = ["apple", "banana"];
fruits.push("orange", "mango");
console.log(fruits);
```

Output:

```sh
~/> node push.js
["apple", "banana", "orange", "mango"]
```

The push method is commonly used to add elements to the end of an array. It can add multiple elements at once and returns the new length of the array.

5. pop.
   The `pop()` method removes the last element from an array and returns that element. It modifies the original array by removing its last element.

```javascript
const fruits = ["apple", "banana", "orange"];
const lastFruit = fruits.pop();
console.log(lastFruit);
console.log(fruits);
```

```sh
~/> node pop.js
orange
["apple", "banana"]
```

The pop method is commonly used when you need to remove and work with the last element of an array. It's the opposite of the push method.
