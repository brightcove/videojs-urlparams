# Video.js URL Params

This plugin reads the containing page's URL to determine what time to seek to at the start and whether to automatically beging playing.

## Using the Plugin

The plugin registers itself when you include video.urlparams.js in your page:

    <script src='videojs.urlparams.js'></script>

Once you have your video object, you can activate the URL Params plugin.

    video.urlParams();

The plugin takes an optional `options` object.
If an `options` object is provided with a `url` property, that value will be treated as the URL for extracting the time to which to seek.
The default is to use the value of `window.location.href`;

    video.urlParams({
      url: "http://some.url/goes/here#t=2h16m32s"
    });

The URL is inspected for two parameters:

 * the `t` parameter is used for the time to which to seek, and
 * the presence of the `autoplay` parameter indicates that the player should begin playing immediately (if possible).

The value for the `t` parameter should consist of some amount of time in hours, minutes and/or seconds.
For example, all of the following are valid values:

 * t=2h
 * t=2h16m
 * t=16m
 * t=16m32s
 * t=32s

The parameters may appear virtually anywhere in the URL, on either side of the `#` mark if present.

The autoplay parameter does not need a value (e.g. `autoplay=1`).
The simple presence of the string `autoplay` is all that is required.
