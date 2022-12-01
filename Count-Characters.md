---
title: LAB 4-30: Count Characters
subtitle: CST-105
author: Brent L. Ricks
date: July 9, 2022
subject: Lab
---

# LAB 4-30: Count Characters

```java
/*
Write a program whose input is a character and a string, and whose output indicates the number of times the character appears in the string. The output should include the input character and use the plural form, n's, if the number of times the characters appears is not exactly 1.

Ex: If the input is: n Monday
the output is: 1 n

Ex: If the input is: z Today is Monday
the output is: 0 z's

Ex: If the input is: n It's a sunny day
the output is: 2 n's

Case matters.

Ex: If the input is: n Nobody
the output is: 0 n's

n is different than N.
*/

import java.util.Scanner;
import java.util.ArrayList;

public class LabProgram {
   public static void main(String[] args) {
      Scanner input = new Scanner(System.in);
      ArrayList<String> inputArray = new ArrayList<String>();
      String selectedChar = input.next();
      int charCount = 0;
      
      while (input.hasNext()) {
         inputArray.add(input.next());
      }
      
      for (String str: inputArray) {
         for (int c = 0; c < str.length(); ++c) {
            char currentChar = str.charAt(c);
            char originalChar = selectedChar.charAt(0);
            if (currentChar == originalChar) {
               ++charCount;
            }
         }
      }
      
      if (charCount == 0 || charCount > 1) {
         System.out.println(charCount + " " + selectedChar +"'s");
      }
      else {
         System.out.println(charCount + " " + selectedChar);
      }
   }
}
```

