# MAD - Exercise 01
## Tasks
* Watch the Kotlin Crashcourse Video in Moodle or complete the tutorials **[Introduction to programming in Kotlin](https://developer.android.com/courses/pathways/android-basics-compose-unit-1-pathway-1)** and **[Kotlin fundamentals](https://developer.android.com/courses/pathways/android-basics-compose-unit-2-pathway-1
)**.
* Answer the questions inside this Readme.md file and push it to your repository.
* Submit your coding solution of the Number Guessing Game inside the repository.
* Submit the link to your repository in Moodle.

## Questions
### Describe how Kotlin handles null safety. What are nullable types and non-null types in Kotlin? (0,5 points)

<span style="color:blue">Kotlin is null safe, which is useful in case of preventing NullPointerExceptions, means that you can´t declare null typically. But there is a way you can, and that´s with the ? after the Datatype, for this example it would be String?</span>
> Note: you can also use code snippets to illustrate your answer. 

```kotlin 
// example code snippet for using null
val a: String? = null // null type
```

<span>For the cases below we can use "!!" to force the .toLowerCase() (errors can occur), the other options we have is with the "?" where compiler checks if a is null, in the case of it being null, the .toLowerCase() is being ignored. If it´s not null the .toLowerCase() is being executed. What we could also do is check if a is null with an if.</span>
```kotlin 
// example code snippet
val a: String? = null // non-null type
a.toLowerCase() // would not work
a!!.toLowerCase() // should use this usualy, only in cases we are 100% sure we need it
a?.toLowerCase() // typical approach

if(a != null){
    a.toLowerCase()
}
```

```kotlin 
// example code snippet
val a: String = "value" // non-null type
```

### What are lambda expressions and higher order functions in Kotlin? Why would you store a function inside a variable? (0,5 points)

<span style="color:blue">They are like objects that can be saved in variables. It´s better for overview and you write less code for more funcitonality. Higher Order Functions can use other functions as parameters, which is useful when we have separated logic in two functions but need them in another function</span>

```kotlin 
val printMessages: (String) -> Unit = {println("User: $it")}

val printMessagesForAdmin: (String) -> Unit = {println("Admin: $it")}

fun printCustomMessage(message: String, printMessages: (String) -> Unit) {
    printMessages(message)
}

printCustomMessage("Hello I´m user anna", printMessages)
printCustomMessage("Hello I´m user manu", printMessagesForAdmin)

```

### Provide a solution for the following number guessing game inside `App.kt`. (3 points)

## Number Guessing Game in Kotlin
The game is a simple number guessing game. The task is to generate a random, max 9-digit, number. The number must **not contain repeating digits**. Valid digits are 1-9.
Ask the user to guess the max 9-digit number. The game is finished when the user guesses the correct digits in the correct order.
In each round, the user gets feedback about the number of correct digits and the number of correct digits in the correct position.
The output should be in the format "n:m", where "n" is the number of digits guessed correctly regardless of their position, 
and "m" is the number of digits guessed correctly at their correct position. Here are some examples:

This example shows the game flow with 4-digits to guess (the default argument)

Generated number: 8576
-	User input: 1234, Output: 0:0
-	User input: 5678, Output: 4:1
-	User input: 5555, Output: 1:1
-	User input: 3586, Output: 3:2
-	User input: 8576, Output: 4:4 -> user wins

Take a look into the provided code structure in `src/main/kotlin/App.kt`. Implement the following methods (lambda expressions):
- _playNumberGame(digitsToGuess: Int = 4)_ (1 point): The main game loop that handles user input and game state. Make use of _generateRandomNonRepeatingNumber_ and _checkUserInputAgainstGeneratedNumber_ here. This function also utilizes a default argument 
- _generateRandomNonRepeatingNumber_ (1 point): A lambda expression that generates a random number with non-repeating digits of a specified length.
- _checkUserInputAgainstGeneratedNumber_ (1 point): A lambda expression that compares the user's input against the generated number and provides feedback.

``CompareResult.kt`` This class is a data structure which helps with bundling the result of the comparison of the user input and the generated number. Look at the toSting() and use it in your output.

Run the project with `./gradlew run` and test your implementation with the provided tests in `src/test/kotlin/AppTest.kt` with `./gradlew test`.

# Project Structure
The project is structured into two main Kotlin files:

**App.kt**: Contains the main game logic and functions.

**AppTest.kt**: Contains unit tests for the various functions in App.kt.

