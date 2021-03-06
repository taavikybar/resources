# Resources

[Data Structures](./resources/data-structures.md)

[Algorithms](./resources/algorithms.md)

[Big O](./resources/big-o.md)

## SOLID principles

* S - Single-responsiblity Principle - each function has only one purpose, only one reason to change. only one job.
* O - Open-closed Principle. objects/entities should be open for extension but closed for modification.
* L - Liskov Substitution Principle - an object of subtype has provable property that its parent has. every subclass should be substitutable by its parent. meaning if using a parent as input type and passing in a child class, the method present on the parent and being used, should follow the same signature on the child so that the class using it won't break.
* I - Interface Segregation Principle - client shouldn't depend on methods they do not use or implement interfaces they do not use. means having more custom specific interfaces that can be implemented as needed by a class.
* D - Dependency Inversion Principle - entities should depend on abstractions not concertions (implementations). e.g db connection class can have various implementations and the classes using it should not have to care.

## OSI model

* Open System Interconnection Model - framework to describe the functions of a networking system
* Physical layer - electrically or optically transmitting raw unstructured data across the network between devices. e.g voltages, pin layout, cabling, frequencies, devices, etc.
* Data Link layer - physically connected nodes performing node-to-node data transfer in frames
* Network layer - receiving frames for Data Link layer and delivering them to intended destinations based on logical addresses like IP. crucially routers
* Transport layer - delivery of data packets, most common TCP - Transmission Control Protocol
* Session layer - conversations between computers, connections between computers created, managed, terminated. also auth and reconnections.
* Presentation layer - translates data from Session layer to Application layer, aka syntax layer. also encryption, decryption required by application layer.
* Application layer - end user and Application layer interact with the software, web browsers, apps. identifies communication partners, resource availability and synchronizes communication.


## Node.js architecture

* single threaded event loop
* non-blocking I/O
* request comes in
* worker pool: heavy async operation is sent to an auxiliary thread (I/O, network, image manipulation, big data anaylsis)
* event loop keeps track of the status of async operations
* worker pool implemented in `libuv` - multi-platform async I/O library
* can spawn and manage as many threads as needed.
* threads return their response to event loop when ready, which is then placed on the execution queue or returned to the client
* single thread approach has speed and scalability advantages compared to one-thread-per-request approach
* main thread can be blocked my data heavy operations which therefore should be sent to workers


![](https://cdn.buttercms.com/0Nh1yR6SSPwqnsKYSfHa)


## JS runtime

* Stack - JS uses event based Stack where new frames are created on top of each as code is executed. the frames are then run and removed in LIFO manner until stack is empty
* Queue - JS runtime uses a Queue for messages to be processed which at some point during the event loop start being processed in FIFO manner. messages are added when an event happens via an event listener (if there is no listener, message is lost).
* Event Loop - waits for messages and processes them
* Heap - memory where Objects are stored. what about primitives?
* setTimeout - minimum delay as 2nd argument. if there are no messages in the Queue, the code is run after the delay, otherwise the previous messages need to be processed first.
* Never Blocking - handling I/O is performed by events and callbacks

## JS memory management

* automatic garbage collection that frees up memory once it is not needed anymore
* this is an approximate process cause its hard to determine exactly when a piece of memory is no longer needed

## Web workers

* have their own Stack, Heap and Message Queue. same for iframes.
* 2 distinct runtimes can only communicate via messages via `window.postMessage` method which adds a message to the other runtime if the lattes listens to message events. only by same-origin policy. can use to communicate between browser windows via getting a reference to the window.
* can run code from a file
* cannot modify DOM
* limited access to window
* can spawn new workers

## Websockets

* 2-way interactive communication session between users browser and the server
* can send messages to a server and receive event-driven responses without having to poll the server

## Webhooks

* altering the behavior of a web page with custom callbacks that can be maintained and hosted somewhere else
* usually triggered by some event e.g pushing code to repo, comment on a blog. then the source site makes an HTTP request to the URL configured in the webhook.
* can be used to trigger CI/CD systems, notify bug tracking systems
* use HTTP and therefore can be integrated into web services without any additional infra

## IndexedDb

* client-side storage of significant amounts of structured data
* Web Storage for smaller amounts of data - sessionStorage (not persistent) and localStorage (persistent)
* SQL based RDBMS (relational db mgmt system) but with object-orientation being able to store any object indexed with a key

## difference between `git merge` and `git rebase`?

* `git merge`
	* logs are intact with complete history - can be clumsy log / history
	* easy to find mistakes and resolve them
	* should be used on shared branches
	* can just use squash commits feature to have a single commit when merging
* `git rebase`
	* logs modified after merge. no logs of feature branch retained.
	* therefore cannot track when and how the commits were merged to target branch
	* should be used on private branches
	* main idea is to keep a linear project history because before merging feature branch commits in, the main branch is updated with any new commits done to it. therefore, feature branch commits are chronologically applied later. basically rewriting history cause you are now working from an updated main branch although it wasn't like that when you started.
	* never should be used on public repos on commits that have already been pushed up because others might have based their work on these commits and with rebase you can overwrite them, making this history disappear
* one way is to first rebase and then merge, thereby having up to date main branch to merge into


## Generator functions

* `function*` syntax allows creating iterating functions with non-continuous execution
* when called, returns a Generator with `next()` method returning `{ value: any, done: boolean }`


## `call()`, `bind()`, `apply()`

* `call` executes a function with a given context e.g `func.call(context)` with additional multiple parameters possible
* `apply` same as `call` but takes context and parameters as an array
* `bind` creates a new function with the context set to given context


## Iterations

* `for...of` creates a loop over iterable objects like String, Array, array-like objects (arguments, NodeList), TypedArray, Map, Set and user-defined iterables
* `for...in` iterates of enumerable properties of an object that are keyed by strings ignoring keyed by Symbol including inherited enumerable properties


## Promises

* can have any of three states: `Pending`, `Fulfilled`, `Rejected`
* takes callbacks for `resolve` and `reject` events

## Throttle vs debounce

* `throttle` implementation runs once on event, then waits X amount of time before being able to run again on an event. basically a timed lock is locked upon first execution which after being released is able to accept new event triggers.
* `debounce` delays execution until X amount of time has passed since the last event trigger



