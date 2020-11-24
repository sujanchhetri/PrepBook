# Nodejs Questions

1. ### What is Node.js?

    Node.js is a JavaScript platform/runtime built on Google Chrome's JavaScript V8 engine. This allows JavaScript to be used on machines outside of a browser and allows developers to use JavaScript to write things like command-line tools and server-side scripts.
    As a result, Node.js represents the JavaScript everywhere paradigm by unifying web application development around a single programming language, rather than different languages being used on the server and client-side.



2. ### What is Node.js used for?

    Node.js is usually used for non-blocking and event-driven servers.
    This makes it great for building things like static file servers, web application frameworks, REST APIs, messaging middleware, real-time services (chat, games, etc), command-line applications, browser games, and anything else that isn't CPU intensive or doesn't require long processing times.
    Amongst those use-cases, web applications are the most commonly used by developers.



3. ### What language is Node.js written in?

    Node.js works by using the V8 engine to compile JavaScript into native machine code during runtime.
    In order to bind JavaScript code with the V8 engine (written in C++), most of the Node.js code is written in C++. But there are many parts of Node.js that are also written in JavaScript.
    Node.js is open-sourced, so you can check the code for yourself.



4. ### Who was the original author/creator of Node.js? And who works on Node.js now?

    Node.js was initially created by Ryan Dahl in 2009 and was sponsored by Joyent. Today, Node.js is maintained and built by open-source software developers.



5. ### What are the key features of Node.js?

    V8
    Since Node.js compiles JavaScript to machine code using the V8 engine, it allows for high runtime performance (a.k.a it's really fast).

    Single-Threaded Execution
    On the main thread that runs JavaScript, Node.js is single threaded (multiple threads are used under-the-hood by V8). This means Node.js is non-blocking (for the most part), where the majority of the functions (callbacks) are delegated to the event loop and executed asynchronously.

    Asynchronous
    Multiple requests to Node.js can be handled without having any dependency on each other, which boosts both throughput and efficiency.

    Rich Ecosystem Provided By NPM
    The default package manager for Node.js, named NPM, is a command-line utility included by default with Node.js. And it also provides a huge online repository of open-source code to choose from. NPM allows you to search, install, share, and reuse lines of code.

    Full Stack JavaScript Development
    Node.js made it possible for developers to use JavaScript on the server-side. Now, they can use the same scripting language on both the frontend and backed when they build applications. This allows developers to build things faster and reduces the size of the learning curve for developers who are already proficient in JavaScript.



6. ### What are some of the drawbacks with of Node.js?

    The main drawback is that it's not efficient when handling CPU-intensive tasks or any long-running operations. Examples of these types of tasks include generating audio and video or editing graphics.



7. ### What's the name of the JavaScript engine Node.js is built on?

    The V8 engine.



8. ### How does the V8 engine work?

    V8 compiles and executes JavaScript source code into machine code, handles memory allocation for objects, and garbage collects objects it no longer needs. V8 enables any C++ application to expose its own objects and functions to JavaScript code.



9. ### What is the event loop in Node.js?

    The event loop is what allows Node.js to perform non-blocking Input/Output operations by offloading operations to the system kernel whenever possible.

    The main role of the event loop is to schedule which operations the single thread should be performing at any given point in time.

    For more information on how the event loop works.

    Another great source for further reading.



10. ### What is libuv?

    libuv is a multi-platform support library with a focus on asynchronous I/O. It was primarily developed for use by Node.js, but it’s also used by Luvit, Julia, pyuv, and others.

    It is used by the Node.js behind-the-scenes to perform I/O for network and file operations.

    Check out the libuv documentation


11. ### How does Node.js handle child threads?

    Node.js is a single thread process and, by default, doesn't expose child threads and thread management to the developer. Behind the scenes, Node.js does spawn child threads for certain tasks like asynchronous Input/Output operations. But it runs in the background and doesn't execute any application JavaScript code or block the main event loop.

    But, developers to spawn their own external child processes by using tools like the child_process module and worker threads.



12. ### What is the difference between synchronous and asynchronous programming?

    Synchronous: When you execute code synchronously, you wait for it to finish before moving to another task.
    Asynchronous: When you execute code asynchronously, you can move on to another task before it finishes.

13. ### Why is asynchronous programming important in Node.js?

    User interfaces are asynchronous by nature, in that they spend the majority of their time waiting for the user to interrupt the event loop and trigger event handlers.

    Therefore, Node.js is also asynchronous by default and the server works in the same way. It waits for a request from the network and can accept additional incoming requests while the first one is handled. This is very beneficial to performance on the server.



14. ### How do you handle errors when dealing with asynchronous code?

    Return an Error as the First Parameter to a Callback Function
    In Node.js, the standard way to handle errors in asynchronous functions is to return them as the first argument in a function's callback. If the error exists, the first parameter is passed an Error object that contains the information on the error. If there is no error, the first parameter will be null.

    Here is an example of using this in your code:
```javascript
function (error, returnValue) {
  if (error) {
    console.log(error)
    return
  } else {
    console.log(returnValue)
  }
}
```
  As you can see in the example, if there is no error, the callback returns a value of null as the first argument. If an error does exist, the first parameter returns an Error object.

  Use a Try...Catch Statement Inside an Async/Await Function
  Another way to handle errors in asynchronous code is to use an async function with a try...catch statement inside of it that will catch any errors that occur.

  Here's a code example:
```javascript
async function main() {
  try {
    const data = await getData()
    console.log(class="hljs-params">data)
  } catch (error) {
    console.log(error)
  }
}
```
  In the code example, notice that the catch block will handle parsing errors if one occurs in the try block.



15. ### Why is some code considered to be "blocking"?

    Blocking code is when the execution of additional JavaScript in the Node.js process must wait until a non-JavaScript operation completes. This happens because the event loop is unable to continue running JavaScript while a blocking operation is occurring.

    Blocking methods execute synchronously and non-blocking methods execute asynchronously.

16. ### What is process .nextTick() used for?

    In Node.js, each iteration of the event loop is called a tick. The process.nextTick() 

    method is used to defer the execution of a function until the next iteration in the Node.js event loop.

    You can pass a function to the process

    .nextTick()

    like this:
```javascript
process.nextTick(() => {
  // do something here
}
```
  This tells the Node.js engine to call that function at the end of the current operation and before the next event loop tick starts.

  Another way to set code to run in the next iteration of the event loop is to use the setImmediate() function.

  The code looks like this:
```javascript
setImmediate(() => {
  // do something here
})
```
  It's worth noting that a function passed to process.nextTick() is going to be executed on the current iteration of the event loop, after the current operation ends. This means that it will always execute before setImmediate().



17. ### What is event-driven programming?

    Event-driven programming is a paradigm in which the flow of the program is determined by events like user actions (clicks or keypresses) or messages from other programs. In an event-driven application, there's usually a main loop that listens for certain events and triggers a callback function when one of the events is received.



18. ### What is the EventEmitter in Node.js?

    The EventEmitter is a module that facilitates communication/interaction between objects in Node.js. Emitter objects emit named events that cause previously created listeners to be called when they detect the named event.

    It works similar to how a pub/sub or observer design patter does.


19. ### Can you create an HTTP server using Node.js? If so, can you explain the code needed to do so?

    Yes, you can certainly create an HTTP server using Node.js.

    Here is what a basic HTTP server would look like using the HTTP module:
```javascript
const http = require("http")

http.createServer(function (req, res) {
  res.writeHead(200, {"Content-Type": "text/plain"})
  res.write("Hello World!")
  res.end()
}).listen(8080)
```
  When preparing for the interview, it's unlikely that your interviewer expects you to know this code off the top of your head. But, it may be helpful to have a general idea of how one is built and be able to talk through the overall idea of a HTTP server. Being able to talk over different HTTP frameworks you've used in your own projects may be helpful as well.



20. ### What is a control flow function? And what are the steps to execute one?

    The control flow is the order in which the computer executes statements in a script. A control flow function is one that handles or modifies the sequence in which different pieces of code runs. And is often the code that runs between asynchronous function calls.

    To execute a control flow function, these steps should be followed:

    Control the order of execution.
    Collect the required data.
    Limit the concurrency.
    Invoke the next step of the program.

21. ### Does Node.js support multi-core computing platforms? Is it capable of utilizing more than one CPU core?

    A single instance of Node.js runs in a single thread. To take advantage of multi-core systems, the user will sometimes want to launch a cluster of Node.js processes to handle the load.

    The Cluster module allows you to easily create multiple child processes that all share the same server ports.

22. ### Describe what a stream is in Node.js?

    In Node.js, a stream is an abstract interface for working with streaming data in Node.js. Streams are a way to handle network communications, reading/writing files, and any other kind of end-to-end exchange where data is being moved from one place to another.

    If you wanted to create a program that read a file, the conventional way would be to read the file into memory from start-to-finish and then process it. With streams, you can read that file piece by piece and process the file without storing the entire thing in memory.

    For example, in a Node.js based HTTP server, the request is a readable stream and the response is a writable stream. Both involve moving data from one destination to the other.

    Another example can be found with the fs module, which lets you work with both readable and writable file streams.

    The use of streams provides two key advantages:

    Uses less memory: since only chunks of data are stored in memory, you use a lot less computing resources.
    Takes less time to process data: since you can start processing the data right away (instead of waiting until all the data has been received), lots of time is saved.


23. ###  How many types of streams exist in Node.js?

    Three are four different types of streams in Node.js:

    Writable: streams to which data can be written to.
    Readable: streams from which data can be read from.
    Duplex: streams that are both Writable and Readable.
    Transform: Duplex streams that can modify the data as it's written or read.

24. ### What kind of events can be fired by a stream?

    Each type of stream in Node.js is an EventEmitter instance and can throw several types of events at different times.

    These are the commonly used ones:

    data: fired whenever data is available to be read.
    end: fired when there is no more data to be read.
    error: fired when there is an error when receiving or writing data.
    finish: fired when all the data has been flushed to the underlying system.


25. ### What's piping in Node.js?

    In Node.js, piping is used when dealing with streams. And is the name for the method used to connect a readable stream to a writeable stream. This is a common method when dealing with file streams using the stream.pipe function.


26. ### What's the purpose of the Buffer class in Node.js?

    A buffer represents a chunk of memory allocated outside of the V8 JavaScript engine. And can be thought of as an array of integers where each value represents a byte of data.

    In essence, a buffer serves as a temporary place in memory where data can be dumped and used for further processing.

    The Buffer class was introduced as part of the Node.js API to enable interaction with octet streams in TCP streams, file system operations, and other contexts.


27. ### What's the difference between readFile() and createReadStream() in Node.js?

    readFile(): the file is completely pushed into the buffer for processing and returns the response only when the entire has been pushed into the buffer and read. It uses a lot of memory and can be very slow when handling large files.
    createReadStream(): the is pushed into the buffer in chunks and each chunk is removed when it has been processed. The file is sent in chunks and once the process of one chunk is done, it sends a response and removes it from the buffer. This is more effective and memory efficient when dealing with larger files.


28. ### What general practices do you use for debugging when building Node.js applications?

    For this question, explain some debugging methods you have used in the past. These may be specific to you, but you can talk about some general topics such as these:

    The Built-In Debugger
    The Node.js debugger is a built-in way to debug an application. It exposes a debugger statement that you can place in your source code to cause your code to break at certain points. You must run your Node.js application in debug mode for this to work (node debug your-app).

    It would look similar to this in your code:

```javascript
setTimeout(() => {
  debuggerconsole.log("world")
}, 1000)

console.log("hello")
```
  When you run that code with the debug flag, it will expose a command-line interface that allows you to inspect your code.

  Node Inspector
  The Node Inspector is an NPM package that provides a debugger interface for Node.js applications.

  You can talk about using this tool or one of the many others for debugging.

  Creating Tests
  By creating extensive tests for your application, you will form a great understanding of how your application works and it will make the process of finding bugs easier when they occur.



29. ### What keyword can you insert into your code to act as a debug breakpoint?

    The Node.js debugger is a built-in way to debug an application. It exposes a debugger statement that you can place in your source code to cause your code to break at certain points. You must run your Node.js application in debug mode for this to work (node debug your-app).

    It would look similar to this in your code:
```javascript
setTimeout(() => {
  debuggerconsole.log("world")
}, 1000)

console.log("hello")
```
  When you run that code with the debug flag, it will expose a command-line interface that allows you to inspect your code.



30. ### What's the difference between programmer and operational errors?

    Operational Errors
    Operational errors are run-time problems experienced by correctly-written programs. These are not necessarily bugs in the program and are usually problems caused by something with the system itself, the system's configuration, the network, or a remote service.

    Some specific examples include:

    failed to connect to server
    ailed to resolve hostname
    server returned a 500 response
    system is out of memory
    Programmer Errors
    Programmer errors are bugs in the program and are caused by the developer. These are things that can be fixed by changing the code.



31. ### What are callbacks used for in Node.js?

    Node.js APIs make heavy use of callback functions. A callback is a function passed as an argument to another function that will be called when the function ends. It is an asynchronous equivalent for a function and is called at the completion of a given task.



32. ### What is the first argument passed to a Node.js callback function?

    The error object.

    If an error occurred, it will be returned by the first error argument. And the second argument of the callback is usually reserved for successful response data.



33. ### What is a Promise?

    A promise is an object that may produce a single value at some point in the future and represents the result of an asynchronous function. That value can be either a resolved value or a reason for why it wasn't resolved (an error).

    A promise can be in three different states:

    pending
    fulfilled
    rejected
    Callbacks can be attached to the promise to handle the fulfilled value or any rejection reasons.


34. ### What is an async function? Why is it used?
    An aync function is one that operates asynchronously via the event loop and uses a Promise to return its result. These are declared using the async function syntax.

    An async function can use the await expression to pause the execution of the asynchronous function and wait for the Promise to resolve (only the async function block waits, not the execution thread). Then it resumes the async function's execution and evaluates as the resolved value.

    Here's an example of what one looks like in code:

```javascript
async function main() {
  try {
    const data = await getData()
    console.log(data)
  } catch (error) {
    console.log(error)
  }
}
```
    The purpose of an async function is to enable developers to write promise-based code as if it were synchronous, but without blocking the execution thread.



35. ### What is callback hell?

    Callback hell is a JavaScript anti-pattern caused by deeply nested asynchronous functions. Callback hell happens when you have callbacks within callbacks within callbacks and your code becomes difficult if not impossible to reason about.



36. ### How do you prevent or fix callback hell?

    The most important way to avoid callback hell is to move functions out of the way so that the program can be more easily understand without wading through miles of functions and their callbacks.

    Here are some other methods of preventing callback hell are:

    Don't nest functions, give them names, and place them at the top of your program.
    Utilize function hoisting to move functions out of the way.
    Handle every error in each of your callbacks.
    Modularize your code by creating reusable functions and placing them in their own module.



37. ### What is NPM?

    NPM is the default package manager for Node.js and servers as the world's largest software registry. Open source developers from every continent use npm to share and borrow packages, and many organizations use npm to manage private development as well.



38. ### What functionalities does NPM provide when building Node.js applications?

    NPM consists of a command-line client and an online database of public and paid private packages called the NPM registry. The registry is accessed via the client, and the available packages can be browsed and searched via the NPM website.



39. ### What's the difference between NPM packages and Node.js core modules?

    Node.js core modules provide the bare minimum functionalities of Node.js. They are compiled into the binary distribution of Node.js and load automatically when the Node.js process starts. Therefore, they can be imported directly into your Node.js code without installing anything.

    On the other hand, NPM packages is code that can be imported into a Node.js application via the NPM registry. These need to be installed via the NPM command-line utility.



40. ### What is a global installation of a NPM dependency?

    An NPM dependency that is installed globally on your machine will be stored in a single place in the system, no matter where you run the installation script. The destination for the packages will depend on your OS, deployment, or configuration settings.

    But, you won't be able to import global packages into a Node.js application directly.

    You can install Node.js packages globally by adding the -g flag to the npm install command.



41. ### What is a local dependency of a NPM dependency?

    NPM packages installed locally will be installed to the node_modules directory for a given Node.js application. These packages can be imported directly into the Node.js application it was installed for.

    This is the default behavior for installing NPM packages and, therefore, you don't need to add any flags to the npm install command.



42. ### How do you update NPM to a new version in Node.js?

    You can update NPM to the latest version by using this command: npm install -g npm@latest.



43. ### What is the most popular alternative to NPM? What are its benefits?

    Yarn is a popular alternative to NPM.

    Many have reported that Yarn provides much faster installation times compared to NPM due to it's caching mechanisms. And it also makes security a core value by using checksums to verify the integrity of every installed package before its code is executed.



44. ### What's a package.json file? And what is it used for?

    The package.json file holds the various metadata relevant to a Node.js project. It gives information to NPM that allows it to identify the project as well as handle its dependencies.

    It can also hold other types of metadata such as a project description, the version of the project, license information, and even configuration data. It is usually stored in the root directory of a Node.js application.



45. ### What's a package-lock.json file? And why is it used?

    The package-lock.json file is automatically generated for any operations where NPM modifies either the node_modules directory or the package.json file. It describes the exact tree that was generated, such that subsequent installs can generate identical trees, regardless of intermediate dependency updates.

    It serves several purposes:

    Ensures that teammates, deployments, and continuous integration are guaranteed to install exactly the same dependencies.
    Provides a facility for users to "time-travel" to previous states of node_modules without having to commit the directory itself.
    Facilitates more visibility to tree changes through readable source control diffs.
    Optimizes the installation process by allowing NPM to skip repeated metadata resolutions for previously-installed packages.



46.  ### How do you update a dependency using NPM?

    You can update one or multiple NPM dependencies using the npm update app-name command.



47. ### What's the difference between a dependency and a devDependency in the package.json file?

    The devDependencies are modules that are only required during the development process. And dependencies are modules that are required at runtime.



48. ### What are exit codes in Node.js?

    Node.js will normally exit with a 0 status code when no more async operations are pending. There are other codes used in different circumstances.

    Some examples include:

    1 - Uncaught Fatal Exception: There was an uncaught exception, and it was not handled by a domain or an event handler.
    3 - Internal JavaScript Parse Error: The JavaScript source code internal in Node's bootstrapping process caused a parse error.
    4 - Internal JavaScript Evaluation Failure: The JavaScript source code internal in Node's bootstrapping process failed to return a function value when evaluated.



49. ### What is REPL in Node.js?

    Node.js comes with a virtual machine called REPL, which is also called the Node shell. REPL stands for Read-Eval-Print-Loop and the virtual environment can be used as a quick and easy way to test simple Node.js code.



50. ### Why is it important to maintain a consistent coding style across a Node.js project?

    Inconsistent code can cause problems if your code is very interconnected with legacy code or if it's part of a much large library. And it could also cause problems if a lot of people work on your codebase and, therefore, many different people need to understand it and work on it.

    Maintaining a consistent coding styling will help mitigate any of those potential problems.



51. ### What tools can be used to assure it?

    You can use JavaScript IDE's like VS Code that will help you format your code by default. And you can also use packages like ESLint that let you configure a set of formatting rules for your code and enforces them during testing and deployment processes.



52. ### What purpose does a .env file serve?

    The .env file is used for storing any environment variables used for a Node.js project.

    Environment variables are used to store sensitive information like API keys and passwords and can be used to easily handle those variables globally across an entire Node.js application.

    The .env file is usually stored in the root directory for an application and shouldn't be committed to the source code repository because it often contains sensitive information like passwords and usernames.

    In order to use the variables declared in the .env file, you'll need to use some type of loader. We have an article that goes over how to do that.



53. ### What are the differences between the setTimeout() & setInterval() functions?

    setTimeout()
    The setTimeout() function lets you run a function once after an interval of time has elapsed (specified by the developer).

    Here's a code example:

```javascript
setTimeout(() => {
  console.log("Hello!")
}, 1000)
```
  The message will be logged after the 1000 milliseconds time interval has elapsed.

  setInterval()
  The setInterval() function lets you run a function repeatedly, starting after an interval of time has elapsed (specified by the developer), and then repeating continuously at that interval.

  Here's a code example:

```javascript
setInterval(() => {
  console.log("Hello!")
}, 5000)
```
  This will first wait for 5000 milliseconds and then log the message after every subsequent 5000 milliseconds have passed.

  It's dangerous to use the setTimeout() function for shorter time periods. You should only use it for longer periods to avoid getting backed up.



54. ### How do you create a directory using Node.js?

    Node.js has an Fs core module that provides an fs.mkdir() function that makes creating a new directory or folder an easy process.

  The code would look something like this:

```javascript
const fs = require("fs")
fs.mkdir("./new-directory-name", class="hljs-function">(err) {
  if (err) {
    console.log(err)
  } else {
    console.log("New directory successfully created.")
  }
})
```
  That function would result in a new directory called new-directory-name being created.

  It's also worth noting that fs.mkdir() doesn't create nested or dependent directories in it's default state.


55. ### How do you delete a directory?

    Node.js has an Fs core module that provides an fs.rmdir() function that allows you to delete an empty directory.

    If you want to delete a directory that contains files or other sub-directories, you'll need to recursively go through and remove all the individual files first. There are NPM packages that handle this for you, such as rimraf.



56. ###  How would you read the contents of a directory?

    Node.js has an Fs core module that provides an rgb(65, 66, 69);">fs.readdir() function that makes it easy to read the contents of a specified directory.

    It would be used in your code like this:

```javascript
const path = require("path")
const fs = require("fs")

const directoryPath = path.join(__dirname, "files")

fs.readdir(directoryPath, function(err, files) {
  if (err) {
    console.log("Error getting directory information.")
  } else {
    files.forEach(function(file) {
      console.log(file)
    })
  }
})
```
  The results will be both files and directories, so you'll need fs.stat() to differentiate between which is which.




57. ### What is the preferred method of solving unhandled exceptions in Node.js?

    Process is a global object that provides information about the current Node.js process that is being used by your application. And it is also a listener function that listens for certain events to occur.

    Some of those events include:

    exit
    disconnect
    uncaughtException
    rejectionHandled
    You can write your own code to detect when the unhandledException event has been fired and handle the error safely:
```javascript
class="ql-syntax" spellcheck="false">process.on("uncaughtException", function(err) {
  // handle the errorconsole.log(err)
})
```




58. ### Can you name some programming paradigms that are important for Node.js developers?

    Four important programming paradigms:

    Functional Programming
    Object-Oriented Programming
    Procedural Programming
    Imperative Programming

59. ### Can you describe what functional programming is?

    Functional Programming is a programming paradigm where you structure your code using mostly functions. These functions take inputs (called arguments) and show the output based on those inputs provided to the function.

    It also doesn't allow any mutation or shared state and the functions are intended to stay pure to their expression and avoid side-effects.

    Examples of functional programming languages include Lisp, Haskell, Erlang, Clojure, and Elm.

    Some features of the functional programming paradigm include first-class citizen functions, higher-order functions, and function composition.

    The main benefit of using functional programming is that it doesn't involve a lot of side-effects and is immutable, which reduces the chances that your code will create hard to track down bugs. And your code will be more clean, straightforward, and succinct.



60. ### What is object-oriented programming?

    Object-oriented programming is a coding paradigm where you use objects to model real-world things that you want to represent inside your application. And it provides a simple way to access functionality that would otherwise be hard or impossible to make use of.


61. ### What are the pros and cons between these two paradigms: functional programming and object-oriented programming?

    Object-Oriented Programming
    Pros:

    The basic concepts behind objects and method calls are easy to understand for developers.
    The imperative style (rather than declarative) reads like a more straight forward set of instructions for the computer to follow.
    Cons:

    Objects and behaviors are tacked together to the same entity and often use a shared state. This means they can be accessed at random by other functions in a non-deterministic order, which could lead to undesirable behavior such as race conditions.
    Functional Programming
    Pros:

    In the functional paradigm, sharing state and/or side-effects is avoided. This eliminates the potential for bugs to arise from the same functions using the same resources.
    Programs that use pure functions are typically easier to scale to multiple additional processors or across distributed clusters without race condition or threading resource issues.
    Functional programming usually uses the declarative style, which does not give step-by-step instructions for operations. They instead focus on what to do and let the underlying functions figure out how to do it. This leaves a lot of room for refactoring and performance optimization.
    Cons:

    Using functional programming styles in your code too much can potentially lead to reduced readability because the resulting code is often abstract, more terse, and less concrete.
    More people are familiar with the object-oriented programming style, so common ideas in functional programming may be confusing to new teammates.




62. ### What is a pure function?

    Pure functions don't produce any side-effects and can't alter any state external from itself. Given the same input, they should always return the same output.

    Not every function can be pure, but its often a good choice when they can be.


63. ###  What is function composition?

    Function composition is the process of combining more than one function to produce a new function.


64. ### What's the difference between the two types of inheritance: prototypal & classical?

    Classical Inheritance
    These inherent from a class and create sub-class relationships called hierarchical class taxonomies. Instances are usually created using a constructor function with the new keyword.

    Class inheritance might or might not use the class keyword from ES6.

    It's also worth noting that classical syntax in JavaScript serves as mostly sugar over prototypal inheritance, which is what's actually used in practice for JavaScript. This is because deeply nested heirarchies over large sets of object/class syntax can have negative effects on performance.

    Prototypal Inheritance
    These inherit directly from another object and are usually created using factory functions or the Object.create() method. Instances can be composed of many different methods.



65. ### What is a Closure?

    A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). In other words, a closure gives you access to an outer function’s scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time.

    Closures are important because they control what is and isn’t in scope in a particular function, along with which variables are shared between sibling functions in the same containing scope. Understanding how variables and functions relate to each other is important in understanding how your code works.

    You can use a closure by defining a function inside another one and then expose it by returning or passing it to another function. The inner function will then have access to the variables in the outer function scope.

    Starting with the release of ES6, you can now create a closure with loops and objects where let and const are scope to the closure. Here's an article on the subject.


66. ### What are some common uses for closures?

    Closures are useful because they let you associate data with a function that operates on that data. This has obvious parallels to object-oriented programming, where objects allow us to associate some data (the object's properties) with one or more methods.

    Some use cases for closures include event handlers, callbacks, intervals, timeouts, and keeping variables private within a given function.

    Closures have the chance of causing an over-consumption of memory and/or memory leaks if they're not handled correctly.


67. ### What's Git used for?

    Git is a free and open-source distributed version control system.

    In other words, it's an application that keeps track of your code and all the changes that have been made to it in the past. Also, it allows you to share your code with others and collaborate on it without overwriting each other's changes.


68. ### What's a reverse proxy?

    A reverse proxy is a type of web server that takes requests, forwards them to another HTTP server somewhere else, receives a reply, and then forwards the data to the original requestor.



69. ### What are the benefits of using a reverse-proxy (with Nginx or Apache) for a Node.js application?

    There are several benefits:

    SSL termination: Handling SSL termination (changing HTTP to HTTPS) directly in your Node.js app can be tedious and expose security risks. When only a reverse proxy is allowed to perform SSL termination, only the reverse proxy has access to the SSL certificate. Without a reverse proxy, all the code in your application (including 3rd party modules) will have access to your certificates.

    Clustering: Node.js comes with it's built-in Cluster modules which can run applications on more than one process. But using software like Nginx to run a reverse proxy is often more efficient and uses less cache than a Node.js solution.

    Gzip compression: Off-loading gzip compression from your application to the reverse proxy can allow you to have the same compression logic at the organization level, instead of having to configure it for each application.

    Performance benefits: SSL encryption, clustering, and gzip compression are high CPU-bound operations. Dedicated reverse proxy tools (like Nginx) usually perform those tasks faster than Node.js.

    Simplified application code: Using a reverse proxy allows your application to focus on business logic and not about protocols and process management. As a result, your code will be simplified greatly.



70. ### What's the difference between SQL & NoSQL databases?

    SQL: a relational database management system, is vertical scalable, has fixed schema, is not suitable for hierarchical data storage, and can be used for complex queries.
    NoSQL: a distributed database management system, horizontally scalable, has a dynamic schema, is best suitable for hierarchical data storage, and is not good for complex queries.

71. ### What's the difference between declaring a variable with const, var, or let?

    let: means the variable may be reassigned (used for things like a counter in a loop or a value swap in an algorithm).
    const: means that the identifier can't and won't be reassigned.
    var: means that the variable may or may not be reassigned and it may or may not be used for an entire function


72. ### What's the difference between the null, undefined, and undeclared variable values?

    null: is a value of a variable and is a type of object.
    undefined: is a variable that has been declared but no value exists for it.
    undeclared: is a variable that has been declared without the var, let, or const keyword.

73. ### What are some of the most popular Node.js packages you know of?

    This answer can be unique to what you've used in the applications you've built. But below are some ideas for what you could respond with:

    Express: A Node.js web application server framework, designed for building single-page, multi-page, and hybrid web applications. It is the standard server framework for node.js.

    Request: Request is designed to be the simplest way possible to make HTTP calls.

    Browserify: Browserify lets you require("modules") in the browser by bundling up all of your dependencies.

    PM2: PM2 is a production process manager for Node.js applications with a built-in load balancer. It allows you to keep applications alive forever, to reload them without downtime and to facilitate common system admin tasks.

    Cheerio: A fast, flexible, and lean implementation of JQuery designed for use on the server.

    Passport: Passport is authentication middleware for Node.js. Extremely flexible and modular, Passport can be unobtrusively dropped into any Express-based web application.
    Nodemailer: Makes it easy to send emails from Node.js.

74. ### What's the purpose of the console object?

    In Node.js, console is a global object used for printing different levels of messages to stdout and stderr. It also includes built-in ways to print informational, warning, and error messages.

    Here are the two most used methods provided by the console object and their key differences:

    console.log(): writes to stdout, buffered, and asynchronous
    console.error(): writes to stderr, synchronous, and blocking
    Here's some code examples for both:

```javascript
console.log("Hello")
// Prints: Hello, to stdoutconsole.error(new Error("Error occurred!"))
// Prints: [Error: Error occurred!], to stderr
```

75. ###  What is the purpose of module.exports in Node.js?

    The module.exports takes a JavaScript code file and exposes it to other files so they can import those functions or variables. Whatever variable or function you assign with module.exports or 

    exports will be exposed as a module for other files.



76. ### How would you describe a monolithic application architecture?

    A monolithic architecture means an app is built as one cohesive unit of code that has components that are designed to work together and share the same resources.



77. ### How would you describe a microservice application architecture?

    A microservice architecture means an app is made up of lots of smaller, independent applications capable of running with their own resources and can scale independently from each other across multiple machines.



78. ### What are the pros and cons between a microservice and monolithic architecture?

    Monolithic
    Pros:

    When everything is running through the same application, it's easy to hook up components to those cross-cutting concerns.
    Shared-memory access is faster than inter-process communication, therefore there can be performance advantages.

    Cons:
    These applications tend to get entangled as the application evolves, which makes it hard to isolate different services.
    Monolithic architectures become harder to understand the larger they get because of dependencies, side-effects, and magic that are now obvious unless you look at a specific part of the codebase.
    
    Microservice
    Pros:
    Since each service is modularized and has its own specific job, microservice architectures are usually organized better.
    They can result in better performance because you can isolate specific services and scale them individually from the rest of the application.
    
    Cons:
    Testing can be difficult since each service is running in its own environment.
    Deployment complexity will be increased and the operational cost of deploying and managing the multiple services and systems will be increased as well.

79. ### Walk us through an application you've built?

    Be prepared to walk-through an application you've listed on your resume. Make sure you can talk about the following:

    The technologies you used to build the application (packages, testing frameworks, etc).
    If you were part of a team, what role you had in building the application.
    Explain both what design decisions you made and why they were made.
