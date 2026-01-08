#while-loop

Zig's while loop has three parts - a condition, a block and a continue expression.

Without a continue expression.
```zig
test "while" {
	var i: u8 = 2;
	while (i<100) {
		i *= 2;
	}
	try expect(i == 128);
}
```

With a continue expression.

```zig
test "while with continue expression" {
	var i: u8 = 2;
	while (i<10) : (i += 1) {
		sum += i;
	}
	try expect(i == 55);
}
```

With a `continue`.
```zig
test "while with continue" {
	var i: u8 = 2;
	while (i<3) : (i += 1) {
		if(i == 2) continue;
		sum += i;
	}
	try expect(i == 55);
}
```
With a `break`.

```zig
test "while with break" {
	var sum: u8 = 0;
	var i: u8 = 0;
	while (i <= 3) : (i += 1) {
		if (i == 2) break;
		sum += i;
    }
    try expect(sum == 1);
}
```

