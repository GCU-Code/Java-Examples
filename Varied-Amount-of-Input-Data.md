---
title: LAB 3-33: Varied Amount of Input Data
subtitle: CST-105
author: Brent L. Ricks
date: July 8, 2022
subject: Lab
---

# LAB 3-33: Varied Amount of Input Data

```java
/*
Statistics are often calculated with varying amounts of input data. Write a program that takes any number of non-negative integers as input, and outputs the max and average. A negative integer ends the input and is not included in the statistics.

Ex: When the input is: 15 20 0 5 -1
the output is: 20 10

You can assume that at least one non-negative integer is input.
*/

import java.util.Scanner; 

public class LabProgram {
   public static void main(String[] args) {
		Scanner scnr = new Scanner(System.in);
		// Set up variables and initialize them.
		int numInput = 0;
		int numMax = 0;
		int numCount = 0;
		int numSum = 0;
		double numAverage = 0;

      // This will always be true at start since initialized with 0.
		while (numInput >= 0) {
			numInput = scnr.nextInt();
			
			// If input is 0 or more, we need to add it to the count and sum.
			// In averages, a zero is not ignored but factored in.
			if (numInput >= 0) {
				numSum += numInput;
				++numCount;
				
				// Check to see if new input is larger than current max.
				if (numInput > numMax) {
					numMax = numInput;
				}
			}
		}

      // Quick error handling to catch first input being 0.
		if (numSum != 0) {
			numAverage = (double)numSum / (double)numCount;
		}
		
		// Print the max.
		System.out.print(numMax);

      // Check to see if there is a remainder for double, if no, remove decimal.
      // If double has remainder, only take to the hundreth place.
		if (numAverage % 1 == 0) {
			System.out.printf(" %.0f", numAverage);
		} else {
			System.out.printf(" %.2f", numAverage);
		}
		System.out.println();
   }
}
```