#assignmet 
# Assignment

Value assignment has the following syntax: `(const|var) identifier[: type] = value`.

- `var` indicates that `identifier` is a **variable** that stores a mutable value.
- `: type` is a type annotation for `identifier`, and may be omitted if the data type of `value` can be inferred.

```zig
const constant: i32 = 5; // signed 32-bit constant
var variable: u32 = 5000; // unsigned 32-bit variable

// @as performs an explicit type coercion
const inferred_constant = @as(i32, 5);var inferred_variable = @as(u32, 5000);
```

Constants and variables _must_ have a value. If no known value can be given, the [`undefined`](https://ziglang.org/documentation/master/#undefined) value, which coerces to any type, may be used as long as a type annotation is provided.

```zig
const a: i32 = undefined;
var b: u32 = undefined;
```

