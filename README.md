# Awesome Carve [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of Carve resources, tools, editors, and libraries.

[Carve](https://github.com/markup-carve/carve) is a post-Markdown lightweight markup language with visual mnemonics and human-centered design. It builds on [Djot](https://djot.net/)'s technical rigor — linear parsing, no expressive blind spots, arbitrary attributes — while adding visual mnemonics (`/italic/`, `*bold*`, `_underline_`, `~strike~`) and conventions that match how non-technical users naturally mark up text.

## Contents

- [Official Resources](#official-resources)
- [Specification](#specification)
- [Parsers & Libraries](#parsers--libraries)
- [Editors & IDE Support](#editors--ide-support)
- [Tools](#tools)
- [Converters](#converters)
- [Migration](#migration)
- [Roundtrip Conversion](#roundtrip-conversion)
- [Framework Integration](#framework-integration)
- [CMS Integration](#cms-integration)
- [Documentation Tools](#documentation-tools)
- [Static Site Generators](#static-site-generators)
- [Syntax Highlighting](#syntax-highlighting)
- [Sandboxes](#sandboxes)
- [Example Sites](#example-sites)
- [Learning Resources](#learning-resources)
- [Community](#community)

## Official Resources

Documentation and reference materials for Carve.

- [carve](https://github.com/markup-carve/carve) - Language definition, philosophy, and quick reference.
- [carve-js](https://github.com/markup-carve/carve-js) - Reference TypeScript implementation.
- [tree-sitter-carve](https://github.com/markup-carve/tree-sitter-carve) - Native Tree-sitter grammar for Carve.
- [carve-lsp](https://github.com/markup-carve/carve-lsp) - Language server for diagnostics and document symbols.

## Specification

Formal syntax specification and grammar definitions.

- [carve `grammar.ebnf`](https://github.com/markup-carve/carve/blob/main/resources/grammar.ebnf) - Normative EBNF grammar plus the PART 9 semantic constraints (the conformance authority).
- [Carve docs](https://markup-carve.github.io/carve/) - Rendered spec, examples, and edge-case reference.
- [Conformance test suite](https://github.com/markup-carve/carve/tree/main/tests/corpus) - The shared spec corpus: input `.crv` paired with expected `.html`, generated from `docs/examples.md`. Also emitted in the djot.js fenced format at [`tests/spec`](https://github.com/markup-carve/carve/tree/main/tests/spec), plus a feature-tagged Tier-2 set in `tests/corpus-optional`. Every implementation consumes it as a git submodule; new slugs are drift-guarded per impl.

## Parsers & Libraries

Language-specific implementations for parsing and rendering Carve.

### JavaScript / TypeScript

- [carve-js](https://github.com/markup-carve/carve-js) - Reference TypeScript implementation of the Carve markup language.

### PHP

- [carve-php](https://github.com/markup-carve/carve-php) - PHP parser and renderer with a `carve` CLI binary; implements the full Carve syntax and passes the spec corpus (forked from djot-php).

### Rust

- [carve-rs](https://github.com/markup-carve/carve-rs) - Rust parser and HTML renderer with a `carve` CLI binary; passes the upstream spec corpus.
- [carve-wasm](https://github.com/markup-carve/carve-wasm) - WebAssembly bindings for the Rust implementation.

### Python

- [carve-py](https://github.com/markup-carve/carve-py) - Python bindings (PyO3) over the carve-rs engine; `carve.to_html` plus Markdown, plain-text, and ANSI renderers and the extension toggles, output byte-identical to the carve-rs CLI. Installs as a native wheel via maturin.

### Go

- [carve-go](https://github.com/markup-carve/carve-go) - Pure-Go module (no cgo): embeds a WASI build of carve-rs and runs it via wazero. `ToHTML` output byte-identical to the carve-rs CLI.

### Ruby

- [carve-rb](https://github.com/markup-carve/carve-rb) - Native Ruby gem (magnus over carve-rs); `Carve.to_html(source, extensions:)`, output byte-identical to the carve-rs CLI.

<!-- Add additional language sections (Go, Ruby, …) as implementations land -->

## Editors & IDE Support

Syntax highlighting and editing support for popular editors.

- [intellij-carve](https://github.com/markup-carve/intellij-carve) - JetBrains IDE plugin (IntelliJ IDEA, PhpStorm, WebStorm, ...) for `.crv` and `.carve` files: TextMate-based highlighting, live split preview (carve-js or carve-php), HTML export, live templates, and custom preview CSS.
- [vscode-carve](https://github.com/markup-carve/vscode-carve) - VS Code extension for `.crv` and `.carve` files, with syntax highlighting, semantic tokens, diagnostics, and document symbols.
- [zed-carve](https://github.com/markup-carve/zed-carve) - Zed editor extension for `.crv` and `.carve` files, backed by the native Tree-sitter grammar.
- [emacs-carve](https://github.com/markup-carve/emacs-carve) - Emacs major mode (`carve-mode`) for `.crv` and `.carve` files: font-lock highlighting for the full syntax, `%%` comments, imenu heading index, and outline support.
- [vim-carve](https://github.com/markup-carve/vim-carve) - Vim and Neovim support: classic regex syntax highlighting that works with any colorscheme, plus Neovim Tree-sitter integration reusing the native grammar and queries.
- [sublime-carve](https://github.com/markup-carve/sublime-carve) - Sublime Text package with a `.sublime-syntax` highlighter authored from the shared TextMate grammar.
- [helix-carve](https://github.com/markup-carve/helix-carve) - Helix editor support: `languages.toml` entry and runtime queries backed by the tree-sitter-carve grammar.

## Tools

Command-line utilities for working with Carve documents.

- [carve-lsp](https://github.com/markup-carve/carve-lsp) - Language server for editor integrations and tooling that speaks LSP.
- [`carve` CLI (carve-php)](https://github.com/markup-carve/carve-php) - Convert `.crv` files to HTML (and import Markdown/HTML/BBCode/Djot) from the command line.
- [`carve` CLI (carve-rs)](https://github.com/markup-carve/carve-rs) - Fast native `.crv` to HTML converter binary.

### Validators & Linters

- [`carve lint`](https://github.com/markup-carve/carve-js#cli) - Validator in the carve-js CLI. Flags problems that parse but render wrong: broken `</#id>` cross-references, duplicate heading ids, trailing `{…}` heading attributes, legacy `raw FORMAT` fences, and block markers that leaked as plain text. Exits non-zero, so it works as a CI gate; the same checks surface live in editors via [carve-lsp](https://github.com/markup-carve/carve-lsp).

### Formatters

- [`carve fmt`](https://github.com/markup-carve/carve-js#cli) - Canonical Carve formatter, in the `carve` CLI of all three engines ([carve-js](https://github.com/markup-carve/carve-js), [carve-php](https://github.com/markup-carve/carve-php), [carve-rs](https://github.com/markup-carve/carve-rs)) with byte-identical output. Conservative, idempotent, and semantic-preserving (the rendered HTML is unchanged): normalizes whitespace, list markers, headings, fence lengths, and attribute spacing. `carve fmt -w` rewrites in place; `carve fmt --check` is a CI gate. The serializer is also exposed programmatically (`carveToCarve` / `to_carve`).

### Benchmarks

- [carve-bench](https://github.com/markup-carve/carve-bench) - Cross-engine render performance benchmarks: per-engine in-process timing harnesses (carve-js, carve-php, carve-rs) over a fixed document set, with an orchestrator that writes a results table. A speed comparison; correctness is covered by the shared conformance corpus.

## Converters

Render Carve to other output formats. All four reference engines ship the same renderer set, selectable by CLI flag or API.

- **Carve to HTML** - the default output of every engine: [carve-js](https://github.com/markup-carve/carve-js) `renderHtml`, [carve-rs](https://github.com/markup-carve/carve-rs) `carve --html`, [carve-php](https://github.com/markup-carve/carve-php/blob/main/src/Renderer/HtmlRenderer.php) `HtmlRenderer`, [carve-py](https://github.com/markup-carve/carve-py) `carve.to_html`.
- **Carve to Markdown** - [carve-js](https://github.com/markup-carve/carve-js) `renderMarkdown`, [carve-rs](https://github.com/markup-carve/carve-rs) `carve --markdown`, [carve-php](https://github.com/markup-carve/carve-php/blob/main/src/Renderer/MarkdownRenderer.php) `MarkdownRenderer`, [carve-py](https://github.com/markup-carve/carve-py) `carve.to_markdown`.
- **Carve to plain text** - [carve-js](https://github.com/markup-carve/carve-js) `renderPlain`, [carve-rs](https://github.com/markup-carve/carve-rs) `carve --plain`, [carve-php](https://github.com/markup-carve/carve-php/blob/main/src/Renderer/PlainTextRenderer.php) `PlainTextRenderer`, [carve-py](https://github.com/markup-carve/carve-py) `carve.to_plain_text`.
- **Carve to ANSI (terminal)** - [carve-js](https://github.com/markup-carve/carve-js) `renderAnsi`, [carve-rs](https://github.com/markup-carve/carve-rs) `carve --ansi`, [carve-php](https://github.com/markup-carve/carve-php/blob/main/src/Renderer/AnsiRenderer.php) `AnsiRenderer`, [carve-py](https://github.com/markup-carve/carve-py) `carve.to_ansi`.

## Migration

Tools for migrating from other markup formats to Carve.

- [carve-js `markdownToCarve`](https://github.com/markup-carve/carve-js) - Source-to-source Markdown → Carve converter (handles the inline syntax that differs from Markdown, blank-line block spacing, setext headings, and more).
- [carve-php converters](https://github.com/markup-carve/carve-php/tree/main/src/Converter) - Markdown, HTML, BBCode and Djot → Carve converters, with a `carve` CLI for converting files.

## Roundtrip Conversion

Tools supporting lossless bidirectional conversion for content editing workflows. Essential for WYSIWYG integration where content is stored as Carve but edited as HTML — changes made in the visual editor convert back to Carve without losing syntax choices or formatting details.

- [carve-php](https://github.com/markup-carve/carve-php) - Round-trip mode (data attributes for Carve to HTML to Carve) plus an `HtmlToCarve` converter for WYSIWYG editing workflows.

## Framework Integration

Carve support for web frameworks.

- [laravel-carve](https://github.com/markup-carve/laravel-carve) - Laravel package rendering Carve to HTML via carve-php: `@carve` / `@carveRaw` / `@carveText` Blade directives, a `Carve` facade with named converter profiles (including the static graceful-degradation mode), a `ValidCarve` validation rule, and content-hash render caching.
- [laravel-carve-demo](https://github.com/markup-carve/laravel-carve-demo) - Runnable Laravel app demonstrating every feature of laravel-carve: Blade directives, facade and named profiles, form validation, a safe-mode comparison, and the static graceful-degradation mode rendered side by side with the interactive output.
- [symfony-carve](https://github.com/markup-carve/symfony-carve) - Symfony bundle that renders Carve to HTML via carve-php: a `{{ value|carve }}` Twig filter, a `carve()` function, a `CarveRenderer` service, and configurable safe-mode sanitization.
- [symfony-carve-demo](https://github.com/markup-carve/symfony-carve-demo) - Runnable Symfony app demonstrating every feature of the symfony-carve bundle: Twig filter and function, the service, a live editor, a safe-mode comparison, and a syntax gallery.
- [vite-plugin-carve](https://github.com/markup-carve/vite-plugin-carve) - Vite plugin for importing `.crv` and `.carve` files as rendered HTML modules.
- [carve-grammars](https://github.com/markup-carve/carve-grammars) - Tiptap editor kit and Carve serializer for building WYSIWYG editors that read and write Carve (also ships Prism and highlight.js grammars; see Syntax Highlighting).
- [carve-components](https://github.com/markup-carve/carve-components) - React and Vue 3 `<Carve>` components (and a `useCarveHtml` hook/composable) that render Carve to HTML via carve-js, with per-framework subpath exports, SSR support, and safe-by-default raw-HTML escaping.

## CMS Integration

Carve plugins for content management systems.

- [wp-carve](https://github.com/markup-carve/wp-carve) - WordPress plugin (carve-php engine) with live in-browser preview, multi-format paste, frontmatter-to-meta, render caching, and a REST API.

## Documentation Tools

Generate documentation from Carve source files.

- [mkdocs-carve](https://github.com/markup-carve/mkdocs-carve) - MkDocs plugin that renders `.crv`/`.carve` pages via carve-py, with per-extension config and full nav/path support.

## Static Site Generators

Build static websites with Carve content.

- [astro-carve](https://github.com/markup-carve/astro-carve) - Astro integration: import `.crv`/`.carve` files into Astro pages and components as rendered HTML with frontmatter.
- [eleventy-carve](https://github.com/markup-carve/eleventy-carve) - Eleventy (11ty) plugin adding `.crv`/`.carve` as a template format, with Carve frontmatter flowing into the data cascade.
- [hugo-carve](https://github.com/markup-carve/hugo-carve) - Hugo preprocessor (via carve-go) that converts `.crv`/`.carve` content to HTML pages, preserving front matter. (Hugo has no markup-plugin API, so it is a convert-then-build step.)
- [jekyll-carve](https://github.com/markup-carve/jekyll-carve) - Jekyll converter plugin rendering `.crv`/`.carve` pages via the carve Ruby gem.

## Syntax Highlighting

Grammars and themes for displaying Carve with syntax colors.

- [tree-sitter-carve](https://github.com/markup-carve/tree-sitter-carve) - Tree-sitter grammar with queries for highlighting, injections, folds, indents, locals, and text objects.
- [carve-grammars `prism/carve.js`](https://github.com/markup-carve/carve-grammars/blob/main/prism/carve.js) - Prism grammar for highlighting Carve source on the web (`Prism.languages.carve`).
- [carve-grammars `highlightjs/carve.js`](https://github.com/markup-carve/carve-grammars/blob/main/highlightjs/carve.js) - highlight.js grammar for highlighting Carve source on the web (ESM, CommonJS, or classic `<script>`).
- [vscode-carve `carve.tmLanguage.json`](https://github.com/markup-carve/vscode-carve/blob/main/syntaxes/carve.tmLanguage.json) - TextMate grammar (also bundled by intellij-carve).

## Sandboxes

Interactive playgrounds for experimenting with Carve.

- [Carve Playground](https://markup-carve.github.io/carve/playground) - Type Carve and see the rendered HTML live in the browser.
- [carve-wysiwyg](https://github.com/markup-carve/carve-wysiwyg) - WYSIWYG editor for Carve built on the carve-grammars Tiptap kit: visual editing, a live Carve source pane, and an HTML preview, with round-trip import via carve-js.

## Example Sites

Websites and blogs built with Carve.

- [Carve documentation site](https://markup-carve.github.io/carve/) - The official docs, built from Carve sources via vite-plugin-carve.

## Learning Resources

Articles and tutorials for learning Carve.

### Articles

<!-- Add entries here -->

### Tutorials

<!-- Add entries here -->

## Community

Places to discuss Carve and get help.

- [GitHub Discussions](https://github.com/markup-carve/carve/discussions) - Discussion forum for Carve.
- [GitHub Issues](https://github.com/markup-carve/carve/issues) - Report bugs and request features.
