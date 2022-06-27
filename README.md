# Practice repository

* difference between git merge and git rebase?

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











