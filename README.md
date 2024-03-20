# Hugo Module Example

This is an example of a Hugo module that provides partial and shortcode templates.

```text
layouts/
├── partials/
│   └── hme/
│       └── greeting.html
└── shortodes/
    └── hme/
        └── greeting.html
```

The `hme` subdirectory provides a namespace to avoid collisions with other modules, themes, or custom templates.

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
