# Command Groups/Compositions

Individual commands are capable of accomplishing a large variety of robot tasks, but what happens when we need multiple things to happen sequentially, or in parallel? For that we use Command Groups

!!! note
    Command Groups require all subsystems their components require.

### Usage

As most command group methods are pretty self-explanatory, this document will show you some examples and commented definitions.

=== "Kotlin"

    ```kotlin
    val chained = someCommand.andThen(anotherCommand) // When "someCommand" finishes, "anotherCommand" will be scheduled
    val repeats = command.repeatedly() // Restarts every time the command ends
    val racing = someCommand.raceWith(anotherCommand) // The two command will start in parallel, when one command finishes, the other will be terminated as well
    val until = someCommand.until({driver.isXPressed()}) // The command will terminate if the lambda becomes true
    val timeout = someCommand.withTimeout(5) // The command will terminate within 5 seconds
    val parallel = Commands.parallel(someCommand, anotherCommand) // These command will run in parallel
    ```

=== "Java"

    ```java
    // TODO
    ```

Easy enough, right?
