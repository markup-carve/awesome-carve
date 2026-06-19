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

- [markup-carve/carve](https://github.com/markup-carve/carve) - Language definition, philosophy, and quick reference.
- [markup-carve/carve-js](https://github.com/markup-carve/carve-js) - Reference TypeScript implementation.
- [markup-carve/tree-sitter-carve](https://github.com/markup-carve/tree-sitter-carve) - Native Tree-sitter grammar for Carve.
- [markup-carve/carve-lsp](https://github.com/markup-carve/carve-lsp) - Language server for diagnostics and document symbols.

## Specification

Formal syntax specification and grammar definitions.

- [markup-carve/carve `grammar.ebnf`](https://github.com/markup-carve/carve/blob/main/resources/grammar.ebnf) - Normative EBNF grammar plus the PART 9 semantic constraints (the conformance authority).
- [Carve docs](https://markup-carve.github.io/carve/) - Rendered spec, examples, and edge-case reference.

## Parsers & Libraries

Language-specific implementations for parsing and rendering Carve.

### JavaScript / TypeScript

- [markup-carve/carve-js](https://github.com/markup-carve/carve-js) - Reference TypeScript implementation of the Carve markup language.

### PHP

- [markup-carve/carve-php](https://github.com/markup-carve/carve-php) - PHP parser and renderer with a `carve` CLI binary; implements the full Carve syntax and passes the spec corpus (forked from djot-php).

### Rust

- [markup-carve/carve-rs](https://github.com/markup-carve/carve-rs) - Rust parser and HTML renderer with a `carve` CLI binary; passes the upstream spec corpus.
- [markup-carve/carve-wasm](https://github.com/markup-carve/carve-wasm) - WebAssembly bindings for the Rust implementation.

<!-- Add additional language sections (Go, Python, Ruby, …) as implementations land -->

## Editors & IDE Support

Syntax highlighting and editing support for popular editors.

- [markup-carve/intellij-carve](https://github.com/markup-carve/intellij-carve) - JetBrains IDE plugin (IntelliJ IDEA, PhpStorm, WebStorm, ...) for `.crv` and `.carve` files: TextMate-based highlighting, live split preview (carve-js or carve-php), HTML export, live templates, and custom preview CSS.
- [markup-carve/vscode-carve](https://github.com/markup-carve/vscode-carve) - VS Code extension for `.crv` and `.carve` files, with syntax highlighting, semantic tokens, diagnostics, and document symbols.
- [markup-carve/zed-carve](https://github.com/markup-carve/zed-carve) - Zed editor extension for `.crv` and `.carve` files, backed by the native Tree-sitter grammar.

## Tools

Command-line utilities for working with Carve documents.

- [markup-carve/carve-lsp](https://github.com/markup-carve/carve-lsp) - Language server for editor integrations and tooling that speaks LSP.
- [`carve` CLI (carve-php)](https://github.com/markup-carve/carve-php) - Convert `.crv` files to HTML (and import Markdown/HTML/BBCode/Djot) from the command line.
- [`carve` CLI (carve-rs)](https://github.com/markup-carve/carve-rs) - Fast native `.crv` to HTML converter binary.

### Validators & Linters

- [`carve lint`](https://github.com/markup-carve/carve-js#cli) - Validator in the carve-js CLI. Flags problems that parse but render wrong: broken `</#id>` cross-references, duplicate heading ids, trailing `{…}` heading attributes, legacy `raw FORMAT` fences, and block markers that leaked as plain text. Exits non-zero, so it works as a CI gate; the same checks surface live in editors via [carve-lsp](https://github.com/markup-carve/carve-lsp).

## Converters

Tools for converting Carve to other formats (HTML, PDF, plaintext, …).

<!-- Add entries here -->

## Migration

Tools for migrating from other markup formats to Carve.

- [markup-carve/carve-js `markdownToCarve`](https://github.com/markup-carve/carve-js) - Source-to-source Markdown → Carve converter (handles the inline syntax that differs from Markdown, blank-line block spacing, setext headings, and more).
- [markup-carve/carve-php converters](https://github.com/markup-carve/carve-php/tree/main/src/Converter) - Markdown, HTML, BBCode and Djot → Carve converters, with a `carve` CLI for converting files.

## Roundtrip Conversion

Tools supporting lossless bidirectional conversion for content editing workflows. Essential for WYSIWYG integration where content is stored as Carve but edited as HTML — changes made in the visual editor convert back to Carve without losing syntax choices or formatting details.

- [markup-carve/carve-php](https://github.com/markup-carve/carve-php) - Round-trip mode (data attributes for Carve to HTML to Carve) plus an `HtmlToCarve` converter for WYSIWYG editing workflows.

## Framework Integration

Carve support for web frameworks.

- [markup-carve/symfony-carve](https://github.com/markup-carve/symfony-carve) - Symfony bundle that renders Carve to HTML via carve-php: a `{{ value|carve }}` Twig filter, a `carve()` function, a `CarveRenderer` service, and configurable safe-mode sanitization.
- [markup-carve/symfony-carve-demo](https://github.com/markup-carve/symfony-carve-demo) - Runnable Symfony app demonstrating every feature of the symfony-carve bundle: Twig filter and function, the service, a live editor, a safe-mode comparison, and a syntax gallery.
- [markup-carve/vite-plugin-carve](https://github.com/markup-carve/vite-plugin-carve) - Vite plugin for importing `.crv` and `.carve` files as rendered HTML modules.
- [markup-carve/carve-grammars](https://github.com/markup-carve/carve-grammars) - Tiptap editor kit and Carve serializer for building WYSIWYG editors that read and write Carve (also ships Prism and highlight.js grammars; see Syntax Highlighting).

## CMS Integration

Carve plugins for content management systems.

- [markup-carve/wp-carve](https://github.com/markup-carve/wp-carve) - WordPress plugin (carve-php engine) with live in-browser preview, multi-format paste, frontmatter-to-meta, render caching, and a REST API.

## Documentation Tools

Generate documentation from Carve source files.

<!-- Add entries here -->

## Static Site Generators

Build static websites with Carve content.

<!-- Add entries here -->

## Syntax Highlighting

Grammars and themes for displaying Carve with syntax colors.

- [markup-carve/tree-sitter-carve](https://github.com/markup-carve/tree-sitter-carve) - Tree-sitter grammar with queries for highlighting, injections, folds, indents, locals, and text objects.
- [markup-carve/carve-grammars `prism/carve.js`](https://github.com/markup-carve/carve-grammars/blob/main/prism/carve.js) - Prism grammar for highlighting Carve source on the web (`Prism.languages.carve`).
- [markup-carve/carve-grammars `highlightjs/carve.js`](https://github.com/markup-carve/carve-grammars/blob/main/highlightjs/carve.js) - highlight.js grammar for highlighting Carve source on the web (ESM, CommonJS, or classic `<script>`).
- [markup-carve/vscode-carve `carve.tmLanguage.json`](https://github.com/markup-carve/vscode-carve/blob/main/syntaxes/carve.tmLanguage.json) - TextMate grammar (also bundled by intellij-carve).

## Sandboxes

Interactive playgrounds for experimenting with Carve.

- [Carve Playground](https://markup-carve.github.io/carve/playground) - Type Carve and see the rendered HTML live in the browser.

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
