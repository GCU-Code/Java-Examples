---
title: 5-Digit Computation
subtitle: CST-105
author: Brent L. Ricks
date: July 9, 2022
subject: Exercise
---

# 5-Digit Computation

```java
/*
Write a program that prompts the user to enter a 5-digit positive integer. Using only the / and % operations, compute each individual digit and display the sum of the digits. 

Example:
Enter a 5-digit positive integer: 30458
The sum of the digits is 3 + 0 + 4 + 5 + 8 = 20
*/

import java.util.Scanner;

public class FiveDigitCompute {
	public static void main(String[] args) {
		// Add a try catch in case something other than an integer is entered.
		try (Scanner scnr = new Scanner(System.in)) {
			boolean run = true;

			// Holds the input from the user.
			int numUserInput;
			// Holds the count of digits in the entered integer.
			int numDigitCount;
			// Holds the sum of individual digits.
			int numDigitSum;

			// Create variables to hold each digit in integer.
			int num1stDigit;
			int num2ndDigit;
			int num3rdDigit;
			int num4thDigit;
			int num5thDigit;

			// While true, the program will start over if an in correct integer is entered.
			while (run) {
				System.out.println("Please inter a 5-digit positive integer to see the sum of its digits.");
				// Get the user input and set the count of digits in the entered integer.
				numUserInput = scnr.nextInt();
				numDigitCount = String.valueOf(numUserInput).length();

				// Check if the integer meets the digits requirement (5) and is positive.
				if (numDigitCount == 5 && numUserInput > 0) {
					num1stDigit = numUserInput / 10000;
					num2ndDigit = numUserInput / 1000 % 10;
					num3rdDigit = numUserInput / 100 % 10;
					num4thDigit = numUserInput / 10 % 10;
					num5thDigit = numUserInput % 10;

					// Add the digits up to get and set the sum.
					numDigitSum = num1stDigit + num2ndDigit + num3rdDigit + num4thDigit + num5thDigit;

					// Display the individual digits and sum as an equation.
					System.out.println(num1stDigit + " + " + num2ndDigit + " + " + num3rdDigit + " + " + num4thDigit
							+ " + " + num5thDigit + " = " + numDigitSum);
					run = false;
				} else {
					// I the integer entered is NOT a 5-digit positive, notify user and start over.
					System.out.println("You did not enter a 5-digit positive integer.\n");
					run = true;
				}
			}
		} catch (Exception e) {
			// Something went horribly wrong (most likely a non-integer was entered).
			System.out.println(
					"Uh Oh! You must have not entered an integer.\n To try again, you must restart the program.");
		}
	}
}
```

