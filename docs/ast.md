# Dolin AST Design

This file defines the early abstract syntax tree structure for Dolin.

## Root

A Dolin file is represented as a program.

Program
- rules: list of RuleNode

## Rule node

A rule contains a name and a body.

RuleNode
- name
- body

## Statement types

The body of a rule contains statements.

Supported statement nodes:

- TakeNode
- SetNode
- WhenNode
- ShowNode
- AllowNode
- DenyNode

## Take node

Represents an input declaration.

Example:

take username

Shape:

TakeNode
- name

## Set node

Represents a value assignment.

Example:

set role "guest"

Shape:

SetNode
- name
- value

## Show node

Represents output text.

Example:

show "valid"

Shape:

ShowNode
- value

## Allow node

Represents an accepted result.

Example:

allow

Shape:

AllowNode

## Deny node

Represents a rejected result.

Example:

deny

Shape:

DenyNode

## When node

Represents a conditional branch.

Example:

when email has "@"
then show "valid"
else show "invalid"

Shape:

WhenNode
- left
- operator
- right
- then_branch
- else_branch

## Condition model

Condition parts:

- left: identifier
- operator: is | not | has | starts | ends
- right: literal or identifier

## Example AST shape

Source:

rule email_check
take email

when email has "@"
then show "valid"
else show "invalid"
done

AST:

Program
- RuleNode
  - name: email_check
  - body
    - TakeNode
      - name: email
    - WhenNode
      - left: email
      - operator: has
      - right: "@"
      - then_branch
        - ShowNode
          - value: "valid"
      - else_branch
        - ShowNode
          - value: "invalid"

