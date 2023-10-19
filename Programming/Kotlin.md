### Syntax
**Common Types** (Title case)
- Integer types
	- 32 bits: `Int`
	- 64 bits: `Long`
- Floating-point types
	- 32 bits: `Float` (6 - 7 d.p.)
	- 64 bits: `Double` (15-16 d.p.)
- Booleans
	- Logical OR: `||`
	- Logical AND: `&&`
	- Logical NOT: `!`
- Strings
	- `Strings`
- Array
	- `Array<Type>`

**Type Conversion**
- `toInt(): Int`
- `toFloat(): Float`
- `toDouble(): Double`

**Array Conversion**
- To Set: `toSet()`
- To List: `toList()`

**Program entry point**
```
fun main(){
	println("Hello world")
}
```

**Prints**
- Print without line break
```
print("Hello")
print("world")
________________________________
Hello world
```

- Print with line break
```
print("Hello")
print("world")
________________________________
Hello world
```

- String templates
```
val i = 1
println("i = $i")
________________________________
i = 1
```

- Expression
```
val s = "abc"
println("$s.length is ${s.length}")
_____________________________________
abc.length is 3
```

**Functions**
- Function with 2 integer type parameters and integer return type
```
// Addition function
fun sum(a: Int, b: Int): Int{
	return a + b
}

OR

// Return type is infered
fun sum(a: Int, b: Int) = a + b
```

**Variables**
- Read-only local variables (Immutable): `val`
- Mutable variables: `var`

**Create arrays functions**
- `arrayOf()`
- `arrayOfNulls()`
- `emptyArray()`


**Classes and instances**
```
class Rectangle(var height: Double, var length: Double){
	var perimeter = (height + length) * 2
}
```

#### Conditions and loops
**If expression**
```
var a = 5
var b = 10

var max = a
if (a < b) max = b

// with else
if (a > b) {
	max = a
} else {
	max = b
}

// as expression
max = if (a > b) a else b
```

**When expression**
```
when (x) {
	1 -> println("x == 1")
	2 -> println("x == 2")
	else -> {
		println("x is neither 1 or 2")
	}
}
```

**For loops**
```
// print from 1 to 5
for (i in 1..5){
	println(i)
}
_____________________________
1
2
3
4
5
```

