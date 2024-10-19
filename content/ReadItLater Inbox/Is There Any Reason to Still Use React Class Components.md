[[ReadItLater]] [[Article]]

# [Is There Any Reason to Still Use React Class Components?](https://medium.com/geekculture/is-there-any-reason-to-still-use-react-class-components-9b6a1e6aa9ef)

## A Look at Functional vs Class Components with React Hooks

Choose your character!

Nope.

Thanks for reading!

.

.

Oh I have to explain myself? Alright fine…

## Quick Background

So when I first learned React, you had to make a choice when creating a component. You could create the component as a simple function that returns some JSX (hence its called a Functional Component), or you could declare the component as a React.Component class inherited from the React library (hence why it’s called a Class Component).

The Functional Component was generally used for simpler components that would just display info passed into it, whereas a Class Component was what you would use when you needed to store state in your component, or if you wanted to do more fancy stuff like loading content asynchronously after the component mounted to the DOM.

That all changed in 2018 when the React team released [React Hooks](https://reactjs.org/docs/hooks-intro.html). Hooks are built in functions that perform preset duties such as giving your component the ability to store state (useState hook) or allowing you to perform side effects (useEffect hook) when loading your components, similar to lifecycle events such as componentDidMount in class components.

## Current State of React Hooks

As time has gone on, the community has moved more and more towards using React hooks, and a lot of the support is focused on them versus classes. Also, I’m seeing more and more the new waves of engineers coming out are focusing their time on learning hooks, and are being taught them before classes in school/bootcamps.

While the React team has no plans to deprecate the class components, I feel they are shifting their focus slowly away from them more and more each year. This is just my opinion, but I have a feeling that within the next few years they could stop supporting it completely.

The downsides of using classComponents is that they come with a bunch of preloaded stuff inside them whether you want it or not. If you are just using state in a Component for example, you are still loading all of the other stuff that comes along with it each time you render that component. As your code base grows bigger and bigger this means more data must be transferred on each page load and longer and longer rendering times.

With functional components the component starts out much lighter and you can add capabilities as you need them. Yes it may take a little bit more work when creating the component to go and import the useState and useEffect hooks, and to set each one up rather than having it preloaded for you, but that little bit of extra work could pay dividends in terms of app loading size and file size when you start expanding your application.

For most application, useState, useEffect, and useContext should cover about 99% of the things you would need a Class Component for. There are also [several more hooks](https://reactjs.org/docs/hooks-reference.html) for use in more specific applications. For those that are feeling really ambitious, here is an excellent video from Ben Awad on YouTube going over those additional hooks in more detail.

[www.youtube.com/watch?v=f687hBjwFcM](https://www.youtube.com/watch?v=f687hBjwFcM)

If you’re just starting out, I wouldn’t even worry about those extra ones yet and would just focus on mastering the main 3.

## Edge Cases Where You Have to Use Class Components

Of course like anything in software development, there are certain cases where you don’t have a choice and have to use classes although they are very rare.

In the rare case that you need access to any of

-   getSnapshotBeforeUpdate
-   getDerivedStateFromError
-   componentDidCatch

There are no direct React Hook equivalents yet, but apparently there are plans to develop these in the future in which case the answer to this articles title question will be a resounding NO.

## Final Verdict

**99.9% of the time you should be using Functional Components**. If you’ve been putting of learning React Hooks then you have some homework to do!