# TRI

TRI is a variant of RDF Turtle with N3 rules and indentation, focusing on the manual editing of RDF triples.

## Roadmap

- [ ] Syntax
- [ ] Parser
- [ ] Highlight
- [ ] Language Server

## Syntax

### Indentation

Use indentation instead of punctuations (`,;.`). A level of indentation should be made when term are moved to the next line.

```turtle
ex:a ex:b ex:c

ex:a ex:b
  ex:c

ex:a
  ex:b ex:c

ex:a
  ex:b
    ex:c

# all are equiv to 

ex:a ex:b ex:c .
```

The same level of indentation adds a new sentence/predicate/object 

```turtle
ex:a
  ex:b ex:c
       ex:d
  ex:e ex:f
ex:g ex:h ex:i

# is equiv to

ex:a ex:b ex:c .
ex:a ex:b ex:d . 
ex:a ex:e ex:f .
ex:g ex:h ex:i .
```

**TBD**: syntax for multi-line string. Yaml may be a good example.

**TBD**: how to handle `<<:a :b :c>>` and `{| :b :c |}`. (prefer wisp like syntax)

### Rules

The [N3 Builtin Functions](https://w3c-cg.github.io/n3Builtins/) can be directly used.

The N3 syntax

```notation3
{ ?paper :title ?title } => { ?paper a :Paper } .
```

can be written as 

```turtle
(<< _:paper :title _:title >>) => (<< _:paper a :Paper >>)
```

where `{}` graph is viewed as a list of quoted triples `<<>>`,
variable `?a` as scoped usage of blank node `_:a`.
And `=>` is just `log:implies`, like `a` for `rdf:type`.

### Language Server

To be implemented.
