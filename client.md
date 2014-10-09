### getting started with JavaScript client side only i18n

#### Setup

Make sure you have setup **node-webmaker-i18n** if not see [express.md](./express.md) on how to do this step before you proceed.

Download and include [localized.js](https://github.com/mozilla/node-webmaker-i18n/blob/master/localized.js) in your HTML file.

``` bash
$ bower install webmaker-i18n
```

``` html
<!DOCTYPE html>
<html lang="en-US" dir="ltr">
<head>
  ...
  <script src="bower_components/webmaker-i18n/localized.js"></script>
```


#### AMD Usage
``` javascript
require(['path/to/localized'], function(localized) {
  // Don't do anything until the DOM + localized strings are ready
  localized.ready(function(){
    var someText = localized.get('some key');
  });
});
```

#### Global Usage

``` javascript
// Don't do anything until the DOM + localized strings are ready
Localized.ready(function(){
  var someText = localized.get('some key');
});
```
