#if-expression

Zig's if statements accept `bool` values (i.e. `true` or `false`). Unlike languages like C or JavaScript, there are no values that implicitly coerce to bool values.

Ternary conditional operators (cond ? a : b) do not exist in zig.
```zig
const expect = @import("std").testing.expect;

test "if statement" {
    const a = true;
    var x: u16 = 0;
    if (a) {
        x += 1;
    } else {
        x += 2;
    }
    try expect(x == 1);
}
```

If statements also work as expressions.
```zig
test "if statment expression" {
	const a = true;
	var x: u16 = 0;
	x += if(a) 1 else 2;
	try expect(x == 1);
}
```