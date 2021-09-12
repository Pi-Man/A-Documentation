#Structure definition

##syntax
```
struct <Name[:GenericArg]...[*(LengthArg|?)]> { <field>,... }
```

##specification
`Name`, `GenericArg`, `LengthArg`, and `field` must start with [a-zA-Z_] but may contain any [a-zA-Z0-9_]
any number of `GenericArg`s may be used
if `LengthArg` is used, the struct can only accept compile time fixed lengths
if `?` is used as a length, the struct is responsible for determining its own size at runtime
the last field may or may not end with `,`
it is recommended that `GenericArg` use `T` for type and `N` for size and any single capital letter for anything else
it is recommended that `LengthArg` be `L`

shall define a type that will allocate and manage space for all provided fields
if a `LengthArg` or `?` is not provided, then uppon instantiating as an array, the given number of elements will be allocated in a single continuous block

##examples
```
struct Foo {
  int:32 i,
  float:64 d
}
```
```
struct Bar:N {
  int:N i,
  float:N f
}
```
```
struct FooBar:T:N {
  T:N a,
  float:N f,
  T:32 b
}
```