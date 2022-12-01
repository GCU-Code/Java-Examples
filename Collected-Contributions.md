---
title: Collected Contributions
subtitle: CST-105
author: Brent L. Ricks
date: July 9, 2022
subject: Exercise
---

# Collected Contributions

```java
/*
Develop a program that tabulates contributions collected by an organization. The organization wishes to accept contributions until a total of $10,000,000 is met. Once this total is hit, no further contributions should be accepted. 

The organization wants the program to read data from an input file (input.in). The following data should be written to a file called results.out
a.	The total number of contributions needed to meet the goal of 10 million dollars
b.	The amount of the largest and smallest contribution accepted
c.	The average contribution size
d.	The final total of the contributions accepted

Implement (code) and test your program with a variety of input data. It is helpful to set a smaller contribution goal when testing your program. Consider both the scenario where the input file does not contain enough contributions to meet the goal and the scenario where the input file contains more data than needed. The output file should match the formatting shown in the example.

Example Output:
It took 2007 contributions to reach the goal.
The maximum contribution received was $53,246.00.
The minimum contribution received was $7.00.
The average contribution amount was $4,982.98.
A total of $10,000,043.00 was collected.
*/

import java.util.Scanner;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.PrintWriter;
import java.text.NumberFormat;

public class Start {
	// Set a constant to be used throughout all methods.
	// This is the Goal amount to reach.
	public final static double CONTRIBUTION_GOAL = 10000000.00;

	public static void main(String[] args) throws IOException {
		// First, read file with data containing contributions.
		ReadFromFile();
	}

	public static void ReadFromFile() throws IOException {
		FileInputStream fileByteStream = null;
		Scanner fileReader = null;

		// Declare and initialize variables to be used.
		double avgContribution = 0;
		double numMin = 0;
		double numMax = 0;
		double totalContributions = 0;
		int contributionCount = 0;

		// Open file stream and reader. Retrieve file.
		fileByteStream = new FileInputStream("src/input.in");
		fileReader = new Scanner(fileByteStream);

		// Inform user of reading file start.
		System.out.println("Reading Document...");

		// Get the all the donations from the input file.
		// Use .hasNext instead of .hasDouble so we can check among text.
		while (fileReader.hasNext()) {
			try {
				/*
				 * If next is a number, we Parse to Double. Otherwise, we ignore and continue to
				 * next(). This variable is scoped to only this loop.
				 */
				double numCurrent = Double.parseDouble(fileReader.next());

				/*
				 * Set the minimum number. On first run, numMin = 0 so the first minimum is the
				 * first number.
				 */
				if (numMin == 0) {
					numMin = numCurrent;
				} else if (numCurrent < numMin) {
					numMin = numCurrent;
				}

				// Set the max number.
				if (numCurrent > numMax) {
					numMax = numCurrent;
				}

				/*
				 * We only want to track the number of contributions required to meet the stated
				 * CONTRIBUTION_GOAL. If the goal is not met, we add one to the count.
				 */
				if (totalContributions <= CONTRIBUTION_GOAL) {
					++contributionCount;
				}

				// Add the current amount to the total and get average (inclusive)
				totalContributions += numCurrent;
				avgContribution = totalContributions / contributionCount;

			} catch (Exception e) {
				// Do nothing and continue to next input.
			}
		}

		// Close the file reader & byte stream.
		fileReader.close();

		// Now that the file has been read, pass in the variables to SaveToFile method.
		SaveToFile(totalContributions, numMax, numMin, avgContribution, contributionCount);
	}

	public static void SaveToFile(double total, double max, double min, double avg, int count) throws IOException {
		NumberFormat formatCurrency = NumberFormat.getCurrencyInstance();
		FileOutputStream fileOutStream = null;

		// Open file stream to write to file.
		fileOutStream = new FileOutputStream("src/results.out");

		// Create a variable to hold the different statuses.
		String goalStatus = "";

		// Check total received against the set goal.
		if (total < CONTRIBUTION_GOAL) {
			// Did not meet goal.
			goalStatus = "Unfortunately, you did not meet the " + formatCurrency.format(CONTRIBUTION_GOAL)
					+ " goal. \nBelow you will find the results:";
		} else if (total >= CONTRIBUTION_GOAL) {
			// Exceeded goal.
			goalStatus = "It took " + count + " contributions to reach the goal.";
		} else {
			// Goal was met. (probably EXTREMELY rare, but just in case :-)
			goalStatus = "It took " + count + " contributions to reach the EXACT goal.";
		}

		// Open file writer.
		PrintWriter fileWriter = null;
		fileWriter = new PrintWriter(fileOutStream);

		// Write the information to the file.
		fileWriter.println(goalStatus);
		fileWriter.println("The maximum contribution received was: " + formatCurrency.format(max) + ".");
		fileWriter.println("The minimum contribution received was: " + formatCurrency.format(min) + ".");
		fileWriter.println("The average contribution received was: " + formatCurrency.format(avg) + ".");
		fileWriter.println("A total of " + formatCurrency.format(total) + " was collected.");

		// Close the file writer & output stream.
		fileWriter.close();

		// Let the user know that the task has completed.
		System.out.println("Completed Reading Document.");
		System.out.println("---------------------------");
		System.out.println(goalStatus);
	}
}
```

