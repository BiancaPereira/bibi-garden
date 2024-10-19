[[ReadItLater]] [[Article]]

# [Understanding React Fiber Architecture - DZone Web Dev](https://dzone.com/articles/understanding-of-react-fiber-architecture)

Join the DZone community and get the full member experience.

[Join For Free](https://dzone.com/static/registration.html)

![](https://dz2cdn1.dzone.com/storage/temp/12848218-pic-yarn-in-pile.jpg)

React 16.0 was released with an update to the React core algorithm. This new core architecture is named “[*Fiber*](https://dzone.com/articles/react-16-release-whats-new)*.*” Facebook has completely rewritten the internals of React from the ground-up while keeping the public API essentially unchanged; in simple terms, it means only changing the engine of a running car.

With this release, some new features are also added, like Asynchronous Rendering, Portals, Error Boundaries, Fragments (i.e. return array of elements). Incremental rendering is the headline addition to React, which adds the ability to split rendering work into chunks.

*React Fiber* is the new reconciliation algorithm. Reconciliation is the process of comparing or diffing old trees with a new tree in order to find what is changed or modified. In the original reconciliation algorithm (now called Stack Reconciler), the processing of component trees was done synchronously in a single pass, so the main thread was not available for other UI related tasks like animation, layouts, and gesture handling. Fiber Reconciler has different goals:

-   Ability to split interruptible work in chunks.
-   Ability to prioritize, rebase, and reuse work in progress.
-   Ability to yield back and forth between parents and children to support layout in React.
-   Ability to return multiple elements from `render()`.

**Sierpinski triangle** rendering using Stack and Fiber:

-   [Fiber Example](https://claudiopro.github.io/react-fiber-vs-stack-demo/fiber.html).
-   [Stack Example](https://claudiopro.github.io/react-fiber-vs-stack-demo/stack.html).

> **You may also like: [Everything React: Tutorials for Beginners and Experts Alike](https://dzone.com/articles/everything-react-tutorials-for-beginners-and-exper).**

In the above example, there are two different kinds of updates going on — one that makes the triangle narrow and wide which has to happen every 16ms (60 FPS) in order for the animation to look smooth and one that updates the numbers contained inside every single dot, which happens approximately every 1000ms.

A *fiber* (not Fiber with a capital ‘F’) is a JavaScript object that contains information about a component, its input, and output. At any time, a component instance has at most two fibers that correspond to it: the current fiber and the work-in-progress fiber. A fiber can be defined as a unit of work.

**Fiber prioritizes work on 7 levels:**

1.  NoWork – no work is pending.
2.  SynchronousPriority – for controlled text inputs. Synchronous side-effects.
3.  TaskPriority – completes at the end of the current tick.
4.  AnimationPriority – needs to complete before the next frame.
5.  HighPriority – an interaction that needs to complete pretty soon to feel responsive.
6.  LowPriority – data fetching, or result from updating stores.
7.  OffscreenPriority – Won’t be visible but do the work in case it becomes visible.

**React Fiber performs reconciliation in two phases: Render and Commit**

**1\. Lifecycle methods called during render phase:**

-   `UNSAFE_componentWillMount()`
-   `UNSAFE_componentWillReceiveProps()`
-   `getDerivedStateFromProps()`
-   `shouldComponentUpdate()`
-   `UNSAFE_componentWillUpdate()`
-   `render()` 

**2\. Lifecycle methods called during commit phase:**

-   `getSnapshotBeforeUpdate()`
-   `componentDidMount()`
-   `componentDidUpdate()`
-   `componentWillUnmount()` 

The earlier whole reconciliation process was synchronous (recursive), but in Fiber, it is divided into two phases. Render phase (a.k.a. Reconciliation phase) is asynchronous, so three of the lifecycle methods were marked unsafe because putting the code with side-effects inside these methods can cause problems, as lifecycle methods of different components are not guaranteed to fire in a predictable order.

React Fiber uses `requestIdleCallback()` to schedule the low priority work and `requestAnimationFrame()` to schedule high priority work.

**Problems with Current Implementation:**

-   Long-running tasks cause frame drops.
-   Different tasks have different priorities.

**So in a nutshell, what makes Fiber interesting?**

-   It makes apps more fluid and responsible.
-   In the future, it could parallelize work a.k.a. Time Slicing.
-   It would improve startup time while rendering components using React Suspense.

Fiber is currently available for use but it runs in compatibility mode with the current implementation.

## Further Reading

-   Evolution of React on a Timeline.
-   React.js Essentials.
-   How to Learn React.js, Part 1: The React Road Map for Modern Web Developers.

React (JavaScript library) Architecture