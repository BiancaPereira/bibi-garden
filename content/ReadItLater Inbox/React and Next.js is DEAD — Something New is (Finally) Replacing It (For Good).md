[[ReadItLater]] [[Article]]

# [React and Next.js is DEAD — Something New is (Finally) Replacing It (For Good)](https://javascript.plainenglish.io/react-and-next-js-is-dead-something-new-is-finally-replacing-it-for-good-c792c48806f6)

Is this the beginning of the next revolution for JavaScript Framework? Apparently, YES!

Photo by [JC Gellidon](https://unsplash.com/@jcgellidon?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)

The paradox in web development is that more JavaScript is required to implement the features that your customers desire. However, less JavaScript is required to make your site load fast.

As a developer, you will always be crushed in the middle trying to strike a balance between the two.

What if I told you that you could write as much JavaScript as you want — gigabytes of it — and still not worry about your app’s performance?

What if I told you that every prominent web framework you have used up to this point is fundamentally flawed by design? They expect you to act in a way that will make your life difficult.

JavaScript is ***inevitable***.

It’s time to accept this reality and simplify your life (for the better).

## The Mess We Are In (That Nobody Tells You)

> The masses are always wrong…Wisdom is doing everything the crowd does not do. All you do is reverse the totality of their learning and you have the heaven they’re looking for.
> 
> — Charles Bukowski

We are too stubborn to acknowledge the fact that the web development situation (currently) is a mess.

We long ago concluded (a blunder) that sending HTML (client to server) was too expensive and began developing (even worse) alternatives.

All these years, we have been developing various frameworks — we have been fighting with the *very* foundation on which the web was built.

Allow me to show you the entire picture, and you will understand (exactly) what I mean.

In a typical web application, we send server-side rendered HTML to the client (may God have mercy on those SPA people), and the client renders it (until then, it is inert) — you *cannot* **interact** with it.

The next thing the browser does is: It downloads the application (JavaScript parts) for your page.

And finally, it executes the application (attaching listeners) — you *can* **interact** with it now.

The browser executes the application means it is attaching listeners (visualized as black boxes) which gives us interactivity.

Despite sending the entire structure (including the view) to the client, we still have to wait for it to become interactive.

The start-up time is unnecessarily ***increased*** by the whole process — Surely this is a problem, isn’t it?

The main reason websites take so long to load is that they have to start from scratch each time.

We call that ***hydration*** (we have fancy names for everything) — What we mean is that the browser is reading the JavaScript parts and determining which sections of the code belong where (attaching listeners) on the web page.

Well, Som — If that’s the issue, can’t we fix it by lazy loading everything? (I can hear you say that).

We can do that, but it is not the solution (as most people think).

After we send server-side HTML and the client downloads and executes it, we try to lazy load the web app in particular chunks.

WebApp (with Lazy load) doesn’t load applications all at once.

Well, guess what?

When the system comes across the lazy loaded boundary and because the component is ***visible***, it has no choice but to go back and request the lazy loaded components, download them and finish hydration.

This fails the very purpose we used lazy load in first place

Lazy loading is only useful in the existing systems, and for the components that are currently not in your render tree because you don’t need context in that case.

For the components that are currently in your render tree, lazy loading is a distraction.

People don’t realize this, and when you say that your application is too big. They will say “*Ah! just lazy load everything and it will be fine.*”

They don’t realize that actually, it’s not that ***easy***, specifically because of the problem we just discussed.

We also have these island architectures (popularised by Astro)

Where instead of hydrating everything at the beginning (which is kind of expensive), We hydrate when the client goes and interacts with the particular component.

So, If I interacted with the menu, I only meant to hydrate the menu, if I interact with any particular components, I only hydrate that, not the whole app.

Astro

This is an *improvement*.

But these islands are still relatively big. And inter-island communication becomes a problem because you just turned your component into an island, an island is an application. Now you have an inter-application communication problem that you need to solve in some way.

Now, Comes **Qwik**.

When I go and interact with a *specific* component, only that *specific* component gets resolved.

Specifically, observe that ***neither*** the parents ***nor*** the children of the component had to be resolved in this instance (unlike what occurred in the case of Astro).

Qwik says, “*I just need to do this guy and nothing else*.”

Qwik is also intelligent enough to recognize when one component is dependent on another (Imagine ***add to cart* 🛒** button in an e-commerce app) and wake up the dependent component.

Qwik Solves the inter-island communication problem

If we open the Network tab, we’ll find zero JavaScript on the initial page load.

Having no JavaScript showed up on this particular page, is not that impressive. Any framework can do this (if you are asking for a static page).

What makes QWIK special is that it figured this out on its own.

It essentially just looked up your code and said, “*Actually, you don’t need any JavaScript over here, I’m not even going to bother sending it.*”

You’ll notice that JavaScript is not loaded until we click the button.

When I click `Hello`, only the piece of code that contains the `console.log(Hello)` shows up. Nothing else!

A “sprinkle” of JS doesn’t take long to become a waterfall. As your sprinkles grow, your load times won’t. Qwik lets you write as much JavaScript as your heart desires without the burden of bundle size or slow performance.

Next.js vs Qwik (on a 3G network)

Additionally, it is clever enough to [*prefetch*](https://qwik.builder.io/docs/advanced/prefetching/) files in the background for users on sluggish networks.

Qwik-powered apps are interactive from the start.

You can achieve incredible app performance without even thinking about it.

## Ingenuity is Often Disguised as Magic

It was such a magical moment for me when I came to know about Virtual Machines. “***What? This can’t be True — You can run an OS inside an OS?****”* I thought to myself.

But what looked magic to me was pure technology underneath.

I could boot up Linux inside of my Windows machine itself was incredible for me.

But that’s not the thing that excited me.

You could bootup Linux, log in, open up an app (say word processor), and start typing and then at some point, you save the virtual machine, and take the file that you saved, send it to your friend.

When my friend opens up the file and resumes the machine, the machine is exactly where I left off.

You don’t have to go through the bootup process over again. You don’t go through the opening up of the word processor, you don’t go through typing the letter, you are just *exactly* where I left off with the letter open and ready to take on the next character.

That’s what grabbed my attention.

That’s exactly what’s happening here with **QWIK**.

The application starts on a server. It gets itself to a particular state. We snapshot the state, we send the state in the form of an HTML into the client, and on the client, we continue where we left off, right?

Essentially, if you think about the reason why websites are slow to start, is because we have to boot up. The reason it’s slow is that you’re paying for the bootup — Hydration — as we already saw.

We say, “*Oh! The Website is still loading”* but fundamentally, the website is booting up, this is what’s happening — isn’t it?

The reason why QWIK applications are fast to start is that they skipped the bootup, they get you to the exact state that it was on a server and continue where you left off.

It contains the code we want to execute, and also has access to the lexical environment to update states that might be shared by other components, which itself comes from another lazy loaded chunk.

> “The Best Code is No Code at All”

Qwik is not fast because it is efficient, but it is fast because it is good at avoiding work!

It brings an entirely new rendering paradigm to the table called ***resumability*** (which eliminates the need for hydration.)

How we develop (now) ***vs*** the way **Qwik** is offering

This is exactly how we stream movies online, but here we are doing it in a non-linear fashion. The user decides which part of the application they **want** *and* **when** — that’s why we are calling it *resumable*.

Qwik opens up a whole new world of possibilities. You can, for example, render your page on multiple backend edge services and assemble it as a single response.

Watch This 👆 If you want to be a part of the future of web development!

## Conclusion

Thousands of years ago, Gautama — The Buddha told us to choose a middle path. We developers are too stubborn, we still choose to go to extremes.

There is one tribe that tells you to go all JavaScript (every other SPA), there is one tribe that tells you not to choose JavaScript at all (WebSocket-based frameworks, like LiveView), and there is the rest of it which lets you use JS at the burden of the bundle size (and at the cost of performance).

Qwik is a breath of fresh air in all of these, it is nothing like we have ever used before.

I am not here to evangelize any framework, but we have to acknowledge the fact that this approach is revolutionary.

I wish more frameworks would come up with this approach.

This approach is the way forward, otherwise, we would be going on in loops forever.

## Note of Gratitude

I wanted to take this last opportunity to say thank you.

Thank you for being here! I would not be able to do what I do without people like you who follow along and take that leap of faith to read my post.

I hope you’ll [**join me**](https://polymathsomnath.medium.com/subscribe) in [**my future blog post**](https://polymathsomnath.medium.com/subscribe) and stick around because I think we have something great here. And I hope that I will be able to help you along in your career for many more years to come!

See you next time. Bye!