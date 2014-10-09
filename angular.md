### getting started with Angularjs i18n

#### Setup

Make sure you have setup **node-webmaker-i18n** if not see [express.md](./express.md) on how to do this step before you proceed.

Download [i18n.js](https://github.com/mozilla/webmaker.org/blob/master/public/js/angular/i18n.js) and include in your Angularjs dependency

All strings should be included in [locale/<en_US>/translation.json](/locale/en_US/translation.json).

The format is slightly different than how we do it in Webmaker apps and this is the [chrome-i18n](./chrome-i18n.md) format

To localize string in template file you have three options:

1. `{{ '_some_key_name_' | i18n }}`
  This will check the translation file and look for that specific key name and return the message. If key name not found it will return **unkown key: "_some_key_name_"**.

2. `<span ng-bind-html="'_some_key_name' | i18n"></span>`

  This method is useful when you have some markup.

3. `<span bind-unsafe-html="'_some_key_name' | i18n"></span>`

  This method is useful when you have some variable inside your string for instance: "My name is {{name}}."
