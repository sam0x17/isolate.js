# isolate.js

Isolate.js is a JavaScript plugin that allows you to define isolated CSS "namespaces"
which you can turn on and off on the fly from JavaScript or within different portions
of your document markup. This is extremely useful for scenarios where you want to use
CSS styles from multiple sources that conflict with one another.

When you include a CSS file, you can specify the namespace you want it to live in like
this:
```html
<link rel="stylesheet" type="text/css" data-namespace="bootstrap" href="style/bootstrap.css">
```

This will cause any CSS classes defined in `bootstrap.css` to be suppressed _unless_
you manually specify that for some portion of your document or JavaScript code you
want to "use" your custom `boostrap` namespace. You can enable the `bootstrap` namespace
you just created from your document markup as follows:
```html
<!-- code out here cannot use bootstrap styling -->
<div data-namespace="bootstrap">
  <!-- code within this block can use bootstrap styling -->
</div>
<!-- code out here also cannot use bootstrap styling -->
```

You can also enable/disable a namespace from within JavaScript:
```JavaScript
// bootstrap styles not visible
uses('bootstrap')
// bootstrap styles visible
end_uses()
// bootstrap styles not visible
```

Alternatively, you can do this callback-style:
```JavaScript
// bootstrap styles not visible
uses('bootstrap', function() {
  // bootstrap styles visible
})
// bootstrap styles not visible
```
