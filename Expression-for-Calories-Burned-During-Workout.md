---
title: LAB 2-33: Expression for Calories Burned During Workout
subtitle: CST-105
author: Brent L. Ricks
date: July 8, 2022
subject: Lab
---

# LAB 2-33: Expression for Calories Burned During Workout

```java
/*
The following equations estimate the calories burned when exercising (source):

Women: Calories = ( (Age x 0.074) — (Weight x 0.05741) + (Heart Rate x 0.4472) — 20.4022 ) x Time / 4.184

Men: Calories = ( (Age x 0.2017) + (Weight x 0.09036) + (Heart Rate x 0.6309) — 55.0969 ) x Time / 4.184

Write a program using inputs age (years), weight (pounds), heart rate (beats per minute), and time (minutes), respectively. Output calories burned for women and men.

Output each floating-point value with two digits after the decimal point, which can be achieved as follows:
System.out.printf("%.2f", yourValue);

Ex: If the input is:

49 155 148 60
the output is:

Women: 580.94 calories
Men: 891.47 calories
*/

import java.util.Scanner;

public class LabProgram {
   public static void main(String[] args) {
      Scanner scnr = new Scanner(System.in);
      int age;
      double weight;
      double heartRate;
      double time;
      double caloriesBurnedMen;
      double caloriesBurnedWomen;
      
      age = scnr.nextInt();
      weight = scnr.nextDouble();
      heartRate = scnr.nextDouble();
      time = scnr.nextDouble();
      
      // Women: Calories = ( (Age x 0.074) — (Weight x 0.05741) + (Heart Rate x 0.4472) — 20.4022 ) x Time / 4.184
      // Men: Calories = ( (Age x 0.2017) + (Weight x 0.09036) + (Heart Rate x 0.6309) — 55.0969 ) x Time / 4.184
      // System.out.printf("%.2f", yourValue);
      
      caloriesBurnedWomen = ((age * 0.074) - (weight * 0.05741) + (heartRate * 0.4472) - 20.4022) * time / 4.184;
      caloriesBurnedMen = ((age * 0.2017) + (weight * 0.09036) + (heartRate * 0.6309) - 55.0969) * time / 4.184;
      
      System.out.print("Women: ");
      System.out.printf("%.2f", caloriesBurnedWomen);
      System.out.println(" calories");
      System.out.print("Men: ");
      System.out.printf("%.2f", caloriesBurnedMen);
      System.out.println(" calories");
   }
}
```