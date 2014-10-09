Setup [node-webmaker-i18n](https://github.com/mozilla/node-webmaker-i18n#middleware) in your express.js app.

``` javascript
var i18n = require('webmaker-i18n');
...
app.use(i18n.middleware({
  supported_languages: [
    'en-US', 'th-TH', 'ru'
  ],
  default_lang: 'en-US',
  translation_directory: path.join( __dirname, 'locale' )
}));
```

This should be setup before `app.router` (express router).

You should also setup [stringsRoute](https://github.com/mozilla/node-webmaker-i18n#stringsroute) which is useful for client-side i18n

``` javascript
app.get( "/strings/:lang?", i18n.stringsRoute( "en-US" ) );
```