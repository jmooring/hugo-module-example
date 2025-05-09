# Hugo Module &ndash; Example

This is an example of a Hugo module that provides:

- partial templates
- shortcode templates
- a Sass file
- a site configuration file

```text
./
├── layouts/
│   ├── _partials/
│   │   └── hme/
│   │       └── greeting.html
│   └── _shortcodes/
│       └── hme/
│           └── greeting.html
├── miscellaneous/
│   └── sass/
│       └── bar/
│           └── _index.scss
├── LICENSE
├── README.md
├── go.mod
└── hugo.yaml
```

The `hme` subdirectory provides a namespace to avoid collisions with other modules, themes, or custom templates.

Requires Hugo v0.146.7 or later.

## Configuration

To add this module to your project, initialize your project as a Hugo module:

```sh
hugo mod init foo
```

In the above, `foo` is typically something like `github.com/user/project`.

Then add this to your site configuration:

```toml
[[module.imports]]
path = 'github.com/jmooring/hugo-module-example'
```

## Usage

To use the greeting partial:

```go-html-template
{{ partial "hme/greeting.html" "John" }}
```

To use the greeting shortcode:

```go-html-template
{{< hme/greeting John >}}
```

## Inspection

To inspect the module components:

```sh
hugo mod vendor
```

This will "vendor" all of the module dependencies into a `_vendor` directory in the root of your project. When you build your site, Hugo looks for modules in the `_vendor` directory, falling back to the module cache.

When you have finished inspecting the files, remove the `_vendor` directory so that you can update the module as needed.

## Update

To update the module to the latest version:

```sh
hugo mod get -u github.com/jmooring/hugo-module-example
```

To update the module to a specific version:

```sh
hugo mod get -u github.com/jmooring/hugo-module-example@v0.1.0
```

To update all modules to the latest version:

```sh
hugo mod get -u ./...
```
