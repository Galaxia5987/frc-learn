# The Static Modifier

In previous documents we learned that everything in Java is an object, **Everything**.
Even the `main` method which seems so simple, is enclosed in a `Main` class(which is in fact an object too). But what happens when we just want a property or method that is general? Something that doesn't have this object hierarchy like in real life. Sometimes this simplicity is all we want and need.

For that we have the static modifier.

## What is it?

The static modifier works on properties and methods, and seperates them from class instances, to the general class interface.
This means that each property or method which has the static modifier will not be tied to any instance, and be "floating" inside the class.

We have two types of variables in the class scope:

* Non-static (Instance bound): Belongs to a specific object. Every object gets it's own personal copy.

* Static: Belongs to the class itself. There is only one copy, and everyone shares it.

## How do we write it?

Take the following example:
```java
public class Player {
    private String name;
    private int score;
    private static int totalPlayers = 0;

    public Player(String playerName) {
        this.name = playerName;
        this.score = 0;
        
        totalPlayers++; 
    }

    public void winMatch() {
        this.score += 10;
        System.out.println(this.name + " won! Score is now: " + this.score);
    }

    public static void printPlayerCount() {
        System.out.println("Total players currently in game: " + totalPlayers);
    }
}
```
```java
public class Main {
    public static void main(String[] args) {
        Player.showPlayerCount(); // Total players: 0

        Player player1 = new Player("John");
        Player player2 = new Player("Jane");

        player1.winMatch(); // player1 score becomes 10
        player1.winMatch(); // player1 score becomes 20
        player2.winMatch(); // player2 score becomes 10(player1 score is unaffected)

        // Even though player1 and player2 are separate, they share totalPlayers as it's static.
        Player.showPlayerCount(); // Output: Total players: 2
    }
}
```
