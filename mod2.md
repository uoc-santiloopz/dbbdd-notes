# Disseny conceptual

## UML

### Data types
* String
* Integer
* date
* boolean

### Multiplicity
`name: String[min..max]`
`name: String[*]`

### Derivate attr
`\name: type`

### Primary key
`name <P>: type`

### Candidate key
`name <Un>: type` -> pag 20

### Cardinality
* 1 === 1..1
* * === 0..n
* n..m
* optional === 0..1
* compulsory === 1..*

In ternary:  
* M:N:P or *..*..*.
* M:N:1 or *..*..1.
* M:1:1 or *..1..1.
* 1:1:1 or 1..1..1.
