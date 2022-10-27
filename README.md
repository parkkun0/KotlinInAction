# KotlinInAction 
testing out and practicing codes in the book, "Kotlin In Action"

## KotlinInAction Summary & Takeaways
### Chapter 2: Basics
#### How to use arguments on main
```
fun main (args: Array<String>) {
  val name
  if (args.size > 0) {
    name = args[0]
  else
    name = "Kotlin"
  println("Hello $name")
}
```

#### Kotlin Packaging
Kotlin can put multiple classes on a single fiel and make a file name different from class name

#### Powerful `when` statement
since when can take expression for its condition check, we can do the following
```
fun mix (c1: Color, c2: Color) =
  when (setOf(c1, c2)) {
    setOf(RED, YELLOW) -> ORANGE
    setOf(YELLOW, BLUE) -> VIOLET
    setOf(BLUE, VIOLET) -> INDIGO
    else -> throw Exception("Dirty color")
  }
```

#### `in` operator
`in` operator checks if certain value is in between a designated range
```
fun isLetter(c: Char) = c in 'a'..'z' || c in 'A'..'Z'
val isInBetween = "Kotlin" in "Java".."Scala"
```
The expression that use in needs to be `Comparable`

### Chapter 3: Function declaration and invokation
#### multi-tupled return values
tupled return is possible
```
for ((index, element) in collection.withIndex()) {
  if (index > 0) result.append(separator)
  result.append(element)
}
```

#### @JvmOverloads
The annotation auto-generates Functions in Java that skips each parameter declaration starting from the last one to the first.
Each skipped parameter would use default parameter declared in Kotlin.
```
@JvmOverloads
fun <T> joinToString(
  collection:Collection<T>
  separator: String = ", ",
  prefix: String = ""
): String

String joinToString(Collection<T> collection, String separator, String prefix);
String joinToString(Collection<T> collection, String separator);
String joinToString(Collection<T> collection);
```

#### @file:JvmName
This annotation lets you choose the class name mapped in Java
```
@file:JvmName("StringFunctions")
package strings
fun joinToString(...): String { ... }

/* Java */
import strings.StringFunctions;
StringFunctions.joinToString(list, ...)
```

#### Extension Functions cannot be overriden

#### If a signature of member function and extension functions are the same, the member function has the precedence, meaning member function will be called.

#### Handling Paired values, infixes, and destructuring declaration
```
1.to("one") //is equivalent to 
1 to "one"

infix fun Any.to(other: Any) = Pair(this, other)

val (number, name) = 1 to "one"
```

#### Local functions
```
fun saveUser(user: User) {
  fun validate(value: String, fieldName: String) {
    println("${user.id} has $value for @fieldName") // has reference to outer function
  }
  validate(user.name, "Name")
  validate(user.address, "Address")
}
```


