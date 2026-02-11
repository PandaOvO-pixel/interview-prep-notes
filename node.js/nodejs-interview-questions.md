# Node.js Interview Questions & Answers

## 1. What is Node.js?

**Answer:** Node.js is an open-source, cross-platform JavaScript runtime environment that executes JavaScript code outside a web browser (built on Chrome's V8 engine).

**Key Features:**
- **Asynchronous & Event-Driven:** Non-blocking I/O operations
- **Single-Threaded:** Uses event loop for concurrency
- **Fast:** V8 engine compiles JS to machine code
- **NPM:** Large package ecosystem
- **Cross-Platform:** Runs on Windows, Linux, Mac

**Why Node.js:**
- JavaScript on both frontend and backend
- High performance for I/O operations
- Real-time applications
- Microservices architecture

---

## 2. What is the difference between Node.js and JavaScript?

**Answer:**

| Feature | JavaScript | Node.js |
|---------|-----------|---------|
| Type | Programming language | Runtime environment |
| Execution | Browser | Server |
| DOM | Can access | No DOM access |
| Global | `window` object | `global` object |
| File System | No access | Can access (fs module) |
| Purpose | Client-side | Server-side |

---

## 3. Explain Event Loop in Node.js.

**Answer:** Event Loop is a mechanism that handles asynchronous operations in Node.js by continuously checking and executing callbacks.

**Phases (in order):**
1. **Timers:** Executes setTimeout/setInterval callbacks
2. **Pending Callbacks:** I/O callbacks deferred to next iteration
3. **Idle, Prepare:** Internal use
4. **Poll:** Retrieve new I/O events
5. **Check:** setImmediate callbacks
6. **Close Callbacks:** Socket close events

**How it works:** Single thread processes requests while delegating blocking operations to system kernel/thread pool.

**Interview Tip:** Node.js is single-threaded but handles thousands of concurrent connections efficiently through event loop.

---

## 4. What is the difference between Asynchronous and Synchronous?

**Answer:**

**Synchronous (Blocking):**
- Operations execute sequentially
- Next operation waits for current to complete
- Blocks execution thread

**Asynchronous (Non-Blocking):**
- Operations execute independently
- Doesn't wait for completion
- Uses callbacks/promises/async-await
- Better performance

**Node.js Focus:** Primarily asynchronous for I/O operations.

---

## 5. What is Callback Hell and how to avoid it?

**Answer:** Callback Hell (Pyramid of Doom) is nested callbacks making code hard to read and maintain.

**Problems:**
- Difficult to read
- Hard to debug
- Error handling complex
- Maintainability issues

**Solutions:**

**1. Promises:**
- Chainable `.then()` and `.catch()`
- Better error handling

**2. Async/Await:**
- Synchronous-looking code
- Try-catch for errors
- Most modern approach

**3. Modularization:**
- Break into named functions
- Separate concerns

---

## 6. What are Promises in Node.js?

**Answer:** Promises represent eventual completion or failure of asynchronous operation.

**States:**
- **Pending:** Initial state
- **Fulfilled:** Operation completed successfully
- **Rejected:** Operation failed

**Methods:**
- `.then()` - Handle success
- `.catch()` - Handle errors
- `.finally()` - Always executes

**Advantages:**
- Better than callbacks
- Chainable
- Better error handling
- Avoids callback hell

---

## 7. What is async/await?

**Answer:** Async/await is syntactic sugar over promises for writing asynchronous code that looks synchronous.

**async:**
- Declares asynchronous function
- Always returns promise

**await:**
- Pauses execution until promise resolves
- Only works inside async functions
- Makes code cleaner

**Error Handling:** Use try-catch blocks

**Interview Tip:** Async/await is built on promises, not a replacement. Makes promise-based code cleaner.

---

## 8. What is NPM?

**Answer:** NPM (Node Package Manager) is the default package manager for Node.js.

**Features:**
- Install packages and dependencies
- Manage project dependencies
- Publish packages
- Version management
- Scripts execution

**Key Commands:**
- `npm install` - Install dependencies
- `npm init` - Initialize project
- `npm update` - Update packages
- `npm run` - Run scripts
- `npm publish` - Publish package

**Files:**
- **package.json:** Project metadata and dependencies
- **package-lock.json:** Exact dependency tree

---

## 9. What is the difference between package.json and package-lock.json?

**Answer:**

**package.json:**
- Project metadata
- Dependencies with version ranges
- Scripts
- Manually editable

**package-lock.json:**
- Exact dependency versions
- Dependency tree
- Auto-generated
- Ensures consistent installs
- Should be committed to version control

**Interview Tip:** package-lock.json ensures same versions installed across all environments.

---

## 10. What is Middleware in Node.js?

**Answer:** Middleware are functions that have access to request, response objects and next middleware function in request-response cycle.

**Purpose:**
- Execute code
- Modify request/response
- End request-response cycle
- Call next middleware

**Types:**
- **Application-level:** app.use(), app.get()
- **Router-level:** router.use()
- **Error-handling:** 4 parameters
- **Built-in:** express.json(), express.static()
- **Third-party:** body-parser, cors, morgan

**Execution:** Sequential order matters.

---

## 11. What is Express.js?

**Answer:** Express.js is a minimal and flexible Node.js web application framework.

**Features:**
- **Routing:** Define URL endpoints
- **Middleware:** Request processing pipeline
- **Template Engines:** Dynamic HTML (Pug, EJS)
- **HTTP Methods:** GET, POST, PUT, DELETE
- **Static Files:** Serve CSS, images, JS

**Benefits:**
- Simplifies Node.js development
- Large community
- Many plugins/middleware
- Unopinionated (flexible)

---

## 12. What is the difference between req.params, req.query, and req.body?

**Answer:**

**req.params:**
- URL parameters (route parameters)
- Example: `/user/:id` → `req.params.id`

**req.query:**
- Query string parameters
- Example: `/search?name=john` → `req.query.name`

**req.body:**
- Data from POST/PUT request body
- Requires body parser middleware
- Example: Form data, JSON payload

---

## 13. What is the Event Emitter in Node.js?

**Answer:** EventEmitter is a class that facilitates communication between objects in Node.js (Publish-Subscribe pattern).

**Key Methods:**
- **on():** Register listener
- **emit():** Trigger event
- **once():** One-time listener
- **removeListener():** Remove listener

**Use Cases:**
- Custom events
- Modular architecture
- Asynchronous flows
- Stream handling

**Interview Tip:** Many Node.js core modules inherit from EventEmitter (streams, http server).

---

## 14. What are Streams in Node.js?

**Answer:** Streams are objects that let you read/write data piece by piece (chunks) instead of all at once.

**Types:**
1. **Readable:** Read data (fs.createReadStream)
2. **Writable:** Write data (fs.createWriteStream)
3. **Duplex:** Both read and write (TCP socket)
4. **Transform:** Modify data while reading/writing (compression)

**Benefits:**
- Memory efficient (process large files)
- Time efficient (start processing before loading complete data)

**Use Cases:**
- File operations
- HTTP requests/responses
- Data compression

---

## 15. What is Buffer in Node.js?

**Answer:** Buffer is a temporary storage area for binary data (raw memory allocation outside V8 heap).

**Purpose:**
- Handle binary data
- Work with TCP streams
- File system operations
- Image/video processing

**Creation:**
- `Buffer.from()` - From string/array
- `Buffer.alloc()` - Allocate specific size

**Interview Tip:** Buffers necessary because JavaScript traditionally only handled strings, not binary data.

---

## 16. What is the difference between require() and import?

**Answer:**

| Feature | require() | import |
|---------|----------|--------|
| Type | CommonJS | ES6 Modules |
| Loading | Synchronous | Asynchronous |
| Usage | Can be called anywhere | Top-level only |
| Dynamic | Yes | Limited |
| Node.js | Native support | Supported (with .mjs or "type": "module") |

**Trend:** ES6 modules (import) becoming standard.

---

## 17. What is REPL in Node.js?

**Answer:** REPL (Read-Eval-Print-Loop) is an interactive shell for executing JavaScript code.

**Components:**
- **Read:** Reads user input
- **Eval:** Evaluates code
- **Print:** Prints result
- **Loop:** Repeats process

**Usage:** Type `node` in terminal

**Use Cases:**
- Test JavaScript code
- Debug
- Learn Node.js
- Quick calculations

---

## 18. What is Cluster Module?

**Answer:** Cluster module allows creating child processes (workers) that share same server port.

**Purpose:**
- Utilize multi-core systems
- Load balancing
- Improve performance
- High availability

**How it works:**
- Master process forks worker processes
- Workers share server port
- If worker dies, master spawns new one

**Interview Tip:** Node.js is single-threaded, but clustering helps utilize multiple CPU cores.

---

## 19. What is the difference between process.nextTick() and setImmediate()?

**Answer:**

**process.nextTick():**
- Executes before event loop continues
- Higher priority
- Can block event loop if overused

**setImmediate():**
- Executes in next iteration of event loop
- Check phase
- Better for async operations

**Recommendation:** Use setImmediate() for async callbacks to prevent I/O starvation.

---

## 20. What is the purpose of module.exports?

**Answer:** module.exports is used to export functions, objects, or values from a module to be used in other files.

**Related:** `exports` is shorthand (alias) for `module.exports`

**Caution:** Reassigning `exports` breaks reference. Always safe to use `module.exports`.

**Export types:**
- Single function/class: `module.exports = MyClass`
- Multiple: `module.exports = { func1, func2 }`

---

## 21. What is JWT Authentication?

**Answer:** JWT (JSON Web Token) is a compact token for securely transmitting information between parties.

**Structure:**
1. **Header:** Algorithm and token type
2. **Payload:** Claims (user data)
3. **Signature:** Verify authenticity

**Flow:**
1. User login with credentials
2. Server generates JWT
3. Client stores token
4. Client sends token with requests
5. Server verifies token

**Benefits:**
- Stateless
- Scalable
- Cross-domain
- Self-contained

---

## 22. What is REST API?

**Answer:** REST (Representational State Transfer) is an architectural style for designing networked applications.

**Principles:**
- **Stateless:** Each request independent
- **Client-Server:** Separation of concerns
- **Cacheable:** Responses can be cached
- **Uniform Interface:** Standard HTTP methods

**HTTP Methods:**
- GET: Retrieve data
- POST: Create data
- PUT: Update data
- DELETE: Delete data

---

## 23. What is CORS?

**Answer:** CORS (Cross-Origin Resource Sharing) is a security feature that controls resource sharing between different domains.

**Problem:** Browsers block requests from different origins by default (security).

**Solution:** Server must explicitly allow cross-origin requests.

**Implementation:** Use `cors` middleware in Express

**Headers:**
- Access-Control-Allow-Origin
- Access-Control-Allow-Methods
- Access-Control-Allow-Headers

---

## 24. What is Error Handling in Node.js?

**Answer:**

**Synchronous:**
- Try-catch blocks
- Throws errors

**Asynchronous:**
- Callbacks: Error as first parameter
- Promises: `.catch()` method
- Async/await: Try-catch blocks

**Best Practices:**
- Always handle errors
- Use error middleware in Express
- Log errors
- Don't expose internal errors to clients
- Use proper HTTP status codes

---

## 25. What is the difference between Spawn and Fork?

**Answer:**

**spawn():**
- General purpose process creation
- Doesn't create new V8 instance
- For any system command
- Streams data

**fork():**
- Special case of spawn
- Creates new V8 instance
- Specifically for Node.js scripts
- Built-in communication channel

---

## 26. What is Environment Variable?

**Answer:** Environment variables are external variables that configure application behavior without changing code.

**Common Use Cases:**
- Database credentials
- API keys
- Port numbers
- Environment (dev/prod)

**Access:** `process.env.VARIABLE_NAME`

**Best Practice:** Use `.env` file with `dotenv` package, never commit to version control.

---

## 27. What is the purpose of __dirname and __filename?

**Answer:**

**__dirname:**
- Absolute path of directory containing current file
- Useful for file operations

**__filename:**
- Absolute path of current file including filename

**Use Case:** Construct file paths independent of execution location.

**Note:** Not available in ES6 modules (use `import.meta.url`).

---

## 28. What is Template Engine?

**Answer:** Template engines generate HTML dynamically by combining templates with data.

**Popular Engines:**
- **Pug:** Indentation-based syntax
- **EJS:** Embedded JavaScript (HTML with JS)
- **Handlebars:** Logic-less templates

**Benefits:**
- Reusable templates
- Dynamic content
- Cleaner separation
- Template inheritance

---

## 29. What is the difference between PUT and PATCH?

**Answer:**

**PUT:**
- Replace entire resource
- Send all fields
- Idempotent

**PATCH:**
- Partial update
- Send only changed fields
- More efficient

**Example:**
- PUT: Update entire user object
- PATCH: Update only user email

---

## 30. What is Dependency Injection?

**Answer:** Dependency Injection is a design pattern where dependencies are provided to a module rather than created inside it.

**Benefits:**
- Loose coupling
- Better testability
- Easier maintenance
- Flexibility

**Implementation in Node.js:**
- Constructor injection
- Function parameters
- Dependency injection containers

**Interview Tip:** Makes code more modular and testable by removing hard dependencies.

---
## 31. What is cluster module in Node.js?

**Answer:** Cluster module allows creating child processes that share same server port.

**Purpose:**
- Take advantage of multi-core systems
- Create worker processes
- Share workload
- Improve performance

**Master-Worker Pattern:**
- Master process manages workers
- Workers handle requests
- Automatic load balancing

**Use Case:** Scale Node.js applications across multiple CPU cores.

---

## 32. What is middleware in Express.js?

**Answer:** Middleware are functions that have access to request object, response object, and next middleware function.

**Types:**
- Application-level middleware
- Router-level middleware
- Error-handling middleware
- Built-in middleware
- Third-party middleware

**Functions:**
- Execute code
- Modify request/response
- End request-response cycle
- Call next middleware

**Example Uses:** Logging, authentication, parsing, error handling

---

## 33. What is the difference between `process.nextTick()` and `setImmediate()`?

**Answer:**

**process.nextTick():**
- Executes before event loop continues
- Higher priority
- Executes after current operation
- Before any I/O events

**setImmediate():**
- Executes on next iteration of event loop
- After I/O events
- Lower priority than nextTick

**Order:** nextTick → I/O callbacks → setImmediate

---

## 34. What is package.json?

**Answer:** package.json is manifest file containing metadata about Node.js project.

**Key Fields:**
- `name`: Package name
- `version`: Package version
- `description`: Package description
- `main`: Entry point
- `scripts`: Command shortcuts
- `dependencies`: Production dependencies
- `devDependencies`: Development dependencies
- `engines`: Specifies Node.js version

**Generated by:** `npm init` command

---

## 35. What is the difference between `npm` and `npx`?

**Answer:**

**npm (Node Package Manager):**
- Installs packages
- Manages dependencies
- Runs scripts from package.json
- Global and local installation

**npx (Node Package Execute):**
- Executes packages without installing
- Runs packages from npm registry
- Uses local installation if available
- Good for one-time use

**Example:** `npx create-react-app myapp` (no global installation needed)

---

## 36. What are child processes in Node.js?

**Answer:** Child processes allow Node.js to run system commands and external applications.

**Methods:**
- `spawn()`: Streams data, large outputs
- `exec()`: Buffers data, small outputs
- `execFile()`: Like exec but more efficient
- `fork()`: Special spawn for Node.js processes

**Use Cases:**
- CPU-intensive tasks
- Running scripts
- Executing system commands

---

## 37. What is CORS?

**Answer:** CORS (Cross-Origin Resource Sharing) is security feature that restricts web applications from making requests to different domain.

**Problem:** Browser blocks cross-origin requests by default

**Solution:**
- Enable CORS on server
- Set appropriate headers
- Use cors middleware in Express

**Headers:**
- `Access-Control-Allow-Origin`
- `Access-Control-Allow-Methods`
- `Access-Control-Allow-Headers`

---

## 38. What is the purpose of `module.exports` and `exports`?

**Answer:**

**module.exports:**
- Actual object returned by require()
- Can be reassigned
- Default export mechanism

**exports:**
- Reference to module.exports
- Shortcut for adding properties
- Cannot be reassigned

**Rule:** Use `module.exports` for exporting single item, `exports` for multiple properties.

---

## 39. What is a callback hell and how to avoid it?

**Answer:** Callback hell is situation with deeply nested callbacks making code hard to read and maintain.

**Problems:**
- Hard to read
- Difficult to debug
- Error handling complex
- "Pyramid of doom" structure

**Solutions:**
- Promises
- Async/await
- Modularize code (separate functions)
- Use libraries (async.js)
- Named functions instead of anonymous

---

## 40. What is dotenv?

**Answer:** dotenv is package that loads environment variables from `.env` file into `process.env`.

**Purpose:**
- Separate configuration from code
- Keep sensitive data secure
- Different configs for different environments
- Don't commit secrets to version control

**Usage:** Store API keys, database credentials, ports, etc.

**Best Practice:** Add `.env` to `.gitignore`

---

## 41. What is rate limiting?

**Answer:** Rate limiting restricts number of requests client can make in given time period.

**Purpose:**
- Prevent abuse
- Protect against DDoS
- Ensure fair usage
- Save server resources

**Implementation:**
- express-rate-limit package
- Token bucket algorithm
- Sliding window

**Response:** Return 429 (Too Many Requests) status

---

## 42. What is helmet in Node.js?

**Answer:** Helmet is middleware that helps secure Express apps by setting various HTTP headers.

**Security Headers:**
- Content Security Policy
- X-Frame-Options
- X-XSS-Protection
- Strict-Transport-Security
- X-Content-Type-Options

**Purpose:** Protect against common web vulnerabilities

**Usage:** Simple `app.use(helmet())` adds multiple security headers

---

## 43. What is the purpose of `package-lock.json`?

**Answer:** package-lock.json ensures consistent installations across environments.

**Features:**
- Locks exact package versions
- Includes dependency tree
- Automatically generated
- Improves install speed
- Should be committed to version control

**Difference from package.json:** package.json has ranges, package-lock.json has exact versions

---

## 44. What is Winston?

**Answer:** Winston is popular logging library for Node.js.

**Features:**
- Multiple transports (console, file, remote)
- Log levels (error, warn, info, debug)
- Format customization
- Asynchronous logging
- Query logs

**Transports:** Console, File, HTTP, Stream

**Benefit:** Better than console.log for production applications

---

## 45. What is the difference between authentication and authorization?

**Answer:**

**Authentication:**
- Verifies identity
- "Who are you?"
- Login process
- Credentials validation
- Usually first step

**Authorization:**
- Verifies permissions
- "What can you do?"
- Access control
- Happens after authentication
- Role-based or permission-based

**Example:** Login (authentication), then check if user can delete post (authorization)

---