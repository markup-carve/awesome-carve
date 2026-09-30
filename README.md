# Awesome Carve [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of Carve resources, tools, editors, and libraries.

[Carve](https://github.com/markup-carve/carve) is a lightweight markup language for documents and the web. It keeps Markdown's familiarity and [Djot](https://djot.net/)'s technical rigor - linear parsing, no expressive blind spots, arbitrary attributes - and adds inline delimiters that look like their output (`/italic/`, `*bold*`, `_underline_`, `~strike~`) plus first-class figures, footnotes, cross-references, citations, admonitions and math.

## Contents

- [Official Resources](#official-resources)
- [Specification](#specification)
- [Parsers & Libraries](#parsers--libraries)
- [Editors & IDE Support](#editors--ide-support)
- [Tools](#tools)
- [AI & Agent Tooling](#ai--agent-tooling)
- [Converters](#converters)
- [Migration](#migration)
- [Roundtrip Conversion](#roundtrip-conversion)
- [Framework Integration](#framework-integration)
- [CMS Integration](#cms-integration)
- [Documentation Tools](#documentation-tools)
- [Static Site Generators](#static-site-generators)
- [Presentations](#presentations)
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
- [Conformance test suite](https://github.com/markup-carve/carve/tree/main/tests/corpus) - Shared spec corpus: `.crv` input paired with expected `.html`, used by every implementation as a git submodule. Also in djot.js format at [`tests/spec`](https://github.com/markup-carve/carve/tree/main/tests/spec).
- [carve-proofs](https://github.com/markup-carve/carve-proofs) - Machine-checked Rocq models of Carve parsing rules.

## Parsers & Libraries

Language-specific implementations for parsing and rendering Carve.

### JavaScript / TypeScript

- [carve-js](https://github.com/markup-carve/carve-js) - Reference TypeScript implementation of the Carve markup language.

### PHP

- [carve-php](https://github.com/markup-carve/carve-php) - PHP parser and renderer with a `carve` CLI binary; implements the full Carve syntax and passes the spec corpus (forked from djot-php).
- [carve-php-media-embed](https://github.com/markup-carve/carve-php-media-embed) - Opt-in carve-php extension that embeds audio/video from 30+ providers via media-embed.

### Rust

- [carve-rs](https://github.com/markup-carve/carve-rs) - Rust parser and HTML renderer with a `carve` CLI binary; passes the upstream spec corpus.
- [carve-wasm](https://github.com/markup-carve/carve-wasm) - WebAssembly bindings for the Rust implementation.

### Python

- [carve-py](https://github.com/markup-carve/carve-py) - Python bindings (PyO3) over carve-rs, with HTML, Markdown, plain-text and ANSI renderers. Output byte-identical to the carve-rs CLI.

### Go

- [carve-go](https://github.com/markup-carve/carve-go) - Pure-Go module (no cgo): embeds a WASI build of carve-rs and runs it via wazero. `ToHTML` output byte-identical to the carve-rs CLI.

### Ruby

- [carve-rb](https://github.com/markup-carve/carve-rb) - Native Ruby gem (magnus over carve-rs); `Carve.to_html(source, extensions:)`, output byte-identical to the carve-rs CLI.

### Echo

- [echo-carve](https://github.com/markup-carve/echo-carve) - Bindings for the Echo programming language over the carve-rs engine through a small C ABI; `carve::to_html` renders Carve to HTML.

## Editors & IDE Support

Standalone editors and editing support for popular editors and IDEs.

- [Carver](https://github.com/josbeir/carver) - Native GNOME note-taking app with rich-text editing, synchronized Carve source and preview, and full-text search.
- [emacs-carve](https://github.com/markup-carve/emacs-carve) - Emacs major mode for `.crv` files, with highlighting, an imenu heading index and outline support.
- [helix-carve](https://github.com/markup-carve/helix-carve) - Helix editor support: `languages.toml` entry and runtime queries backed by the tree-sitter-carve grammar.
- [intellij-carve](https://github.com/markup-carve/intellij-carve) - JetBrains IDE plugin for `.crv` files, with highlighting, a live split preview and HTML export.
- [obsidian-carve](https://github.com/markup-carve/obsidian-carve) - Obsidian community plugin registering `.crv` notes with safe reading and editable source views; raw HTML is disabled by default.
- [sublime-carve](https://github.com/markup-carve/sublime-carve) - Sublime Text package for `.crv` files: highlighting with embedded languages in fences, a heading outline, and `carve fmt` and `carve lint` integration.
- [vim-carve](https://github.com/markup-carve/vim-carve) - Vim and Neovim support: regex highlighting for any colorscheme, plus Neovim Tree-sitter integration.
- [vscode-carve](https://github.com/markup-carve/vscode-carve) - VS Code extension for `.crv` files, with syntax highlighting, semantic tokens, diagnostics, and document symbols.
- [zed-carve](https://github.com/markup-carve/zed-carve) - Zed editor extension for `.crv` files, backed by the native Tree-sitter grammar.

## Tools

Command-line utilities for working with Carve documents.

- [carve-lsp](https://github.com/markup-carve/carve-lsp) - Language server for editor integrations and tooling that speaks LSP.
- [`carve` CLI (carve-php)](https://github.com/markup-carve/carve-php) - Convert `.crv` files to HTML (and import Markdown/HTML/BBCode/Djot) from the command line.
- [`carve` CLI (carve-rs)](https://github.com/markup-carve/carve-rs) - Fast native `.crv` to HTML converter binary.
- [homebrew-carve](https://github.com/markup-carve/homebrew-carve) - Homebrew tap for the `carve` CLI.

### Validators & Linters

- [`carve lint`](https://github.com/markup-carve/carve-js#cli) - Validator in the carve-js CLI for problems that parse but render wrong, such as broken cross-references and duplicate heading ids. Works as a CI gate and in editors via carve-lsp.

### Formatters

- [`carve fmt`](https://github.com/markup-carve/carve-js#cli) - Canonical formatter in the `carve` CLI of all three engines, with byte-identical output. Leaves the rendered HTML unchanged; `--check` works as a CI gate.

### Styling

- [carve-css](https://github.com/markup-carve/carve-css) - Stylesheet for Carve's rendered HTML, from admonitions and tab sets to footnotes and the glossary. Scoped under `.carve`, themed through custom properties.

### Benchmarks

- [carve-bench](https://github.com/markup-carve/carve-bench) - Render speed benchmarks across carve-js, carve-php and carve-rs over a fixed document set, written out as a results table.
- [pandoc-format-fidelity](https://github.com/markup-carve/pandoc-format-fidelity) - How much of a document survives conversion, across every format pandoc ships, with Carve scored on the same probes via pandoc-carve.

## AI & Agent Tooling

Skills and servers for AI coding tools and LLM agents writing Carve.

- [carve-mcp](https://github.com/markup-carve/carve-mcp) - Local MCP server backed by carve-js, with tools for linting, formatting, rendering and import. Needs no filesystem or network access; not yet published.
- [carve-skill](https://github.com/markup-carve/carve-skill) - Agent skill (`carve-authoring`) that teaches AI tools to write valid `.crv`, focusing on where Carve differs from Markdown. Sourced from the spec docs.

## Converters

Render Carve to other output formats. All three engines (carve-js, carve-php, carve-rs) and their language bindings ship the same renderer set, selectable by CLI flag or API.

- **Carve to HTML** - the default output of every engine: [carve-js](https://github.com/markup-carve/carve-js) `renderHtml`, [carve-rs](https://github.com/markup-carve/carve-rs) `carve --html`, [carve-php](https://github.com/markup-carve/carve-php/blob/main/src/Renderer/HtmlRenderer.php) `HtmlRenderer`, [carve-py](https://github.com/markup-carve/carve-py) `carve.to_html`.
- **Carve to Markdown** - [carve-js](https://github.com/markup-carve/carve-js) `renderMarkdown`, [carve-rs](https://github.com/markup-carve/carve-rs) `carve --markdown`, [carve-php](https://github.com/markup-carve/carve-php/blob/main/src/Renderer/MarkdownRenderer.php) `MarkdownRenderer`, [carve-py](https://github.com/markup-carve/carve-py) `carve.to_markdown`.
- **Carve to plain text** - [carve-js](https://github.com/markup-carve/carve-js) `renderPlain`, [carve-rs](https://github.com/markup-carve/carve-rs) `carve --plain`, [carve-php](https://github.com/markup-carve/carve-php/blob/main/src/Renderer/PlainTextRenderer.php) `PlainTextRenderer`, [carve-py](https://github.com/markup-carve/carve-py) `carve.to_plain_text`.
- **Carve to ANSI (terminal)** - [carve-js](https://github.com/markup-carve/carve-js) `renderAnsi`, [carve-rs](https://github.com/markup-carve/carve-rs) `carve --ansi`, [carve-php](https://github.com/markup-carve/carve-php/blob/main/src/Renderer/AnsiRenderer.php) `AnsiRenderer`, [carve-py](https://github.com/markup-carve/carve-py) `carve.to_ansi`.
- **Carve to PDF** - four routes:
  - [carve-pdf](https://github.com/markup-carve/carve-pdf) - the `crv2pdf` CLI renders via headless Chrome (CDP) with a pluggable PHP or JS Carve backend; also emits standalone HTML, Markdown, and text, with batch and watch modes.
  - [carve-hexapdf](https://github.com/markup-carve/carve-hexapdf) - native PDF via the pure-Ruby HexaPDF engine (no browser).
  - [carve-sile](https://github.com/markup-carve/carve-sile) - typeset PDF through SILE and its Resilient classes, mapping the Carve AST onto real typesetting commands rather than rendering to HTML first; composite figures come out as one numbered unit.
  - [carve-latex](https://github.com/markup-carve/carve-latex) - publication-grade editable LaTeX and reproducible LuaLaTeX PDF for papers, books, theses, and publisher workflows, with bibliographies, indexes, glossaries, diagrams, accessibility options, and versioned fidelity reports.
- **Carve to Typst, DOCX, and every Pandoc writer** - [pandoc-carve](https://github.com/markup-carve/pandoc-carve) - converts the Carve AST to Pandoc's JSON AST, so one Carve document reaches any Pandoc output format; also makes `{=latex}`-style raw spans fire for their target writer.
- **Carve to and from Open Knowledge Format (OKF)** - [carve-okf](https://github.com/markup-carve/carve-okf) - exports Carve document trees as portable Markdown concept bundles with YAML metadata, an index, git-derived history, copied assets, rewritten links, and engine-backed portability diagnostics; validates and imports bundles back to Carve.
- **Carve to chat-platform markup** - [carve-php-chat](https://github.com/markup-carve/carve-php-chat) - renders a Carve document to WhatsApp, Slack, Telegram or Discord markup, and reports what could not survive the trip. Each platform accepts a different, mutually incompatible subset - different link syntax, escaping rules and length caps - and each is a JSON flavor definition rather than a class, so adding one needs no PHP.

## Migration

Tools for migrating from other markup formats to Carve.

- [carve-js `markdownToCarve`](https://github.com/markup-carve/carve-js) - Source-to-source Markdown → Carve converter that handles the syntax where Carve differs from Markdown.
- [carve-php converters](https://github.com/markup-carve/carve-php/tree/main/src/Converter) - Markdown, HTML, BBCode and Djot → Carve converters, with a `carve` CLI for converting files.
- [pandoc-carve import](https://github.com/markup-carve/pandoc-carve) - Anything pandoc reads (DOCX, LaTeX, RST, Org, ...) → Carve, via the Pandoc AST and the `carve fmt` serializer.
- [pdf-to-carve](https://github.com/markup-carve/pdf-to-carve) - PDFs and document images → Carve. Born-digital PDFs convert without AI; scans can use an optional OpenAI-compatible vision path.

## Roundtrip Conversion

Tools supporting lossless bidirectional conversion for content editing workflows. Essential for WYSIWYG integration where content is stored as Carve but edited as HTML — changes made in the visual editor convert back to Carve without losing syntax choices or formatting details.

- [carve-php](https://github.com/markup-carve/carve-php) - Round-trip mode (data attributes for Carve to HTML to Carve) plus an `HtmlToCarve` converter for WYSIWYG editing workflows.

## Framework Integration

Carve support for web frameworks.

- [cakephp-markup](https://github.com/dereuromark/cakephp-markup) - CakePHP plugin rendering Carve to HTML via carve-php: a `CarveHelper` for templates and a `CarveView` for `.crv` template files.
- [laravel-carve](https://github.com/markup-carve/laravel-carve) - Laravel package rendering Carve to HTML via carve-php, with Blade directives, a facade, a validation rule and render caching.
- [symfony-carve](https://github.com/markup-carve/symfony-carve) - Symfony bundle rendering Carve to HTML via carve-php: a Twig filter and function, a renderer service, and safe-mode sanitization.
- [tempest-carve](https://github.com/markup-carve/tempest-carve) - Tempest package rendering Carve to safe HTML via carve-php: an `x-carve` view component and an injectable `CarveRenderer` service.
- [vite-plugin-carve](https://github.com/markup-carve/vite-plugin-carve) - Vite plugin for importing `.crv` files as rendered HTML modules.
- [webpack-loader-carve](https://github.com/markup-carve/webpack-loader-carve) - Webpack 5 loader for importing `.crv` files as build-time-rendered HTML modules, with a verified Next.js webpack build.
- [carve-grammars](https://github.com/markup-carve/carve-grammars) - Tiptap editor kit and Carve serializer for WYSIWYG editors that read and write Carve. Also ships Prism and highlight.js grammars.
- [carve-components](https://github.com/markup-carve/carve-components) - React and Vue 3 `<Carve>` components that render Carve to HTML via carve-js, with SSR support and safe-by-default raw-HTML escaping.

## CMS Integration

Carve plugins for content management systems.

- [shopware-carve](https://github.com/markup-carve/shopware-carve) - Shopware 6 plugin (carve-php engine) with Twig filters, a CMS element, admin live preview and mail rendering.
- [wp-carve](https://github.com/markup-carve/wp-carve) - WordPress plugin (carve-php engine) with live in-browser preview, multi-format paste, frontmatter-to-meta, render caching, and a REST API.

## Documentation Tools

Generate documentation from Carve source files.

- [mkdocs-carve](https://github.com/markup-carve/mkdocs-carve) - MkDocs plugin that renders `.crv` pages via carve-py, with per-extension config and full nav/path support.
- [docusaurus-carve](https://github.com/markup-carve/docusaurus-carve) - Docusaurus 3 docs plugin for `.crv` pages, delegating routes, sidebars and theming to the official docs plugin.
- [zensical-carve](https://github.com/markup-carve/zensical-carve) - Zensical support (the MkDocs successor): a `carve` fence inside Markdown pages, plus a preprocessor that renders whole `.crv` pages.

## Static Site Generators

Build static websites with Carve content.

- [astro-carve](https://github.com/markup-carve/astro-carve) - Astro integration: import `.crv` files into Astro pages and components as rendered HTML with frontmatter.
- [carve-press](https://github.com/markup-carve/carve-press) - First-party static site generator for `.crv` pages: carve-js with Shiki highlighting, link checks at build time, and a dev server.
- [eleventy-carve](https://github.com/markup-carve/eleventy-carve) - Eleventy (11ty) plugin adding `.crv` as a template format, with Carve frontmatter flowing into the data cascade.
- [hugo-carve](https://github.com/markup-carve/hugo-carve) - Hugo preprocessor (via carve-go) that converts `.crv` content to HTML pages before the build, keeping front matter.
- [jekyll-carve](https://github.com/markup-carve/jekyll-carve) - Jekyll converter plugin rendering `.crv` pages via the carve-lang Ruby gem.

## Presentations

Slide decks written in Carve.

- [reveal-carve](https://github.com/markup-carve/reveal-carve) - reveal.js integration: a runtime plugin plus a build step and CLI, with slide directives, deck linting and PDF printing. [Demo deck](https://markup-carve.github.io/reveal-carve/).

## Syntax Highlighting

Grammars and themes for displaying Carve with syntax colors.

- [tree-sitter-carve](https://github.com/markup-carve/tree-sitter-carve) - Tree-sitter grammar with queries for highlighting, injections, folds, indents, locals, and text objects.
- [carve-grammars `prism/carve.js`](https://github.com/markup-carve/carve-grammars/blob/main/prism/carve.js) - Prism grammar for highlighting Carve source on the web (`Prism.languages.carve`).
- [highlightjs-carve](https://github.com/markup-carve/highlightjs-carve) - highlight.js language definition as a standalone npm package. UMD and dependency-free, so a plain `<script>` works as well as a bundler.
- [pygments-carve](https://github.com/markup-carve/pygments-carve) - Pygments lexer; installing it is the whole integration, so `carve` fences highlight in MkDocs, Sphinx, Zensical and `pygmentize`.
- [rouge-carve](https://github.com/markup-carve/rouge-carve) - Rouge lexer, coloring Carve source wherever Rouge is the highlighter, such as a fenced `carve` block in a Jekyll post.
- [carve-grammars `highlightjs/carve.js`](https://github.com/markup-carve/carve-grammars/blob/main/highlightjs/carve.js) - The same grammar as a file inside carve-grammars, for consumers already using that package.
- [vscode-carve `carve.tmLanguage.json`](https://github.com/markup-carve/vscode-carve/blob/main/syntaxes/carve.tmLanguage.json) - TextMate grammar (also bundled by intellij-carve).

## Sandboxes

Interactive playgrounds for experimenting with Carve.

- [Carve Playground](https://markup-carve.github.io/carve/playground) - Type Carve and see the rendered HTML live in the browser.
- [carve-php sandbox](https://sandbox.dereuromark.de/sandbox/carve) - carve-php playground with converters, an AST inspector and extension demos.
- [carve-wysiwyg](https://github.com/markup-carve/carve-wysiwyg) - WYSIWYG editor for Carve on the carve-grammars Tiptap kit, with a live source pane and an HTML preview.

## Example Sites

Websites, blogs, and runnable apps built with Carve.

- [Carve documentation site](https://markup-carve.github.io/carve/) - The official docs, built from Carve sources via vite-plugin-carve.
- [Zensical Carve demo](https://github.com/markup-carve/zensical-carve-demo) - A Zensical site written in Carve with every extension enabled, including CSS for constructs Material does not style.
- [CarvePress documentation site](https://markup-carve.github.io/carve-press/) - The carve-press docs, written in Carve and built by carve-press itself, with blog pages, search and live playground blocks.
- [laravel-carve-demo](https://github.com/markup-carve/laravel-carve-demo) - Runnable Laravel app demonstrating every feature of laravel-carve, including a safe-mode comparison and the static mode side by side.
- [symfony-carve-demo](https://github.com/markup-carve/symfony-carve-demo) - Runnable Symfony app demonstrating every feature of symfony-carve, including a live editor and a safe-mode comparison.
- [tempest-carve-demo](https://github.com/markup-carve/tempest-carve-demo) - Runnable Tempest app demonstrating every feature of tempest-carve.

## Learning Resources

Articles and tutorials for learning Carve.

### Articles

- 2026-07: [Twenty years of Markdown hindsight, in one markup language](https://www.dereuromark.de/2026/07/13/twenty-years-of-markdown-hindsight-in-one-markup-language-carve/) - What Carve keeps from Markdown, and what it fixes.
- 2026-07: [Why Carve markup changes how you author rich text in Shopware 6](https://www.dereuromark.de/2026/07/17/why-carve-markup-changes-how-you-author-rich-text-in-shopware-6/) - Authoring rich text in Shopware 6 without pasting raw HTML.
- 2026-08: [Pandoc: What survives a conversion?](https://www.dereuromark.de/2026/08/19/pandoc-what-survives-a-conversion/) - Measures round-trip fidelity across the formats Pandoc writes, Carve among them.
- 2026-09: [From Markdown to Carve](https://www.dereuromark.de/2026/09/24/from-markdown-to-carve/) - Convert a Markdown file, review syntax changes, and lint the Carve output.

### Tutorials

<!-- Add entries here -->

## Community

Places to discuss Carve and get help.

- [GitHub Discussions](https://github.com/markup-carve/carve/discussions) - Discussion forum for Carve.
- [GitHub Issues](https://github.com/markup-carve/carve/issues) - Report bugs and request features.
- [r/markup_carve](https://www.reddit.com/r/markup_carve) - Subreddit for Carve news, questions, and showing what you built.
