[[ReadItLater]] [[Article]]

# [GitHub - spotify/should-up: Remove most of the "should" noise from your tests](https://github.com/spotify/should-up)

## Should Up

Remove all those "should" prefixes cluttering up your JS unit test descriptions!

When you run `should-up`, it'll go through all the files in the directory you specify, cleaning up as many test descriptions as it can. Afterwards, the changes should look something like this.

| Before | After |
| --- | --- |
|   ``` describe('TodoApp', () => {   it('should store reminders in local storage');   it('should set reminders as done when clicked');   it('should sync with the cloud'); }); ```     |   ``` describe('TodoApp', () => {   it('stores reminders in local storage');   it('sets reminders as done when clicked');   it('syncs with the cloud'); }); ```     |

## Installation

## Usage

```
should-up /path/to/your/tests
```

## Rationale

As you can see from the following highly scientific table of data, there's a pretty strong negative correlation between the readability of your test descriptions and the amount of meaningless filler in them.

| Readability | Amount of meaningless filler |
| --- | --- |
| **Total Disaster**   ⭐️ |   ``` Widget   ✓ should always correctly contain a button whenever appropriate   ✓ should always correctly dispatch an event on click whenever appropriate   ✓ should always correctly show the name of the user whenever appropriate   ✓ should always correctly show the type of widget  whenever appropriate ```     |
| **Still Very Bad**   ⭐️⭐️ |   ``` Widget   ✓ should always correctly contain a button   ✓ should always correctly dispatch an event on click   ✓ should always correctly show the name of the user   ✓ should always correctly show the type of widget ```     |
| **You Are Here →**   ⭐️⭐️⭐️⭐️ |   ```  Widget   ✓ should contain a button   ✓ should dispatch an event on click   ✓ should show the name of the user   ✓ should show the type of widget ```     |
| **All Killer No Filler**   ⭐️⭐️⭐️⭐️⭐️ |   ``` Widget   ✓ contains a button   ✓ dispatches an event on click   ✓ shows the name of the user   ✓ shows the type of widget ```     |

Anyway, when we start everything with the word "should", it sounds like we're not really 100% sure about what our code does. Like maybe we're even a little bit pessimistic that it works at all, but we're crossing our fingers and hoping for the best anyway.

> Well... it *should* dispatch an event on click, but I dunno. Just... look, you can run it if you want, but don't come to me if it breaks is all I'm saying.

When you say something like `it('dispatches an event on click')` instead, it's literally a more enjoyable thing to write. It makes you feel like you're more certain about what your code's doing, and also more proud of your concise new unit test descriptions.

## Contributing

This project adheres to the [Open Code of Conduct](https://github.com/spotify/code-of-conduct/blob/master/code-of-conduct.md). By participating, you are expected to honor this code.

## License

[Apache 2.0](https://github.com/spotify/should-up/blob/master/LICENSE)