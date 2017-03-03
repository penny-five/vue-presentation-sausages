# vue-sausages

Demo app for my presentation at Web Dev & Sausages vol.2 w/TampereJS meetup.

This demo showcases the declarative nature of Vue.js and the usage of computed properties. By pushing a new value to an array we cause a chain reaction where multiple computed properties are recomputed and the UI is rerendered.

Branch called `jsx` has slighty modified version of the app that implements a render function using `jsx`. This modified version demonstrates how render function isn't even called if the data that was mutated wasn't "touched" during the previous render.

Presentation slides are available [here](https://www.slideshare.net/JoonasLehtonen2/vuejs-is-boring-and-thats-a-good-thing).
