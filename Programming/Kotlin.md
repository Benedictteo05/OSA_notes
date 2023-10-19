### Syntax
**Common Types**
- Integer types

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


