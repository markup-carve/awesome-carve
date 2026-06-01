# Awesome Carve [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of Carve resources, tools, editors, and libraries.

[Carve](https://github.com/markup-carve/carve) is a post-Djot lightweight markup language with visual mnemonics and human-centered design. It builds on [Djot](https://djot.net/)'s technical rigor — linear parsing, no expressive blind spots, arbitrary attributes — while adding visual mnemonics (`/italic/`, `*bold*`, `_underline_`, `~strike~`) and conventions that match how non-technical users naturally mark up text.

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

<!-- Add entries here -->

## Parsers & Libraries

Language-specific implementations for parsing and rendering Carve.

### JavaScript / TypeScript

- [markup-carve/carve-js](https://github.com/markup-carve/carve-js) - Reference TypeScript implementation of the Carve markup language.

### PHP

- [markup-carve/carve-php](https://github.com/markup-carve/carve-php) - PHP parser and renderer with a `carve` CLI binary; forked from djot-php, syntax migration in progress.

### Rust

- [markup-carve/carve-rs](https://github.com/markup-carve/carve-rs) - Rust parser and HTML renderer with a `carve` CLI binary; passes the upstream spec corpus.
- [markup-carve/carve-wasm](https://github.com/markup-carve/carve-wasm) - WebAssembly bindings for the Rust implementation.

<!-- Add additional language sections (Go, Python, Ruby, …) as implementations land -->

## Editors & IDE Support

Syntax highlighting and editing support for popular editors.

- [markup-carve/vscode-carve](https://github.com/markup-carve/vscode-carve) - VS Code extension for `.crv` and `.carve` files, with syntax highlighting and `carve-lsp` integration.
- [markup-carve/zed-carve](https://github.com/markup-carve/zed-carve) - Zed editor extension for `.crv` and `.carve` files, backed by the native Tree-sitter grammar.

## Tools

Command-line utilities for working with Carve documents.

- [markup-carve/carve-lsp](https://github.com/markup-carve/carve-lsp) - Language server for editor integrations and tooling that speaks LSP.

## Converters

Tools for converting Carve to other formats (HTML, PDF, plaintext, …).

<!-- Add entries here -->

## Migration

Tools for migrating from other markup formats to Carve.

<!-- Add entries here -->

## Roundtrip Conversion

Tools supporting lossless bidirectional conversion for content editing workflows. Essential for WYSIWYG integration where content is stored as Carve but edited as HTML — changes made in the visual editor convert back to Carve without losing syntax choices or formatting details.

<!-- Add entries here -->

## Framework Integration

Carve support for web frameworks.

- [markup-carve/vite-plugin-carve](https://github.com/markup-carve/vite-plugin-carve) - Vite plugin for importing `.crv` and `.carve` files as rendered HTML modules.

## CMS Integration

Carve plugins for content management systems.

<!-- Add entries here -->

## Documentation Tools

Generate documentation from Carve source files.

<!-- Add entries here -->

## Static Site Generators

Build static websites with Carve content.

<!-- Add entries here -->

## Syntax Highlighting

Grammars and themes for displaying Carve with syntax colors.

- [markup-carve/tree-sitter-carve](https://github.com/markup-carve/tree-sitter-carve) - Tree-sitter grammar with queries for highlighting, injections, folds, indents, locals, and text objects.

## Sandboxes

Interactive playgrounds for experimenting with Carve.

<!-- Add entries here -->

## Example Sites

Websites and blogs built with Carve.

<!-- Add entries here -->

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
