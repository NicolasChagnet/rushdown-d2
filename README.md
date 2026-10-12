# rushdown-d2

This is an extension for the [rushdown](https://crates.io/crates/rushdown) crate.

Draw the `d2` code blocks of a markdown document as inline SVG. [D2](https://d2lang.com) draws a diagram from a small language of its own: the `d2` command-line tool, which must be installed, does the drawing while the document is rendered. The diagram lands in the page as `<figure class="d2">…</figure>`, which needs no script and no stylesheet.

## Usage

Add the crate via `cargo add rushdown-d2` and include it within your rushdown parser

```rust
use rushdown::new_markdown_to_html;
let parser = new_markdown_to_html(
    Default::default(),
    Default::default(),
    rushdown_d2::d2_parser_extension(),
    rushdown_d2::d2_html_renderer_extension(rushdown_d2::Options::default()),
);
let mut html = String::new();
parser(&mut html, "```d2\na -> b\n```").unwrap();
assert!(html.contains("<svg"));
```
