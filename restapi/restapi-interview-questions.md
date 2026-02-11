# REST API Interview Questions & Answers

## 1. What is REST API?

**Answer:** REST (Representational State Transfer) is an architectural style for designing networked applications using HTTP protocol.

**Key Characteristics:**
- **Stateless:** Each request independent
- **Client-Server:** Separation of concerns
- **Cacheable:** Responses can be cached
- **Uniform Interface:** Standard methods (GET, POST, PUT, DELETE)
- **Layered System:** Hierarchical architecture
- **Code on Demand:** Optional (executable code)

**Why REST:**
- Simple and lightweight
- Platform-independent
- Scalable
- Language-agnostic

---

## 2. What are HTTP Methods in REST?

**Answer:**

**GET:**
- Retrieve data
- Idempotent (safe to repeat)
- No body in request
- Cacheable

**POST:**
- Create new resource
- Not idempotent
- Has request body
- Not cacheable

**PUT:**
- Update/Replace entire resource
- Idempotent
- Has request body

**PATCH:**
- Partial update
- Modifies specific fields
- More efficient than PUT

**DELETE:**
- Remove resource
- Idempotent

**HEAD:**
- Like GET but returns only headers
- Check resource existence

**OPTIONS:**
- Describes communication options
- CORS preflight

---

## 3. What is the difference between PUT and PATCH?

**Answer:**

| Feature | PUT | PATCH |
|---------|-----|-------|
| Purpose | Replace entire resource | Update specific fields |
| Idempotent | Yes | Not guaranteed |
| Payload | Complete resource | Partial data |
| Efficiency | Less efficient | More efficient |
| Use Case | Full update | Partial update |

**Example:**
- PUT: Send entire user object to update email
- PATCH: Send only {"email": "new@email.com"}

---

## 4. What are HTTP Status Codes?

**Answer:** Status codes indicate result of HTTP request.

**1xx - Informational:**
- 100: Continue
- 101: Switching Protocols

**2xx - Success:**
- 200: OK (success)
- 201: Created (resource created)
- 204: No Content (success, no response body)

**3xx - Redirection:**
- 301: Moved Permanently
- 302: Found (temporary redirect)
- 304: Not Modified (cached version valid)

**4xx - Client Errors:**
- 400: Bad Request (invalid syntax)
- 401: Unauthorized (authentication required)
- 403: Forbidden (no permission)
- 404: Not Found
- 409: Conflict

**5xx - Server Errors:**
- 500: Internal Server Error
- 502: Bad Gateway
- 503: Service Unavailable
- 504: Gateway Timeout

---

## 5. What is the difference between 401 and 403?

**Answer:**

**401 Unauthorized:**
- Authentication required
- User not identified
- "Who are you?"
- Solution: Provide valid credentials

**403 Forbidden:**
- User authenticated but no permission
- "I know who you are, but you can't access this"
- Solution: Get proper permissions

**Interview Tip:** 401 = "Login first", 403 = "You're logged in but can't access this"

---

## 6. What is RESTful API?

**Answer:** RESTful API is an API that follows REST architectural principles.

**Characteristics:**
- Uses HTTP methods correctly
- Stateless communication
- Resource-based URLs
- Returns standard HTTP status codes
- Supports multiple formats (JSON, XML)
- Follows REST constraints

**Example:**
- RESTful: `GET /users/123`
- Not RESTful: `GET /getUserById?id=123`

---

## 7. What is Idempotency?

**Answer:** Idempotent operations produce same result regardless of how many times executed.

**Idempotent Methods:**
- GET: Reading doesn't change data
- PUT: Same update multiple times = same result
- DELETE: Deleting already deleted resource still results in deleted state
- HEAD, OPTIONS

**Non-Idempotent:**
- POST: Creating multiple times creates multiple resources

**Why Important:**
- Safe to retry
- Network reliability
- Prevents duplicate operations

---

## 8. What is CRUD?

**Answer:** CRUD represents four basic operations for persistent storage.

**Operations:**

**Create** → POST
- Add new resource

**Read** → GET
- Retrieve resource

**Update** → PUT/PATCH
- Modify existing resource

**Delete** → DELETE
- Remove resource

**Interview Tip:** Most APIs are built around CRUD operations mapped to HTTP methods.

---

## 9. What is the difference between REST and SOAP?

**Answer:**

| Feature | REST | SOAP |
|---------|------|------|
| Type | Architectural style | Protocol |
| Format | JSON, XML, HTML | Only XML |
| Performance | Faster (lightweight) | Slower (verbose) |
| Bandwidth | Less | More |
| Security | HTTPS | WS-Security (built-in) |
| Caching | Supports | Difficult |
| Statefulness | Stateless | Can be stateful |
| Use Case | Web, mobile apps | Enterprise, financial |

**Interview Tip:** REST is modern, lightweight standard; SOAP for enterprise with strict standards.

---

## 10. What is JSON?

**Answer:** JSON (JavaScript Object Notation) is lightweight data-interchange format.

**Characteristics:**
- Human-readable
- Language-independent
- Text-based
- Easy to parse

**Data Types:**
- String: "hello"
- Number: 123, 45.6
- Boolean: true, false
- Array: [1, 2, 3]
- Object: {"key": "value"}
- null

**Why popular:**
- Simpler than XML
- Native JavaScript support
- Compact size

---

## 11. What is API Versioning?

**Answer:** API versioning manages changes and updates to API while maintaining backward compatibility.

**Methods:**

**URI Versioning:**
- `/api/v1/users`
- Most common
- Clear and explicit

**Query Parameter:**
- `/api/users?version=1`
- Less common

**Header Versioning:**
- `Accept: application/vnd.myapi.v1+json`
- Clean URLs
- More complex

**Media Type:**
- Content negotiation
- `Accept: application/vnd.company.v1+json`

**Best Practice:** Plan for versioning from start, deprecate old versions gracefully.

---

## 12. What is CORS?

**Answer:** CORS (Cross-Origin Resource Sharing) is security feature that controls resource access from different origins.

**Problem:** Browsers block requests from one origin to another (security).

**Solution:** Server explicitly allows cross-origin requests.

**Headers:**
- `Access-Control-Allow-Origin`: Allowed origins
- `Access-Control-Allow-Methods`: Allowed HTTP methods
- `Access-Control-Allow-Headers`: Allowed headers

**Preflight Request:** OPTIONS request to check permissions before actual request.

**Interview Tip:** CORS is browser security feature; doesn't affect server-to-server communication.

---

## 13. What is Authentication vs Authorization?

**Answer:**

**Authentication:**
- **Question:** "Who are you?"
- **Purpose:** Verify identity
- **Process:** Login with username/password
- **Result:** Identity confirmed
- **Example:** Logging into system

**Authorization:**
- **Question:** "What can you do?"
- **Purpose:** Verify permissions
- **Process:** Check access rights
- **Result:** Permission granted/denied
- **Example:** Admin vs regular user rights

**Interview Tip:** Authentication first, then authorization. AuthN → AuthZ.

---

## 14. What is JWT (JSON Web Token)?

**Answer:** JWT is compact, URL-safe token for securely transmitting information between parties.

**Structure:**
1. **Header:** Algorithm and token type
2. **Payload:** Claims (user data)
3. **Signature:** Verify authenticity

**Format:** `header.payload.signature`

**Flow:**
1. User logs in
2. Server generates JWT
3. Client stores JWT
4. Client sends JWT with requests
5. Server verifies JWT

**Benefits:**
- Stateless
- Self-contained
- Scalable
- Cross-domain

---

## 15. What is OAuth?

**Answer:** OAuth is open standard for token-based authentication and authorization.

**Purpose:** Allow third-party apps limited access without sharing passwords.

**Common Use:** "Login with Google/Facebook"

**Flow:**
1. User initiates
2. Redirect to OAuth provider
3. User authorizes
4. Provider returns auth code
5. Exchange code for access token
6. Use token to access resources

**Versions:** OAuth 1.0 (deprecated), OAuth 2.0 (current)

---

## 16. What is the difference between Authentication Token and API Key?

**Answer:**

| Feature | Token (JWT) | API Key |
|---------|------------|---------|
| Purpose | User authentication | Application identification |
| Expiration | Yes (time-bound) | No (long-lived) |
| User Context | Contains user info | No user info |
| Security | More secure (signed) | Less secure |
| Use Case | User sessions | App-to-app |
| Location | Header (Authorization) | Header or query param |

---

## 17. What is rate limiting?

**Answer:** Rate limiting restricts number of requests a client can make in a time period.

**Purpose:**
- Prevent abuse
- Fair resource usage
- DDoS protection
- Cost control

**Common Limits:**
- Requests per second/minute/hour
- Example: 100 requests per minute

**Implementation:**
- Token bucket algorithm
- Leaky bucket algorithm
- Fixed/sliding window

**Headers:**
- `X-RateLimit-Limit`: Total allowed
- `X-RateLimit-Remaining`: Remaining requests
- `X-RateLimit-Reset`: Reset time

---

## 18. What is API Gateway?

**Answer:** API Gateway is entry point that sits between clients and backend services.

**Functions:**
- Request routing
- Authentication/Authorization
- Rate limiting
- Load balancing
- Caching
- Request/response transformation
- Monitoring and logging

**Benefits:**
- Single entry point
- Centralized security
- Simplified client code
- Microservices abstraction

**Examples:** AWS API Gateway, Kong, Apigee

---

## 19. What is the difference between Synchronous and Asynchronous API?

**Answer:**

**Synchronous:**
- Client waits for response
- Real-time communication
- Immediate result
- Example: GET /users

**Asynchronous:**
- Client doesn't wait
- Non-blocking
- Callback/webhook for result
- Example: Video processing, bulk operations

**Use Async when:**
- Long-running operations
- Unpredictable processing time
- Background jobs

---

## 20. What is REST API Pagination?

**Answer:** Pagination divides large result sets into smaller chunks (pages).

**Methods:**

**Offset-based:**
- `?page=2&limit=10`
- Simple but can miss items if data changes

**Cursor-based:**
- `?cursor=abc123&limit=10`
- Consistent, handles changes
- Better for real-time data

**Benefits:**
- Better performance
- Reduced load
- Improved user experience

**Response should include:**
- Current page
- Total pages
- Total items
- Links to next/previous

---

## 21. What is HATEOAS?

**Answer:** HATEOAS (Hypermedia As The Engine Of Application State) is REST constraint where API responses include links to related resources.

**Purpose:** Client discovers available actions dynamically.

**Example Response:**
```
{
  "id": 123,
  "name": "John",
  "links": {
    "self": "/users/123",
    "orders": "/users/123/orders",
    "delete": "/users/123"
  }
}
```

**Benefits:**
- Self-documenting API
- Loose coupling
- Easier evolution

---

## 22. What is API Documentation?

**Answer:** API Documentation describes how to use and integrate with API.

**Should Include:**
- Endpoints and methods
- Request/response examples
- Parameters
- Authentication
- Error codes
- Rate limits

**Tools:**
- **Swagger/OpenAPI:** Interactive documentation
- **Postman:** API testing and docs
- **ReadTheDocs:** Comprehensive docs

---

## 23. What is Swagger/OpenAPI?

**Answer:** OpenAPI (formerly Swagger) is specification for describing RESTful APIs.

**Components:**
- **OpenAPI Spec:** YAML/JSON API description
- **Swagger UI:** Interactive documentation
- **Swagger Editor:** Edit API specs
- **Swagger Codegen:** Generate client/server code

**Benefits:**
- Standardized format
- Interactive testing
- Auto-generated docs
- Client SDK generation

---

## 24. What are Best Practices for REST API Design?

**Answer:**

**1. Use Nouns for Resources:**
- `/users` not `/getUsers`

**2. Use HTTP Methods Correctly:**
- GET for read, POST for create, etc.

**3. Use Plural Nouns:**
- `/users` not `/user`

**4. Hierarchical Structure:**
- `/users/123/orders`

**5. Version Your API:**
- `/api/v1/users`

**6. Use Standard Status Codes:**
- 200, 201, 400, 404, 500

**7. Filter, Sort, Paginate:**
- `?status=active&sort=name&page=2`

**8. Security:**
- HTTPS always
- Authentication/Authorization

**9. Error Handling:**
- Meaningful error messages

**10. Documentation:**
- Keep docs updated

---

## 25. What is Content Negotiation?

**Answer:** Content negotiation is mechanism for serving different representations of resource.

**Request Headers:**
- **Accept:** Preferred response format
  - `Accept: application/json`
  - `Accept: application/xml`
- **Accept-Language:** Preferred language
- **Accept-Encoding:** Compression (gzip)

**Server Response:**
- Returns format based on Accept header
- `Content-Type` header indicates actual format

**Benefits:**
- Multiple format support
- Client flexibility
- Backward compatibility

---

## 26. What is API Security?

**Answer:** API Security protects APIs from threats and unauthorized access.

**Key Measures:**

**1. Authentication:**
- Verify user identity
- JWT, OAuth

**2. Authorization:**
- Control access rights
- Role-based access

**3. HTTPS:**
- Encrypt data in transit
- Prevent snooping

**4. Input Validation:**
- Sanitize inputs
- Prevent injection attacks

**5. Rate Limiting:**
- Prevent abuse
- DDoS protection

**6. API Keys:**
- Identify applications
- Track usage

---

## 27. What is RESTful URL design?

**Answer:** RESTful URLs should be resource-based and intuitive.

**Good Practices:**

**Use nouns, not verbs:**
- ✓ `/users`
- ✗ `/getUsers`

**Plural nouns:**
- ✓ `/products`
- ✗ `/product`

**Hierarchical:**
- ✓ `/users/123/orders/456`

**Lowercase:**
- ✓ `/product-categories`
- ✗ `/ProductCategories`

**Hyphens not underscores:**
- ✓ `/product-categories`
- ✗ `/product_categories`

**No trailing slash:**
- ✓ `/users`
- ✗ `/users/`

---

## 28. What is the difference between REST and GraphQL?

**Answer:**

| Feature | REST | GraphQL |
|---------|------|----------|
| Request | Multiple endpoints | Single endpoint |
| Data Fetching | Fixed structure | Request specific fields |
| Over-fetching | Yes | No |
| Under-fetching | Yes (multiple requests) | No |
| Versioning | Required | Not needed |
| Learning Curve | Easy | Steeper |
| Caching | Built-in (HTTP) | Complex |
| Use Case | Simple APIs | Complex, nested data |

---

## 29. What is API Throttling?

**Answer:** API Throttling controls request rate to prevent overload.

**Difference from Rate Limiting:**
- **Rate Limiting:** Hard limit, reject after threshold
- **Throttling:** Slow down requests, queue or delay

**Strategies:**
- Reject requests (503 error)
- Queue requests
- Slow down processing

**Benefits:**
- Protect infrastructure
- Fair usage
- Cost management

---

## 30. What is webhook?

**Answer:** Webhook is HTTP callback (reverse API) where server pushes data to client when event occurs.

**How it works:**
1. Client registers webhook URL
2. Event occurs on server
3. Server sends HTTP POST to webhook URL
4. Client receives and processes data

**Use Cases:**
- Payment notifications
- GitHub commits
- Form submissions
- Real-time updates

**vs Polling:**
- Webhook: Push (efficient, real-time)
- Polling: Pull (inefficient, delay)

---
## 31. What is API Gateway?

**Answer:** API Gateway is server that acts as entry point for client requests to backend services.

**Functions:**
- Request routing
- Authentication/Authorization
- Rate limiting
- Load balancing
- Caching
- Request/response transformation
- Monitoring and logging

**Benefits:**
- Centralized management
- Security
- Scalability
- Simplified client code

**Examples:** Kong, AWS API Gateway, Azure API Management

---

## 32. What is the difference between synchronous and asynchronous APIs?

**Answer:**

**Synchronous APIs:**
- Client waits for response
- Blocking operation
- Immediate result
- Simpler to implement

**Asynchronous APIs:**
- Client doesn't wait
- Non-blocking operation
- Response comes later (callback/webhook)
- Better for long operations

**Use Async for:** File processing, email sending, report generation

---

## 33. What is API documentation?

**Answer:** API documentation provides information on how to use and integrate with API.

**Should Include:**
- Available endpoints
- Request/response formats
- Authentication methods
- Error codes
- Examples
- Rate limits
- Changelog

**Tools:**
- Swagger/OpenAPI
- Postman
- API Blueprint
- ReadMe

---

## 34. What is HAL (Hypertext Application Language)?

**Answer:** HAL is format for expressing relationships between resources in API responses.

**Key Concepts:**
- Resources
- Links (`_links`)
- Embedded resources (`_embedded`)

**Benefits:**
- Discoverability
- Self-documenting
- Consistent structure
- Easy navigation

**Use:** HATEOAS implementation

---

## 35. What is API monitoring?

**Answer:** API monitoring tracks API performance, availability, and correctness.

**Metrics:**
- Response time
- Error rates
- Uptime percentage
- Request volume
- Success rate

**Types:**
- Synthetic monitoring (scheduled tests)
- Real user monitoring
- Performance monitoring

**Tools:** Pingdom, New Relic, Datadog, Uptime Robot

---

## 36. What is the difference between REST and GraphQL?

**Answer:**

| REST | GraphQL |
|------|---------|
| Multiple endpoints | Single endpoint |
| Over-fetching/under-fetching | Get exactly what you need |
| HTTP methods define operations | Query language |
| Multiple requests for related data | One request for complex data |
| Versioning needed | No versioning (evolves) |
| Server defines response | Client defines query |

**When to use GraphQL:** Complex data relationships, mobile apps (bandwidth), frequent changes

---

## 37. What are HTTP status code ranges?

**Answer:**

**1xx - Informational:**
- Request received, processing continues

**2xx - Success:**
- Request successfully received and accepted

**3xx - Redirection:**
- Further action needed to complete request

**4xx - Client Error:**
- Request contains bad syntax or can't be fulfilled

**5xx - Server Error:**
- Server failed to fulfill valid request

---

## 38. What is API throttling strategy?

**Answer:** API throttling limits request rate to protect resources.

**Strategies:**
- **Fixed Window:** Count requests in fixed time window
- **Sliding Window:** More accurate, sliding time window
- **Token Bucket:** Tokens refill over time
- **Leaky Bucket:** Requests processed at constant rate

**Response Headers:**
- `X-RateLimit-Limit`: Total allowed
- `X-RateLimit-Remaining`: Remaining requests
- `X-RateLimit-Reset`: Reset time

---

## 39. What is content negotiation?

**Answer:** Content negotiation is mechanism where server serves different versions of resource based on client preferences.

**Types:**
- **Media type:** JSON, XML, HTML
- **Language:** en, es, fr
- **Encoding:** gzip, compress
- **Charset:** UTF-8, ISO-8859-1

**Headers:**
- `Accept`: Media type preference
- `Accept-Language`: Language preference
- `Accept-Encoding`: Encoding preference

---

## 40. What is SOAP?

**Answer:** SOAP (Simple Object Access Protocol) is protocol for exchanging structured information.

| SOAP | REST |
|------|------|
| Protocol | Architectural style |
| XML only | Multiple formats |
| Built-in security (WS-Security) | Relies on HTTPS |
| WSDL for contract | No standard contract |
| Complex | Simple |
| Strictly defined standards | Flexible |

**When to use SOAP:** Banking, payments, enterprise systems requiring high security

---

## 41. What is API lifecycle?

**Answer:** API lifecycle covers stages from planning to retirement.

**Stages:**
1. **Planning:** Define requirements and purpose
2. **Design:** Create API structure and endpoints
3. **Development:** Build API
4. **Testing:** Validate functionality
5. **Deployment:** Release to production
6. **Monitoring:** Track performance
7. **Versioning:** Manage changes
8. **Retirement:** Deprecate old versions

---

## 42. What is mock API?

**Answer:** Mock API simulates real API behavior for testing and development.

**Benefits:**
- Parallel development (frontend/backend)
- Testing without real data
- Offline development
- Faster development cycle
- Cost savings

**Tools:** MockServer, Postman Mock Server, JSON Server

---

## 43. What is the difference between URI and URL?

**Answer:**

**URI (Uniform Resource Identifier):**
- Identifies resource
- Can be URL or URN
- More general

**URL (Uniform Resource Locator):**
- Identifies resource by location
- Specifies how to access
- Subset of URI
- Includes protocol and address

**Example:** `https://api.example.com/users/123` is both URI and URL

---

## 44. What is hypermedia?

**Answer:** Hypermedia is inclusion of links within API responses to guide clients.

**HATEOAS (Hypermedia as the Engine of Application State):**
- API responses include links to related resources
- Client discovers actions dynamically
- Self-documenting

**Benefits:**
- Discoverability
- Loose coupling
- Evolvability

---

## 45. What is API contract?

**Answer:** API contract is formal agreement defining how API behaves.

**Includes:**
- Endpoints and methods
- Request/response formats
- Error handling
- Authentication requirements
- Rate limits
- Expected behavior

**Formats:**
- OpenAPI (Swagger)
- RAML
- API Blueprint

**Purpose:** Clear communication between API provider and consumers

---