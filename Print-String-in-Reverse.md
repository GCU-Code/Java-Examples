---
title: LAB 4-32: Print String in Reverse
subtitle: CST-105
author: Brent L. Ricks
date: July 9, 2022
subject: Lab
---

# LAB 4-32: Print String in Reverse

```java
/*
Write a program that takes in a line of text as input, and outputs that line of text in reverse. The program repeats, ending when the user enters "Done", "done", or "d" for the line of text.

Ex: If the input is: 
Hello there
Hey
done

the output is:
ereht olleH
yeH
*/

import java.util.Scanner;
import java.util.ArrayList;

public class LabProgram {
   public static void main(String[] args) {
      Scanner input = new Scanner(System.in);
      ArrayList<String> strList = new ArrayList<String>();
      String strOutput = "";
      boolean isComplete = true;
      
      while(isComplete) {
         String strCurrent = input.nextLine();
         if(strCurrent.equals("Done") || strCurrent.equals("done") || strCurrent.equals("d")) {
            isComplete = false;
         }
         else {      
            char[] charArray = strCurrent.toCharArray();
            for (int i = charArray.length - 1; i >= 0; i--){
               System.out.print(charArray[i]);
            }
            System.out.println();
         }
      }
   }
}
```

