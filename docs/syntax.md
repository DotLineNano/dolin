# Dolin Syntax

Dolin is a compact flow-line scripting language for checking, matching, and simple validation.

Its design is built around a single readable path called a `line`.
Each line contains small actions and result points, making the script feel like a guided flow instead of a general-purpose programming language.

## Design idea

Dolin is based on the idea of a visible flow line.

- `line` defines the main path
- actions inside it are small steps on that path
- `scan` checks a condition on the path
- `good` and `lost` split the path into result directions
- `prt` and `pnr` act as output points
- `seal` closes the path

This gives Dolin a compact structure that is easy to read and easy to follow.

## Block structure

A flow starts with `line` and ends with `seal`.

Example:

line email_check
pick email

scan email has "@"
    good prt "valid"
    lost prt "invalid"
seal

## Core keywords

### line

Starts a new Dolin flow path.

Example:

line email_check

### seal

Ends the current flow path.

Example:

seal

### pick

Declares an input value.

Example:

pick username
pick email

### hold

Stores or updates a value.

Example:

hold role "guest"
hold limit 10

### scan

Starts a condition check on the current line.

Example:

scan username is "root"
scan email has "@"

### good

Defines the success branch of a scan.

Example:

good prt "accepted"
good open

### lost

Defines the failure branch of a scan.

Example:

lost prt "rejected"
lost lock

### prt

Universal output point.
Can print text, number, bool, or a stored value.

Example:

prt "hello"
prt total
prt 404

### pnr

Number-only output point.
Should only be used with numeric values.

Example:

pnr 10
pnr total

### open

Marks an accepted result.

### lock

Marks a rejected result.

## Operators

Supported operators:

- `is`      exact match
- `isnot`   not equal
- `has`     contains text
- `begins`  starts with
- `ends`    ends with

Examples:

scan name is "admin"
scan name isnot "guest"
scan email has "@"
scan file begins "PK"
scan path ends ".apk"

## Naming rules

Keywords use lowercase only.

Identifiers may contain:
- lowercase letters
- numbers
- underscore

Identifiers must not begin with a number.

Valid identifiers:

- email
- file_name
- user1
- apk_v2

Invalid identifiers:

- 1user
- user-name
- file.name

## Values

Numbers are written without quotes.

Example:

hold limit 10
hold code 404

Strings use double quotes.

Example:

prt "hello"
hold tag "user01"

## Examples

Example 1:

line name_check
pick name

scan name is "root"
    good prt "reserved"
    lost prt "ok"
seal

Example 2:

line email_check
pick email

scan email has "@"
    good prt "valid"
    lost prt "invalid"
seal

Example 3:

line apk_check
pick file_name

scan file_name ends ".apk"
    good prt "android package detected"
    lost prt "unknown file"
seal

Example 4:

line score_view
hold score 99
pnr score
seal

## Notes

- Dolin is line-based
- indentation is part of readability
- no semicolon is needed
- a flow must end with `seal`
- string values use double quotes
- names like `user_name` are allowed
- `prt` is universal output
- `pnr` is numeric-only output

## File extension

Recommended file extension:

- `.don`

