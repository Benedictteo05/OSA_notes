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

**Type Conversion**
- `toInt(): Int`
- `toFloat(): Float`
- `toDouble(): Double`

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



**Classes and instances**
```
class Rectangle(var height: Double, var length: Double){
	var perimeter = (height + length) * 2
}
```


