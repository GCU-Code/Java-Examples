---
title: Guessing Game
subtitle: CST-105
author: Brent L. Ricks
date: July 9, 2022
subject: Exercise
---

# Guessing Game

```java
/*
Write a "guessing game" program that generates a random integer between 1 and 10000, inclusive. The program should prompt the user to enter a guess. For each guess, the program will output ‘HIGHER’ if the user's guess is lower than the target, ‘LOWER’ if the user's guess is higher than the target, or ‘WINNER’ if the user guesses the target. Each time the program prompts the user for a new guess, it should calculate and display the eligible range of values.

Example:
Please enter a value between 1 and 10000: 
5000
LOWER
Please enter a value between 1 and 4999:
4000
HIGHER
Please enter a value between 4001 and 4999:
4640
WINNER
*/

import java.util.Random;
import java.util.Scanner;

public class Start {
	public static void main(String[] args) {
		Scanner scnr = new Scanner(System.in);
		Random randGen = new Random();

		// Set up the global variables to be used.
		int numMin = 1;
		int numMax = 10000;
		int numRandom = randGen.nextInt(1000) + 1;
		int numInput = 0;

		System.out.println("Please enter a value between " + numMin + " and " + numMax + ".");

		// Input is a valid integer. Game starts.
		while (scnr.hasNextInt()) {
			numInput = scnr.nextInt();

			// Check if valid number within the range.
			if ((numInput < numMin) || (numInput > numMax)) {
				System.out.println("You did not enter an integer between " + numMin + " and " + numMax);
				System.out.println("Please enter a value between " + numMin + " and " + numMax + ".");
			}
			
			// Does the entered number match the random generated?
			else if (numInput != numRandom) {
				
				// Evaluate if LOWER or HIGHER
				if (numInput < numRandom) {
					
					// Set the new minimum.
					numMin = numInput;
					System.out.println("HIGHER");
					System.out.println("Please enter a value between " + numMin + " and " + numMax + ".");
				} else {
					
					// Set the new maximum.
					numMax = numInput;
					System.out.println("LOWER");
					System.out.println("Please enter a value between " + numMin + " and " + numMax + ".");
				}
			}
			
			// Numbers must match. WINNER!
			else {
				System.out.println("WINNER");

				// Terminate game
				System.exit(0);
			}
		}

		// User entered a non-integer and must restart to play.
		if (!scnr.hasNextInt()) {
			System.out.println("Only integers may be used in this game.\nPlease restart to play again.");
		}	
		scnr.close();
	}
}
```

