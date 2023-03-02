# Discord-Blocked-Blocker

![icon](https://github.com/aschuhardt/Discord-Blocked-Blocker/raw/master/icon.png)

This is an extension for the Google Chrome web browser.

Hides the "Blocked" messages that appear in Discord's IM interface when a user you have blocked sends a message.

Unfortunately the way discord presents the elements now makes it difficult to hide via simple CSS rules.
For instance, a blocked message will show like this:

```html
<div class="groupStart-3Mlgv1">
  <div class="wrapper-30-Nkg compact-2Nkcau zalgo-26OfGz" role="article">
    <div class="contents-2MsGLg">
      <div class="blockedSystemMessage-3FmE9n container-x059i8 compact-3bMNvi">
      </div>
    </div>
  </div>
</div>
```

And at least the `wrapper` div should be hid in order to effectively hide the message.

It should be enough if a JavaScript could be hooked to DOM changes, to get every `<div class="blockedSystemMessage-*"` DOM handle, then apply `display:none` to the DOM element two levels above it, but that'd be a bit more complex.

For now, this improves the situation:

```css
div[class^="groupStart-"]
div[class*="wrapper-"]
div[class^="contents-"]
div[class*="blockedSystemMessage-"] {
  display: none
}
```
