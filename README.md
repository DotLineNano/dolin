# Dolin

Dolin is a compact flow-line scripting language for checking, matching, and simple validation.

It is designed around a readable execution path called a `line`, where small actions and output points form a simple rule flow.

## Design idea

Dolin is built around the idea of a visible flow line.

- `line` defines the main path
- actions inside it are small steps on that path
- `scan` checks a condition on the path
- `good` and `lost` split the path into result directions
- `prt` and `pnr` act as output points
- `seal` closes the path

This gives Dolin a compact structure that is easy to read and easy to follow.

## Example

```don
line email_check
pick email

scan email has "@"
    good prt "valid"
    lost prt "invalid"
seal
```

## Core keywords

- `line` - starts a flow path
- `pick` - declares input
- `hold` - stores a value
- `scan` - checks a condition
- `good` - success branch
- `lost` - failure branch
- `prt` - universal output point
- `pnr` - number-only output point
- `open` - accepted result
- `lock` - rejected result
- `seal` - ends a flow path

## Example files

The `examples/` directory includes:

- `hello.don`
- `email_check.don`
- `apk_check.don`
- `score.don`
- `main.don`

## File extension

Recommended file extension:

- `.don`

## Project status

Dolin is currently in an early design stage.

The syntax, tokens, and AST structure are being shaped step by step to keep the language compact, readable, and distinctive.

## Goals

- keep syntax compact
- keep flow readable
- make rule checks easy to express
- build a small language with a clear identity

## Documentation

See the `docs/` directory:

- `docs/syntax.md`
- `docs/token.md`
- `docs/ast.md`

## License

See `LICENSE`.
