---
title: Temperature Converter
subtitle: CST-105
author: Brent L. Ricks
date: July 9, 2022
subject: Exercise
---

# Temperature Converter

```java
/*
Write a program that prompts the user to enter a temperature in degrees Fahrenheit. Convert the temperature to degrees Celsius. Then prompt the user to enter a temperature in Celsius. Convert the temperature to degrees Fahrenheit. The formulas needed are C = (F – 32) * 5/9 and F = 9/5*C + 32.

Example:
Enter a Fahrenheit temperature:  100
100F is equivalent to 37.777…C
Enter a Celsius temperature:  100
100C is equivalent to 212F
*/

import java.util.Scanner;

public class TemperatureConverter {
	public static void main(String[] args) {
		try (Scanner scnr = new Scanner(System.in)) {
			// Used for while loops to run.
			boolean isNumber = true;

			// Create variables to hold inputs from user.
			String numUserInputTemp;
			String numTempCelsius;
			String numTempFahrenheit;

			/*********************************************
			 * 
			 *      Convert Fahrenheit to Celsius
			 * 
			 *********************************************/
			
			// Request user input for Fahrenheit.
			System.out.print("Enter a Fahrenheit temperature: ");

			while (isNumber) {
				// If entered value is not a double, notify user and try again.
				// Otherwise, continue with conversion.
				if (!scnr.hasNextDouble()) {
					System.out.println("You did not enter a valid number.\nPlease try again. ");
					scnr.next();
				} else {
					// Capture the input & convert to Celsius.
					numUserInputTemp = scnr.next();
					numTempCelsius = String.valueOf((Double.parseDouble(numUserInputTemp) - 32) * 5 / 9);

					// Format temperature value. Check to see if value is an integer.
					if (numTempCelsius.endsWith(".0")) {
						// Value is an integer so remove the '.0' from the string's value.
						numTempCelsius = String.format("%.0f", Double.parseDouble(numTempCelsius));
					} else {
						// Value is not an integer, so include only the hundredth after the decimal.
						// Future iteration might include rounding to the nearest hundredth.
						numTempCelsius = String.format("%.2f", Double.parseDouble(numTempCelsius));
					}

					// Display output to user
					System.out.println(numUserInputTemp + "F is eqivalent to " + numTempCelsius + "C");

					// Break out of the while loop and continue to next prompt.
					break;
				}
			}

			/*********************************************
			 * 
			 *      Convert Celsius to Fahrenheit
			 * 
			 *********************************************/

			// Request user input for Celsius.
			System.out.print("Enter a Celsius temperature: ");

			while (isNumber) {
				// If entered value is not a double, notify user and try again.
				// Otherwise, continue with conversion.
				if (!scnr.hasNextDouble()) {
					System.out.println("You did not enter a valid number.\nPlease try again. ");
					scnr.next();
				} else {
					// Capture the input & convert to Celsius.
					numUserInputTemp = scnr.next();
					numTempFahrenheit = String.valueOf(Double.parseDouble(numUserInputTemp) * 9 / 5 + 32);

					// Format temperature value. Check to see if value is an integer.
					if (numTempFahrenheit.endsWith(".0")) {
						// Value is an integer so remove the '.0' from the string's value.
						numTempFahrenheit = String.format("%.0f", Double.parseDouble(numTempFahrenheit));
					} else {
						// Value is not an integer, so include only the hundredth after the decimal.
						// Future iteration might include rounding to the nearest hundredth.
						numTempFahrenheit = String.format("%.2f", Double.parseDouble(numTempFahrenheit));
					}

					// Display output to user
					System.out.println(numUserInputTemp + "C is eqivalent to " + numTempFahrenheit + "F");

					// Break out of the while loop. Program ends.
					break;
				}
			}
		} catch (NumberFormatException e) {
			e.printStackTrace();
		}
	}
}
```

