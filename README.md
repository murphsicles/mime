# MIME — Media Type Parsing for Zeta

A Zeta port of the Rust `mime` crate. Provides types for parsing and working with MIME media types (formerly known as MIME types).

## Features

- `Mime` type with `top_level()`, `sub_level()`, `get_param()` accessors
- `MediaRange` for Accept header matching
- `FromStr` parser from `"text/plain"`, `"application/json; charset=utf-8"`, etc.
- Well-known MIME type constants: `TEXT_PLAIN`, `APPLICATION_JSON`, `IMAGE_SVG`, etc.
- `Attr` and `Value` types for parameters

## Usage

```zeta
// Parse a MIME type
var mime = try Mime.from_str("text/plain; charset=utf-8");

// Inspect parts
assert_eq(mime.top_level(), TopLevel.text);
assert_eq(mime.sub_level(), SubLevel.plain);
assert_eq(mime.get_param(Attr.charset), Value.utf_8);

// Use constants
assert_eq(Mime.TEXT_PLAIN_UTF_8, mime);
```

## Constants

```zeta
pub const TEXT_PLAIN: Mime = Mime.new(TopLevel.text, SubLevel.plain);
pub const APPLICATION_JSON: Mime = Mime.new(TopLevel.application, SubLevel.json);
pub const IMAGE_SVG: Mime = Mime.new(TopLevel.image, SubLevel.svg);
// ... and many more
```

## Release Notes

### v0.4.1 — MIME Type Parsing for Zeta

- Initial Zeta port of `mime` v0.3.6 from crates.io
- Full `Mime` type with parsing, comparison, and constants
- `MediaRange` for matching Accept headers
- `Attr`/`Value` parameter support
- 100+ well-known MIME type constants
- MIT License
