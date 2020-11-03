# faux-tray-menu

Example of a faking a right-click menu on a tray icon with a frameless window

This is a placeholder repo for an idea.


## The problem

In NW.js v0.34.0-beta a bug was introduced that causes the taskbar to display NW.js when you open a context menu on a tray app.

![Gif of the bug](https://user-images.githubusercontent.com/4629794/97620291-bfc66980-19f7-11eb-823c-2a39f32c7100.gif)

Currently the only solution is to use NW.js v0.33.4 or below. Idealy this bug would be fixed in NW.js itself, but in the mean time we could also build a workaround for it.


## The idea

The `tray` feature only supports a native menu on right-click (which causes this bug) and a `click` event on left-click. 

```js
tray.on('click', function (evt) {
  nw.Window.get().showDevTools();
  console.log(evt.x);
  console.log(evt.y);
});
```

Using the x,y coords, you could spawn a custom frameless window that simulates a menu at that location. Frameless windows with `show_in_taskbar: false` will not cause this issue. This approach would also allow for much greater control over the rendering and interactivity of the menu.
