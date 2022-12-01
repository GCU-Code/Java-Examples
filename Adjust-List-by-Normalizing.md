---
title: LAB 4-25: Adjust List by Normalizing
subtitle: CST-105
author: Brent L. Ricks
date: July 9, 2022
subject: Lab
---

# LAB 4-25: Adjust List by Normalizing

```java
/*
When analyzing data sets, such as data for human heights or for human weights, a common step is to adjust the data. This adjustment can be done by normalizing to values between 0 and 1, or throwing away outliers.

For this program, adjust the values by dividing all values by the largest value. The input begins with an integer indicating the number of floating-point values that follow. Assume that the list will always contain fewer than 20 floating-point values.

Output each floating-point value with two digits after the decimal point, which can be achieved as follows:
System.out.printf("%.2f", yourValue);

Ex: If the input is: 5 30.0 50.0 10.0 100.0 65.0
the output is: 0.30 0.50 0.10 1.00 0.65 

The 5 indicates that there are five floating-point values in the list, namely 30.0, 50.0, 10.0, 100.0, and 65.0. 100.0 is the largest value in the list, so each value is divided by 100.0.

For coding simplicity, follow every output value by a space, including the last one.
*/

import java.util.Scanner;
import java.util.ArrayList;

public class LabProgram {
   public static void main(String[] args) {
      Scanner input = new Scanner(System.in);
      ArrayList<Double> numList = new ArrayList<Double>();
      double numCurrent = 0.0;
      double numMax = 0.0;
      double numTemp = 0.0;
      
      int numTotal = input.nextInt();
      while(input.hasNextDouble()){
         numCurrent = input.nextDouble();
         numList.add(numCurrent);
         if(Math.abs(numCurrent) > Math.abs(numMax)){
            numMax = numCurrent;
         }
      }
      for(double i:numList){
         numTemp = i / (double)numMax;
         if(numTemp > 0 && numTemp <= 1){
            System.out.printf("%.2f ", numTemp);
         }
      }
      System.out.println();
   }
}
```

