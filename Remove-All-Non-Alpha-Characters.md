---
title: LAB 4-31: Remove All Non-Alpha Characters
subtitle: CST-105
author: Brent L. Ricks
date: July 9, 2022
subject: Lab
---

# LAB 4-31: Remove All Non-Alpha Characters

```java
/*
Write a program that removes all non alpha characters from the given input.

Ex: If the input is: -Hello, 1 world$!
the output is: Helloworld
*/

import java.util.Scanner;
import java.util.ArrayList;

public class LabProgram {
   public static void main(String[] args) {
      Scanner input = new Scanner(System.in);
      ArrayList<String> strArray = new ArrayList<String>();
      String str = "";
      
      while(input.hasNext()) {
         strArray.add(input.next());
      }
      
      for (String s: strArray) {
         str = str += s;
      }
      
      str = str.replaceAll("([^a-zA-Z])", "");
      System.out.println(str);
   }
}
```

