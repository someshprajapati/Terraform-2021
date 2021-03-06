## For and For-each Loop in Terraform

```
SπMESH~[3-For-and-For-Each-Loops (main)]-$ cat vars.tf
ββββββββ΄βββββββββββββββββββββββββββββββββββββββββββββββββββββββ
       β File: vars.tf
ββββββββ΄βββββββββββββββββββββββββββββββββββββββββββββββββββββββ
   1   β variable "list1" {
   2   β   type = list(string)
   3   β   default = [1, 10, 9, 101, 3]
   4   β }
   5   β variable "list2" {
   6   β   type = list(string)
   7   β   default = ["apple", "pear", "banana", "mango"]
   8   β }
   9   β variable "map1" {
  10   β   type = map(number)
  11   β   default = {
  12   β    "apple" = 5
  13   β    "pear" = 3
  14   β    "banana" = 10
  15   β    "mango" = 0
  16   β   }
  17   β }
ββββββββ΄βββββββββββββββββββββββββββββββββββββββββββββββββββββββ
```

#### Loop in Terraform
```
SπMESH~[3-For-and-For-Each-Loops (main)]-$ terraform console

> [for s in ["a", "b", "c"]: s]
[
  "a",
  "b",
  "c",
]

> [for s in ["a", "b", "c"]: upper(s)]
[
  "A",
  "B",
  "C",
]

> [for s in var.list1: s + 1]
[
  2,
  11,
  10,
  102,
  4,
]

> [for s in var.list2: upper(s)]
[
  "APPLE",
  "PEAR",
  "BANANA",
  "MANGO",
]

> [for k, v in var.map1: k]
[
  "apple",
  "banana",
  "mango",
  "pear",
]

> [for k, v in var.map1: v]
[
  5,
  10,
  0,
  3,
]

> {for k, v in var.map1: k => v}
{
  "apple" = 5
  "banana" = 10
  "mango" = 0
  "pear" = 3
}
```
