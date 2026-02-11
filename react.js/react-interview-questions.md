# React.js Interview Questions & Answers

## 1. What is React and what are its features?

**Answer:** React is a JavaScript library for building user interfaces, developed by Facebook in 2013.

**Key Features:**
- **Component-Based:** UI split into reusable components
- **Virtual DOM:** Fast rendering with minimal DOM manipulation
- **JSX:** JavaScript XML syntax for writing HTML in JS
- **Unidirectional Data Flow:** Data flows from parent to child
- **Declarative:** Describe what UI should look like
- **React Hooks:** Write stateful logic without classes

**Why React:**
- Fast performance
- Reusable components
- Large ecosystem
- Strong community support

---

## 2. What is JSX?

**Answer:** JSX (JavaScript XML) is a syntax extension that allows writing HTML-like code in JavaScript.

**Features:**
- Combines HTML and JavaScript
- Transpiled to JavaScript by Babel
- Supports JavaScript expressions in `{}`
- Must return single parent element
- Requires camelCase for attributes (className, onClick)

**Example:** `const element = <h1>Hello, {name}!</h1>`

**Advantages:**
- Easier to visualize UI structure
- Faster than regular JavaScript
- Type-safe (catches errors)

**Interview Tip:** JSX is not mandatory but highly recommended for readability.

---

## 3. What is Virtual DOM?

**Answer:** Virtual DOM is a lightweight copy of actual DOM kept in memory. React uses it to optimize updates.

**How it works:**
1. **Create:** Virtual DOM representation created on changes
2. **Diff:** React compares new and previous virtual DOM (diffing)
3. **Update:** Only changed parts updated in real DOM (reconciliation)

**Benefits:**
- Faster updates (batch processing)
- Better performance
- Cross-browser compatibility

**Interview Tip:** Virtual DOM makes React fast by minimizing expensive DOM operations.

---

## 4. What is the difference between Class and Functional Components?

**Answer:**

| Feature | Class Component | Functional Component |
|---------|----------------|---------------------|
| Syntax | ES6 class | JavaScript function |
| State | this.state | useState hook |
| Lifecycle | Lifecycle methods | useEffect hook |
| this keyword | Required | Not used |
| Performance | Slightly slower | Slightly faster |
| Code | More boilerplate | Cleaner, less code |
| Current Trend | Legacy | Modern approach |

**Interview Tip:** Functional components with hooks are the modern standard.

---

## 5. What are React Hooks?

**Answer:** Hooks are functions that let you use state and lifecycle features in functional components (introduced in React 16.8).

**Common Hooks:**

**useState:** Manage state
**useEffect:** Side effects (lifecycle)
**useContext:** Access context
**useRef:** Create mutable references
**useMemo:** Memoize expensive computations
**useCallback:** Memoize functions
**useReducer:** Complex state logic

**Rules:**
- Only call at top level (not in loops/conditions)
- Only call from React functions

**Benefits:**
- Reuse stateful logic
- Cleaner code
- No classes needed

---

## 6. Explain useState Hook.

**Answer:** useState is a hook for adding state to functional components.

**Syntax:** `const [state, setState] = useState(initialValue)`

**Returns:**
- Current state value
- Function to update state

**Key Points:**
- State updates are asynchronous
- Can use functional update: `setState(prev => prev + 1)`
- Can have multiple useState in one component
- Initial value used only on first render

**Interview Tip:** Don't mutate state directly; always use setState function.

---

## 7. Explain useEffect Hook.

**Answer:** useEffect performs side effects in functional components (replaces componentDidMount, componentDidUpdate, componentWillUnmount).

**Syntax:** `useEffect(callback, dependencyArray)`

**Behaviors based on dependency array:**
- **No array:** Runs after every render
- **Empty array `[]`:** Runs once (mount only)
- **With dependencies:** Runs when dependencies change

**Cleanup:** Return function from useEffect for cleanup (unmount)

**Use Cases:**
- API calls
- DOM manipulation
- Subscriptions
- Timers

---

## 8. What is the difference between Props and State?

**Answer:**

| Feature | Props | State |
|---------|-------|-------|
| Definition | Data passed from parent | Data managed within component |
| Mutability | Immutable (read-only) | Mutable (can be changed) |
| Access | Received as function parameter | Managed with useState/this.state |
| Update | Cannot change | Can update with setState |
| Direction | Parent to child | Local to component |

**Interview Tip:** Props flow down  (parent → child), Events flow up (child → parent via callbacks).

---

## 9. What is Component Lifecycle in React?

**Answer:** Component lifecycle is the series of phases a component goes through from creation to destruction.

**Three Phases:**

**1. Mounting (Birth):**
- constructor()
- getDerivedStateFromProps()
- render()
- componentDidMount() - **Side effects here**

**2. Updating (Growth):**
- getDerivedStateFromProps()
- shouldComponentUpdate()
- render()
- getSnapshotBeforeUpdate()
- componentDidUpdate() - **Side effects here**

**3. Unmounting (Death):**
- componentWillUnmount() - **Cleanup here**

**With Hooks:** useEffect replaces most lifecycle methods in functional components.

---

## 10. What is Prop Drilling and how to avoid it?

**Answer:** Prop Drilling is passing props through multiple intermediate components that don't need the data.

**Problems:**
- Code becomes messy
- Hard to maintain
- Performance issues
- Unnecessary re-renders

**Solutions:**

**1. Context API:** Share data without passing props
**2. Component Composition:** Render children directly
**3. State Management:** Redux, Zustand, MobX
**4. Custom Hooks:** Encapsulate logic

**Interview Tip:** Use Context for global data, props for local/direct parent-child communication.

---

## 11. What is Context API?

**Answer:** Context API provides a way to share data across component tree without prop drilling.

**When to use:**
- Theme data
- User authentication
- Language preferences
- Global settings

**Steps:**
1. Create Context: `React.createContext()`
2. Provider: Wrap components with `<Context.Provider value={data}>`
3. Consumer: Access with `useContext(MyContext)`

**Advantages:**
- Avoid prop drilling
- Global state management
- Built-in React feature

**Interview Tip:** Don't overuse - not replacement for robust state management in large apps.

---

## 12. What are Keys in React and why are they important?

**Answer:** Keys are special attributes for list items that help React identify which items changed, added, or removed.

**Purpose:**
- Optimize re-rendering
- Maintain component state
- Prevent bugs

**Best Practices:**
- Use unique, stable IDs
- Don't use array index (unless list is static)
- Keys should be unique among siblings

**Why not index:**
- Changes on reorder
- Causes performance issues
- Can lead to state bugs

**Interview Tip:** Keys help React's reconciliation algorithm work efficiently.

---

## 13. What are Controlled and Uncontrolled Components?

**Answer:**

**Controlled Components:**
- Form data handled by React state
- Value controlled by React
- onChange updates state
- Single source of truth

**Uncontrolled Components:**
- Form data handled by DOM
- Use refs to access values
- Similar to traditional HTML

**Recommendation:** Controlled components preferred for consistency and validation.

**Interview Tip:** Controlled = React controls value, Uncontrolled = DOM controls value.

---

## 14. What is React Router?

**Answer:** React Router is a library for handling navigation and routing in React applications.

**Key Concepts:**
- **BrowserRouter:** Main router component
- **Route:** Define path and component mapping
- **Link:** Navigate without page reload
- **useNavigate:** Programmatic navigation
- **useParams:** Access URL parameters

**Benefits:**
- SPA navigation
- Dynamic routing
- Nested routes
- Protected routes

---

## 15. What is the difference between useCallback and useMemo?

**Answer:**

| Feature | useCallback | useMemo |
|---------|------------|---------|
| Returns | Memoized function | Memoized value |
| Purpose | Prevent function recreation | Prevent expensive calculations |
| Use Case | Pass callbacks to optimized child | Cache computed values |
| Syntax | `useCallback(fn, deps)` | `useMemo(() => value, deps)` |

**When to use:**
- useCallback: Passing functions to child components
- useMemo: Expensive computations

**Interview Tip:** Both optimize performance by preventing unnecessary re-computations.

---

## 16. What is Redux?

**Answer:** Redux is a predictable state container for JavaScript applications, commonly used with React.

**Core Concepts:**

**Store:** Single source of truth (entire state)
**Actions:** Objects describing what happened
**Reducers:** Pure functions that update state
**Dispatch:** Method to send actions

**Principles:**
1. Single source of truth
2. State is read-only
3. Changes made with pure functions

**When to use:**
- Large applications
- Complex state logic
- State shared across many components

---

## 17. What is the difference between Redux and Context API?

**Answer:**

| Feature | Redux | Context API |
|---------|-------|-------------|
| Purpose | State management library | React feature |
| Complexity | More complex | Simple |
| Performance | Optimized | Can cause unnecessary re-renders |
| DevTools | Excellent debugging tools | Limited |
| Middleware | Supports middleware | No middleware |
| Best For | Large apps | Small to medium apps |

**Interview Tip:** Context API for simple state sharing, Redux for complex state management.

---

## 18. What are Higher-Order Components (HOC)?

**Answer:** HOC is a function that takes a component and returns a new enhanced component.

**Purpose:**
- Code reuse
- Logic abstraction
- Props manipulation
- Render hijacking

**Use Cases:**
- Authentication checks
- Logging
- Error handling
- Data fetching

**Naming Convention:** Prefix with "with" (withAuth, withLoading)

**Modern Alternative:** Custom hooks are now preferred over HOCs.

---

## 19. What are React Fragments?

**Answer:** Fragments let you group multiple children without adding extra nodes to DOM.

**Syntax:**
- `<React.Fragment>...</React.Fragment>`
- Short syntax: `<>...</>`

**Why use:**
- Avoid unnecessary div wrappers
- Cleaner DOM structure
- Slightly better performance

**With keys:** Use full syntax when keys needed in lists.

---

## 20. What is the difference between Element and Component?

**Answer:**

**Element:**
- Plain JavaScript object
- Describes what to render
- Immutable
- Created with JSX or React.createElement()

**Component:**
- Function or class
- Blueprint for creating elements
- Can have state and props
- Reusable

**Relationship:** Components produce elements.

---

## 21. What are Pure Components?

**Answer:** Pure Components automatically implement shallow comparison in shouldComponentUpdate to prevent unnecessary re-renders.

**Class Components:** `React.PureComponent`
**Functional Components:** `React.memo()`

**Benefits:**
- Performance optimization
- Automatic shallow comparison
- Less code

**Use with caution:** Only when props/state are simple (not deeply nested objects).

---

## 22. What is React.memo()?

**Answer:** React.memo() is a higher-order component that memoizes functional components to prevent unnecessary re-renders.

**How it works:**
- Shallow compares props
- Re-renders only if props changed
- Can provide custom comparison function

**When to use:**
- Pure functional components
- Expensive rendering
- Props don't change often

**Interview Tip:** Don't overuse - adds overhead. Use when profiling shows benefit.

---

## 23. What is Lazy Loading in React?

**Answer:** Lazy loading is a technique to split code and load components only when needed.

**Implementation:**
- `React.lazy()` for dynamic imports
- `Suspense` component for fallback UI

**Benefits:**
- Smaller initial bundle size
- Faster initial load
- Better performance

**Use Cases:**
- Route-based code splitting
- Large components
- Modal dialogs
- Tabs content

---

## 24. What is Error Boundary?

**Answer:** Error Boundaries are components that catch JavaScript errors in child component tree and display fallback UI.

**Catches:**
- Rendering errors
- Lifecycle method errors
- Constructor errors

**Doesn't Catch:**
- Event handlers
- Async code
- Server-side rendering
- Errors in error boundary itself

**Implementation:** Class component with componentDidCatch() or getDerivedStateFromError()

**Interview Tip:** There's no error boundary hook yet; must use class component.

---

## 25. What are Portals in React?

**Answer:** Portals provide a way to render children into a DOM node outside parent component's hierarchy.

**Use Cases:**
- Modals
- Tooltips
- Dropdowns
- Popups

**Syntax:** `ReactDOM.createPortal(child, container)`

**Benefits:**
- Escape parent CSS constraints (overflow, z-index)
- Event bubbles to React parent (despite DOM placement)

---

## 26. What is the difference between SPA and MPA?

**Answer:**

**SPA (Single Page Application):**
- Single HTML page
- Content loaded dynamically
- Faster navigation
- Example: React, Vue, Angular apps

**MPA (Multi Page Application):**
- Multiple HTML pages
- Full page reload on navigation
- Traditional server-rendered

**SPA Advantages:** Better UX, faster after initial load
**SPA Disadvantages:** Larger initial load, SEO challenges

---

## 27. What is Server-Side Rendering (SSR)?

**Answer:** SSR renders React components on server and sends HTML to browser.

**Benefits:**
- Better SEO
- Faster initial page load
- Social media sharing (meta tags)

**Drawbacks:**
- Server load
- Complexity
- Slower time to interactive

**Popular Frameworks:** Next.js, Gatsby

---

## 28. What is the difference between useEffect and useLayoutEffect?

**Answer:**

| Feature | useEffect | useLayoutEffect |
|---------|----------|----------------|
| Timing | After paint | Before paint |
| Async | Asynchronous | Synchronous |
| Use Case | Most side effects | DOM measurements |
| Performance | Better | Can block visual updates |

**When to use useLayoutEffect:**
- DOM measurements
- Prevent visual flickering
- Synchronous DOM mutations

**Interview Tip:** 99% of time use useEffect. useLayoutEffect only when timing matters.

---

## 29. What is code splitting in React?

**Answer:** Code splitting is breaking application into smaller chunks loaded on demand.

**Benefits:**
- Reduced initial load time
- Better performance
- Loaded only when needed

**Methods:**
1. **Dynamic imports:** `import()` syntax
2. **React.lazy():** Component-level splitting
3. **Route-based:** Split by routes

**Tools:** Webpack, Parcel support automatic code splitting.

---

## 30. What are Custom Hooks?

**Answer:** Custom hooks are JavaScript functions that use React hooks and encapsulate reusable stateful logic.

**Naming:** Must start with "use" (useFetch, useAuth, useLocalStorage)

**Benefits:**
- Code reuse
- Clean components
- Separate concerns
- Testable logic

**Example Use Cases:**
- Data fetching
- Form handling
- Authentication
- Local storage
- Window size tracking

**Interview Tip:** Custom hooks let you extract component logic into reusable functions following hooks rules.

---
## 31. What is the difference between controlled and uncontrolled components?

**Answer:**

**Controlled Components:**
- Form data handled by React state
- Value controlled by React
- onChange updates state
- Single source of truth
- More control and validation

**Uncontrolled Components:**
- Form data handled by DOM
- Use ref to access values
- Less React code
- Simpler for basic forms

**Recommendation:** Use controlled components for better control and validation.

---

## 32. What is React Context ?

**Answer:** Context provides way to pass data through component tree without passing props manually at every level.

**When to Use:**
- Global data (theme, language, user info)
- Avoid prop drilling
- Data needed by many components at different levels

**Components:**
- `createContext()`: Creates context
- `Provider`: Supplies value
- `Consumer` or `useContext`: Consumes value

**Caution:** Overuse can make component reuse harder.

---

## 33. What are React portals?

**Answer:** Portals provide way to render children into DOM node outside parent component hierarchy.

**Use Cases:**
- Modals
- Tooltips
- Dropdowns
- Overlays

**Syntax:** `ReactDOM.createPortal(child, container)`

**Behavior:**
- Event bubbling works normally
- Context works across portals
- Renders outside parent DOM, but inside React tree

---

## 34. What is React.memo()?

**Answer:** `React.memo()` is higher-order component that memoizes component to prevent unnecessary re-renders.

**How It Works:**
- Shallow props comparison
- Re-renders only if props change
- Performance optimization

**When to Use:**
- Pure functional components
- Component re-renders with same props
- Expensive rendering operations

**Custom Comparison:** Can provide custom comparison function as second argument.

---

## 35. What is the difference between `useMemo` and `useCallback`?

**Answer:**

| useMemo | useCallback |
|---------|-------------|
| Memoizes **value** | Memoizes **function** |
| Returns computed value | Returns memoized callback |
| For expensive calculations | For callback functions |
| Prevents recalculation | Prevents function recreation |

**useMemo:** `useMemo(() => compute(a, b), [a, b])`
**useCallback:** `useCallback(() => doSomething(a, b), [a, b])`

**Key:** `useCallback(fn, deps)` equals `useMemo(() => fn, deps)`

---

## 36. What is prop drilling?

**Answer:** Prop drilling is passing data through multiple component layers to reach deeply nested component.

**Problems:**
- Code verbosity
- Hard to maintain
- Unnecessary re-renders
- Components become less reusable

**Solutions:**
- Context API
- State management (Redux, Zustand)
- Component composition
- Custom hooks

---

## 37. What are error boundaries?

**Answer:** Error boundaries are React components that catch JavaScript errors in child component tree.

**Features:**
- Catch errors during rendering
- Catch errors in lifecycle methods
- Catch errors in constructors
- Display fallback UI
- Log error information

**Limitations:**
- Don't catch errors in event handlers
- Don't catch errors in async code
- Don't catch errors in error boundary itself
- Only class components can be error boundaries

---

## 38. What is lazy loading in React?

**Answer:** Lazy loading defers loading non-critical components until needed.

**Implementation:**
- `React.lazy()`: Dynamic import
- `Suspense`: Fallback UI while loading

**Benefits:**
- Faster initial load
- Reduced bundle size
- Better performance
- Load on demand

**Use Cases:** Route-based splitting, modal dialogs, tabs, conditional features

---

## 39. What is the difference between `useState` and `useReducer`?

**Answer:**

**useState:**
- Simple state management
- Single value or object
- setState updates state
- Good for independent state updates
- Less boilerplate

**useReducer:**
- Complex state logic
- Multiple related values
- Dispatch actions to reducer
- Good for interdependent state
- More predictable
- Similar to Redux pattern

**When to use useReducer:** Complex state logic, multiple sub-values, next state depends on previous.

---

## 40. What is React Fiber?

**Answer:** React Fiber is reimplementation of React's core algorithm (React 16+).

**Key Features:**
- Incremental rendering
- Ability to pause, abort, or reuse work
- Priority to different types of updates
- Concurrency
- Better animation and layout performance

**Benefits:**
- Improved responsiveness
- Better handling of async rendering
- Smoother animations
- Split rendering work into chunks

---

## 41. What are fragments?

**Answer:** Fragments let you group multiple children without adding extra DOM nodes.

**Syntax:**
- `<React.Fragment>...</React.Fragment>`
- Short syntax: `<>...</>`

**Benefits:**
- No extra DOM nodes
- Cleaner HTML
- Better for returns with multiple elements
- Can have key prop (full syntax only)

**Use Cases:** Returning multiple elements, table rows, list items

---

## 42. What is StrictMode?

**Answer:** StrictMode is tool for highlighting potential problems in application.

**Features:**
- Identifies unsafe lifecycles
- Warns about legacy string ref API
- Warns about deprecated findDOMNode
- Detects unexpected side effects
- Detects legacy context API

**Behavior:**
- Development mode only
- No visible UI
- Activates checks for descendants

---

## 43. What is reconciliation?

**Answer:** Reconciliation is algorithm React uses to diff one tree with another to determine what needs to change.

**Process:**
1. Compare element types
2. If different type, replace entire tree
3. If same type, update attributes
4. Recursively process children using keys

**Optimization:**
- Keys help identify which items changed
- Efficient diffing algorithm
- Minimal DOM manipulations

**Complexity:** O(n) instead of O(n³)

---

## 44. What are synthetic events?

**Answer:** Synthetic events are React's cross-browser wrapper around browser's native event.

**Features:**
- Same interface as native events
- Work identically across all browsers
- Event pooling (removed in React 17)
- Better performance
- Normalized behavior

**Difference from Native:** Prevents browser inconsistencies, automatic cleanup

---

## 45. What is server-side rendering (SSR)?

**Answer:** SSR renders React components on server and sends HTML to client.

**Benefits:**
- Better SEO
- Faster initial page load
- Better performance on slow devices
- Social media sharing with preview

**Drawbacks:**
- Server load
- More complex setup
- Longer Time to First Byte (TTFB)

**Frameworks:** Next.js, Gatsby

---