## Introduction to YAML

- YAML stands for YAML Ain’t Markup Language

- It is a vert simple, text based and human readable language which is used to exchange the data between people and computer.

- YAML is used to store key-value pairs, or mappings and lists or sequence of elements

_Note :_

```
1. YAML is not a programming language and it is mostly used for storing configuration information
2. Every YAML file starts with “---” and ends with “…” and it is optional
3. There should be space between : and the value
```

**Syntax :**

```
key: value
```

**Examples :**

1. Simple key-value

```
---
person:
  name: sudhanshu
  address: bangalore
  sex: male
```

2. List

```
---
Color:
  - red
  - yellow
  ...
```

3. List inside dictionary

```
---
person:
  name: sudhanshu
  address: bangalore
  sex: male
  skills:
    - ansible
    - terraform
    - jenkins
...
```

4. List of dictonaries

```
---
- person1:
    name: sudhanshu
    address: bangalore
    sex: male
    skills:
      - ansible
      - terraform
      - jenkins

- person2:
    name: himanshu
    address: bangalore
    sex: male
    skills:
      - java
      - spring
      - python
...
```
