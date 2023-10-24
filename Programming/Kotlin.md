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


**Variables**
- Read-only local variables (Immutable): `val`
- Mutable variables: `var`


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
Hello 
world
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

**Create arrays functions**
- `arrayOf()`
- `arrayOfNulls()`
- `emptyArray()`


#### Conditions and loops
**If expression**
```
// Simple if statement
var max = a
if (a < b) max = b

// With else
if (a > b) {
	max = a
} else {
	max = b
}

// As expression
max = if (a > b) a else b
```

**When expression**
```
when (x) {
	1 -> println("x == 1")
	2 -> println("x == 2")
	3, 4 -> println("x is 3 or 4")
	in 5..6 -> println("x is in range")
	else -> {
		println("none of the above")
	}
}
```

**For loops**
```
// print from 1 to 4
for (i in 1..5){
	println(i)
}
_____________________________
1
2
3
4
```


#### Classes and Objects
**Classes and instances**
```
class Rectangle(var height: Double, var length: Double,){
	var perimeter = (height + length) * 2    //Property initializer
	init {
		self.height = height
		self.length = length
		self.perimeter = perimeter
	}
}

// Class open for inheritance, default is final
open class Rectangle(var height: Double, var length: Double,){
	var perimeter = (height + length) * 2    //Property initializer
}
```


### Resources & Layout
**Resource Directories**

|Directory| |
|-------|----|
|color/|XML files that define a state list of colors|
|drawable/|Bitmap files (.png, .9.png, .jpg, .gif) or XML files that are compiled into the following drawable resource subtypes: Bitmap files Nine-Patches (re-sizeable bitmaps) StatelistsShapesAnimation drawablesOther drawables|
|layout/|XML files that define a user interface layout|
|menu/|XML files that define application menus, such as an Options Menu, Context Menu, or Sub Menu|
|values/|XML files that contains simple values, such as strings, integers, and colors|
|raw/|Arbitrary files to save in their raw form|
|xml/|Arbitrary XML files that can be read at runtime by calling Resources.getXML()|
|animator/| XML files that define property animations.  
|anim/| XML files that define tween animations. (Property animations can also be saved in this directory, but the animator/ directory is preferred for property animations to distinguish between the two types.)| 
|mipmap/| Drawable files for different launcher icon densities|


**ID**
- XML resource that provides a unique identifier for application resources and components.
- Unique resource ID defined in XML.
```
<TextView
android:layout_width="fill_parent"
android:layout_height="wrap_content"
			android:text="My TextView"
			andriod:text="@+id/myTV"
/>
```

**String**
- Provides text strings for application with optional text styling and formatting.
- 3 types of resources that can provide your application with strings"
	- String
	- String Array
	- Quantity Strings (Plurals)
- Resides in /res/values subdirectory
- File name as strings.xml
- Name & Value pair method
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
	<string name="hello">hello</string>
	<string name="app_name">hello appname</string>
<resources>
```

**Compiled/ Non-Compiled Resource**
- XML examples are compiled resources
	- Gets compiled into binary format before becoming part of the installable package
	- Use Android supplied XML readers to read the XML nodes

- Non-Compiled resource
	- Placed in res/raw/directory
	- Gets copied as-is to the device
	- Explicit stream-based APIs to read these files
		- e.g. Audio and Video files

