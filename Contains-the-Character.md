---
title: LAB 4-27: Contains the Character
subtitle: CST-105
author: Brent L. Ricks
date: July 9, 2022
subject: Lab
---

# LAB 4-27: Contains the Character

```java
/*
Write a program that reads an integer, a list of words, and a character. The integer signifies how many words are in the list. The output of the program is every word in the list that contains the character at least once. For coding simplicity, follow each output word by a comma, even the last one. Assume at least one word in the list will contain the given character. Assume that the list of words will always contain fewer than 20 words.

Ex: If the input is: 4 hello zoo sleep drizzle z
then the output is: zoo,drizzle,

To achieve the above, first read the list into an array. Keep in mind that the character 'a' is not equal to the character 'A'.
*/

import java.util.Scanner;

public class LabProgram {
   public static void main(String[] args) {
      Scanner input = new Scanner(System.in);
      int wordCount = input.nextInt();
      String[] words = new String[wordCount];
      char selectedChar;
      
      for(int i = 0; i < wordCount; ++i) {
         words[i] = input.next();
      }
      
      selectedChar = input.next().charAt(0);
      
      for (String i: words) {
         if (i.indexOf(selectedChar) != -1) {
            System.out.print(i + ",");
         }
      }
   }
}
```

