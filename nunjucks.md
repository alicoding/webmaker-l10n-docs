### getting started with Nunjucks i18n

#### Setup

Make sure you have setup **node-webmaker-i18n** if not see [express.md](./express.md) on how to do this step before you proceed.

After the setup you will be able to use `gettext` in your `ejs` template file.

#### Server

``` html
{{ gettext("View as Web App") }}
```

``` javascript
nunjucksEnv.addFilter("instantiate", function (input) {
  return nunjucks.renderString(input, this.getVariables());
});
```

If you have variable included in your translation.json file you have to use `instantiate` filter.

``` json
{
'key': 'My name is {{name}}'
}
```

```
{{ gettext("key") | instantiate }}
```


``` javascript
// `localVar` filter accepting two parameters
// one is the input from 'gettext()' and another is the function itself
// the use case is {{ gettext("some input") | localVar(object) }}
// if the key name is "some input": "My name is {{name}}"
// tmpl.render(localVar) will try to render it with the available variable from the
// `localVar` object and return something like `My name is Ali`
nunjucksEnv.addFilter("localVar", function (input, localVar) {
  return nunjucks.renderString(input, localVar);
});
```

If you have variable that is not part of the global or you want to override it by your own scope you can use `localVar` filter

``` json
{
  "Created by @username": "Created by @{{username}}",
}
```


``` html
<p class="author">{{ gettext("Created by @username") | localVar(make) }}</a>
```

#### Client

``` javascript
// Make the client-side gettext possible!!
nunjucksEnv.addFilter("gettext", function (string) {
  return this.lookup('gettext')(string);
});
```

```
<p>{{ "some key name" | gettext }}
```
