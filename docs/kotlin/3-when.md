# `when` Expression and Statement

`when` is a conditional expression that runs code based on multiple possible values or conditions.
It's similar to the switch statement in Java.

`when` is similar to an `if` statement, but instead of having huge `if-else` branches, it compares all branches to the same variables, reducing much boilerplate and making things cleaner.

## Usage

```kotlin
val userRole = "Editor"
when (userRole) {
    "Viewer" -> println("User has read-only access")
    "Editor" -> println("User can edit content")
    else -> println("User role is not recognized")
}
```

If we were to use `if-else` it would've looked like this:

```kotlin
val userRole = "Editor"
if(userRole == "Viewer"){
    println("User has read-only access")
}else if(userRole == "Editor"){
    println("User can edit content")
}else {
    println("User role is not recognized")
}
```

Yikes.

## Expression vs. Statement

We can use `when` either as an expression or a statement.
This means that it can be the result for a variable, or actions.

As an expression, `when` returns a value we can use later in our code. As a statement, `when` completes an action without returning a result.

<table>
   <tr>
       <td>Expression</td>
       <td>Statement</td>
   </tr>
   <tr>
<td>

```kotlin linenums="0" title=""
// Returns a string assigned to the 
// text variable
val text = when (x) {
    1 -> "x == 1"
    2 -> "x == 2"
    else -> "x is neither 1 nor 2"
}
```

</td>
<td>

```kotlin linenums="0" title=""
// Returns no result but triggers a 
// print statement
when (x) {
    1 -> print("x == 1")
    2 -> print("x == 2")
    else -> print("x is neither 1 nor 2")
}
```

</td>
</tr>
</table>