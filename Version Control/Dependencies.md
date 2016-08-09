# Dependencies

Version control is important, not only for the project itself, but also when it comes to your dependencies (which are basically other projects).

When using any dependency manager (NPM, Composer, etc.) one uses the version to fetch a dependent project at a certain state of its development. Take for instance the following example from a `composer.json` file.

```
require: {
  "wpackagist-plugin/some-plugin": "2.1"
}
```

Now, Composer (and many, if not all, of the other managers) allows you to grab a dependency with many version/tag keys. Furthermore, the values you define can be enhanced for greater ease in update dependencies. For example, you can define the specified version as the minimum version you need and allow for updates with a simple command.

```
require {
    "wpackagist-plugin/some-plugin": "^2.1"
}
```

Not all of the options are the same, but the possibilities are highlighted on semver's documentation for npm: [semver](https://docs.npmjs.com/misc/semver).

This is incredibly versatile and allows developers to do a lot of things. However, it can also become troublesome and "dangerous" really fast.

History has shown us that, as your project grows (dependencies, people in contact with it, time lapsed since version 1.0, etc.) managing the dependencies and their impacts becomes a very sensitive issue. Also, we can't trust that the latest version of any dependency won't break our project.
Because of this, and to give us more security when updating you should use a specific (strict) version for your dependencies.

```
require: {
    "wpackagist-plugin/some-plugin": "2.1.2"
}
```

This will make updating take a little bit longer, but you get the "forced" chance to review any changes to a dependency, test them, and finally push the updated version to be used.
