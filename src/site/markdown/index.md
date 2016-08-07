# Test to show the Velocity tools bug in Maven Site plugin 3.5

This is a test meant to show the Velocity tools bug which appeared in Maven 3.5. This bug stops custom Velocity tools from being loaded, breaking any Maven Skin which may depend on this feature.

For more information check the [Maven Site Plugin issue][issue].

## Usage

This is just a test for the Maven Site, to use it just run the usual Maven Site command:

```
$ mvn install
```

Then check the target folder for the generated site.

## Branches

There are two branches for this project, one using Maven Site v3.4, which works correctly, and another using Maven Site v3.5.1, which breaks the Maven site.

## Changing the Maven Site Plugin version

The Maven Site Plugin version is set on the parent POM. But it can be changed overwriting the plugin.site.velocity.version property. This has already been done in the project to allow quickly changing versions.

## Noticing the errors

The custom Velocity Tools used by the skin change the HTML code of the page, and while some of these changes can be hard to notice, a few can be seen with ease in the index page:

- The heading number will break, and the text will appear in the line after the number
- The header will contain additional menus, as the general info menu will be appended to it
- The footer will contain additional menus, as the documentation menu will be appended to it
- The releases repositories list will appear empty
- The "tested on" section won't appear in the footer

If any of these things appear on the page, that means the custom Velocity tools have stopped working.

## Getting the skin and tools

In case the Maven Skin or the custom Velocity tools used for the tests are needed, they can be found in the following links:

- [Maven Skin][skin]
- [Custom Velocity tools][tools]

[issue]: https://issues.apache.org/jira/browse/MSITE-782

[skin]: https://github.com/Bernardo-MG/docs-maven-skin
[tools]: https://github.com/Bernardo-MG/maven-site-velocity-bug
