## Purpose

**Barchart documentation CLI** allows you to create documentation from the following sources:

* JSDoc
* OpenAPI v3 specification

The CLI uses [Docsify](https://github.com/docsifyjs/docsify) to convert Markdown documentation to HTML.

## Documentation structure

The documentation folder has following structure:

```text
├── docs
│   ├── content
│   │   ├── api
│   │   ├── concepts
│   │   ├── releases
│   │   └── sdk
│   ├── static
│   └── styles
``` 

* `docs` — Root `Docsify` folder. Github pages use it to host documentation website.
* `content` — Stores documentation. All generated and manual documentation should be stored here.
* `api` — Stores documentation that generated from OpenAPI.
* `concepts` — Stores a custom documentation that describe key concepts.
* `releases` — Stores all release notes.
* `sdk` — Stores documentation that generated from JSDoc.
* `static` — Stores static files that can be downloaded, for example: OpenAPI file.
* `styles` — Stores custom `CSS` styles.

## Docsify

Docsify allows ignoring headers by adding `{docsify-ignore}` after the header.

**Example**:
```markdown
# Header {docsify-ignore}
```

### Sidebar

The sidebar stores in the `_sidebar.md` file. It can be updated manually. There are custom sidebars that will be generated by the CLI for the API and SDK folders. 

!> The Sidebar file contains comments like `<!-- api_open --><!-- api_close -->` which shouldn't be deleted. The CLI uses those comments to generate custom sidebars for the `sdk` and the `api` folders.

Learn more about Docsify [here](https://docsify.js.org/#/helpers)

### Coverpage

The coverpage is a landing page for a documentation. The CLI generates the file `docs/_coverpage.md` once when the first time `generate` or `init` commands are called.

### Website

The `index.html` file is an entry point to a documentation website. It contains a `docsify` configuration. The CLI generates the file `docs/index.html` once when the first time `generate` or `init` commands are called. Learn more about `docsify` documentation [here](https://docsify.js.org/#/configuration).


### Custom CSS Styles

Custom CSS styles are located in the file `docs/styles/override.css`.

## Release notes

All release notes should be inside the `releases` folder and stored as separate files. File names must contain a semantic version. All files will be combined to the `releases_notes.md` file. Names of files will be used like subheaders inside `releases_notes.md`. All release files shouldn't contain any markdown headers.

**Example**:

```text
├── docs
│   ├── content
│   │   ├── releases
│   │   │   ├── 0.0.1.md
│   │   │   └── 0.0.2.md
```