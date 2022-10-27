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
```
for ((index, element) in collection.withIndex()) {
  if (index > 0) result.append(separator)
  result.append(element)
}
```
