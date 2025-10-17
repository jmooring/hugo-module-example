# Hugo Module &ndash; Example

This is an example of a Hugo module that provides two shortcodes:

- `green.html` renders the inner Markdown in green
- `red.html` renders the inner Markdown in red

Neither shortcode uses inline styling. Instead, both call the `inject-style-element` partial, which dynamically inserts a shortcode-specific `style` element into the document's `head` element.

The module employs the `hugo-module-example` subdirectory structure as a namespace to prevent naming conflicts with other templates.

```text
layouts/
├── _partials/
│   └── hugo-module-example/
│       └── inject-style-element.html
└── _shortcodes/
    └── hugo-module-example/
        ├── green.html
        └── red.html
```

Requires Hugo v0.146.0 or later.

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

To call the shortcodes:

```text
{{< hugo-module-example/green >}}
This is a **strong** word.
{{< /hugo-module-example/green >}}

{{< hugo-module-example/red >}}
This is an _emphasized_ word.
{{< /hugo-module-example/red >}}
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
