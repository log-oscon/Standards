# Dependencies

Version control is important, not only for the project itself, but also when it comes to your dependencies (which are basically other projects).

When using any dependency manager (NPM, Composer, etc.) one uses the version to fetch a dependent project at a certain state of its development. Take for instance the following examplo from a `composer.json` file.

```
require: {
  "wpackagist-plugin/some-plugin": "2.1"
}
```

Now, Composer (and many, if not all of the others) allows you to grab a depenedency with many version/tag keys. But history has shown us that using a specific (strict) version for your dependencies is the safest way to declare them.

This will make updating a little bit longer, but the benifits of control are much more important.
