---
title: LAB 3-30: Interstate Highway Numbers
subtitle: CST-105
author: Brent L. Ricks
date: July 8, 2022
subject: Discussion Topic
---

# LAB 3-30: Interstate Highway Numbers

```java
/*
Primary U.S. interstate highways are numbered 1-99. Odd numbers (like the 5 or 95) go north/south, and evens (like the 10 or 90) go east/west. Auxiliary highways are numbered 100-999, and service the primary highway indicated by the rightmost two digits. Thus, I-405 services I-5, and I-290 services I-90.

Given a highway number, indicate whether it is a primary or auxiliary highway. If auxiliary, indicate what primary highway it serves. Also indicate if the (primary) highway runs north/south or east/west.

Ex: If the input is: 90
the output is: I-90 is primary, going east/west.

Ex: If the input is: 290
the output is: I-290 is auxiliary, serving I-90, going east/west.

Ex: If the input is: 0
or any number not between 1 and 999, the output is:
0 is not a valid interstate highway number. 
*/

import java.util.Scanner; 

public class LabProgram {
   public static void main(String[] args) {
      Scanner scnr = new Scanner(System.in); 
      int highwayNumber;
      int primaryNumber;
      int numInput;

      try {
         numInput = scnr.nextInt();
         primaryNumber = (numInput > 0 && numInput < 100) ? numInput : 0;
         highwayNumber = (numInput > 99 && numInput < 1000) ? numInput : 0;
         
         if (primaryNumber != 0) {
            if (primaryNumber % 2 == 0) {
               System.out.println("I-" + primaryNumber + " is primary, going east/west.");
            }
            else {
               System.out.println("I-" + primaryNumber + " is primary, going north/south.");
            }
         }
         
         if (highwayNumber != 0) {
            primaryNumber = highwayNumber % 100;
            if (highwayNumber % 2 == 0) {
               System.out.println("I-" + highwayNumber + " is auxiliary, serving I-" + primaryNumber + ", going east/west.");
            }
            else {
               System.out.println("I-" + highwayNumber + " is auxiliary, serving I-" + primaryNumber + ", going north/south.");
            }
         }
         
         if (primaryNumber == 0 && highwayNumber == 0) {
            System.out.println(numInput + " is not a valid interstate highway number.");
         }
      }
      catch (Exception e) {
         System.out.println("You did not enter an integer.");
      }
   }
}
```