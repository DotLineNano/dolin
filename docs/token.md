# Dolin Tokens

Dolin defines a small set of simple token categories.

## Token categories

- keyword
- identifier
- string
- number
- operator

## Keywords

Reserved keywords:

- `line`
- `seal`
- `pick`
- `hold`
- `scan`
- `good`
- `lost`
- `prt`
- `pnr`
- `open`
- `lock`

These keywords should not be used as identifiers.

## Identifiers

Identifiers are user-defined names.

Examples:

- `email`
- `file_name`
- `score`
- `apk_v2`

Rules:

- use lowercase letters
- may contain numbers
- may contain underscore
- must not begin with a number

Valid:

- `user`
- `user1`
- `file_name`

Invalid:

- `1user`
- `user-name`
- `file.name`
- `User`

## Strings

Strings use double quotes.

Examples:

- `"hello"`
- `"valid email"`
- `".apk"`

## Numbers

Numbers are written without quotes.

Examples:

- `10`
- `99`
- `404`
- `0`

## Operators

Supported operators:

- `is`
- `isnot`
- `has`
- `begins`
- `ends`

Meanings:

- `is` - exact match
- `isnot` - not equal
- `has` - contains text
- `begins` - starts with
- `ends` - ends with

Examples:

- `scan name is "root"`
- `scan role isnot "guest"`
- `scan email has "@"`
- `scan file begins "PK"`
- `scan path ends ".apk"`

## Example token breakdown

Source:

- `scan email has "@"`

Breakdown:

- `scan` -> keyword
- `email` -> identifier
- `has` -> operator
- `"@"` -> string

## File extension

Recommended source file extension:

- `.don`
