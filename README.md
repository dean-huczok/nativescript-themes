# nativescript-themes
A NativeScript v3.0+ plugin to deal with UI Themes. This is a fork of Nathanael Anderson's original code, updated with code from [this issue](https://github.com/NathanaelA/nativescript-themes/issues/3) thanks to other GitHub users.

## License

This is released under the MIT License, meaning you are free to include this in any type of program -- However for entities that need a support contract, changes, enhancements and/or a commercial license please contact the original author Nathanael Anderson at [http://nativescript.tools](http://nativescript.tools).

He also does contract work; so if you have a module you want built for NativeScript (or any other software projects) feel free to contact him [nathan@master-technology.com](mailto://nathan@master-technology.com).

Nathanael Anderson's PayPal and Patreon links:
[![Donate](https://img.shields.io/badge/Donate-PayPal-brightgreen.svg?style=plastic)](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=HN8DDMWVGBNQL&lc=US&item_name=Nathanael%20Anderson&item_number=nativescript%2dthemes&no_note=1&no_shipping=1&currency_code=USD&bn=PP%2dDonationsBF%3ax%3aNonHosted)
[![Patreon](https://img.shields.io/badge/Pledge-Patreon-brightgreen.svg?style=plastic)](https://www.patreon.com/NathanaelA)


## Sample Snapshot
![Sample1](docs/themes.gif)


## Installation

This forked plugin is not yet registered on NPM, but the original is. Sorry.
To test it out, you can install the original first:

`tns plugin add nativescript-themes`

...and then replace its `themes.js` with the one from this repo.
But for production you'll want to do it properly... I'm sure you know what you're doing if you're at that level! (if not, Google/StackOverflow is your friend)


## Usage

To use the module you just `require()` it:

```js
var themes = require( "nativescript-themes" );
```

## Setup in App
Modify your startup app.js

```js
var themes = require('nativescript-themes');
themes.applyTheme(themes.getAppliedTheme('red-theme.css'));
```
This will automatically apply the "red-theme.css" theme if no other theme has ever been chosen as the default theme.



## You ask, how exactly does this help?
This allows you to dynamically theme an application just by calling the theme system.  Your master app.css file is applied first, then the theme file and finally your page.css

red-theme.css
```css
Button {
  background-color: red;
}
```

green-theme.css
```css
Button {
  background-color: green;
}
```


## What does this module actually do?
Digging deep inside the NativeScript core and poking it with a stick, it can change which CSS file your app uses.
So it will replace your original "app.css" with whatever you set it to. Understanding this will help you mitigate breaking your layout (set up your CSS structure accordingly).


## Why use this?
This allows you to apply a specific theme file globally so all pages get it.


## Demo
Demo shows three sample themes, and shows how to load the last chosen theme at startup.


### themes.applyTheme('cssFile', options);
**options.noSave** = _true_, this will cause it not to save this info for the getAppliedTheme to retrieve, this would typically used if you needed temporarily apply a theme.
```js
  var themes = require('nativescript-themes');
  themes.applyTheme('red-theme.css');
```


### theme.getAppliedTheme(<default_theme>);
This returns the last theme applied; if no theme has been applied it will use the default_theme.
```js
  var themes = require('nativescript-themes');
  var currentTheme = themes.getAppliedTheme('red-theme.css');
  if (currentTheme === 'red-theme.css') {
      console.log("We are using the default red-theme!")
  } else {
      console.log("We are using", currentTheme);
  }
```

## Tutorials

Need some extra help getting started?  Check out these tutorials for dealing with NativeScript UI themes in an iOS and Android application.

* [Changing the UI Theme in a NativeScript Angular Application](https://www.thepolyglotdeveloper.com/2016/11/changing-a-nativescript-css-skin-at-runtime/)
