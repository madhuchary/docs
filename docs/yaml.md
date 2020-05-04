---
id: yaml
title: YAML - "YAML Ain't Markup Language"
---
In this we will cover Sequence (-), Mapping (:) and datatypes.
## Comments in YAML

```yaml
# full line comment
- name # Partial comment
```
## Sequence of scalars

```yaml
- user1
- user2
- user3
```

## Scalars of Scalars

```yaml
name: user1
age: 30
mobile: 1234
```

## Scalars of Sequences: Array

```yaml
animals:
- cat
- dog
- cow
birds:
- crow
- parrot
- sparrow
```

## Sequence of Mappings

```
students:
- name: madhu
  age: 20
  location: Hyderabad
- name: sudhan
  age: 40
  location: Bangalore
```

## Multiple YAML objects in a single file

```yaml
---
- name: first yaml block

---
- name: second object in same file
```

## Multi-line scalars with "|" (pipe)

```yaml
- script: |
          #!/bin/bash
          echo "This is multi-line demo in yaml"
```

The output of above command will be 

```bash
# output

#!/bin/bash
echo "This is multi-line demo in yaml"
```


## Multi-line scalars with ">"

```yaml
script: >
          #!/bin/bash
          echo "This is multi-line demo in yaml"
```

The output of above command will be single line

```bash
# output

#!/bin/bash echo "This is multi-line demo in yaml"
```

## Strings, Intergers, float, boolean

```
name: "string"
age: 30 # Integer
salary: 10.5 # Float
working: true # boolean

```

```
-  martin:
    name: Martin D'vloper
    job: Developer
    skills:
      - python
      - perl
      - pascal
-  tabitha:
    name: Tabitha Bitumen
    job: Developer
    skills:
      - lisp
      - fortran
      - erlang
```

## Troubleshooting 
### use yamllint for syntax errors or click [here](http://www.yamllint.com/) for online yamllint
