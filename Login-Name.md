---
title: LAB 4-29: Login Name
subtitle: CST-105
author: Brent L. Ricks
date: July 9, 2022
subject: Lab
---

# LAB 4-29: Login Name

```java
/*
Write a program that creates a login name for a user, given the user's first name, last name, and a four-digit integer as input. Output the login name, which is made up of the first five letters of the last name, followed by the first letter of the first name, and then the last two digits of the number (use the % operator). If the last name has less than five letters, then use all letters of the last name.

Ex: If the input is: Michael Jordan 1991
the output is: Your login name: JordaM91

Ex: If the input is: Kanye West 2024
the output is: Your login name: WestK24
*/

import java.util.Scanner;

public class LabProgram {

	public static void main(String[] args) {
	   Scanner input = new Scanner(System.in);
	   String[] userInput = new String[3];
	   String str1 = "";
	   String str2 = "";
	   int str3 = 0;
	   
	   for (int i = 0; i < userInput.length; ++i) {
	      userInput[i] = input.next();
	   }
	   
	   str1 = userInput[1];
	   if (str1.length() < 5) 
	      str1 = str1.substring(0, str1.length());
	   else 
	      str1 = str1.substring(0, 5);
	   str2 = userInput[0].substring(0, 1);
	   str3 = Integer.parseInt(userInput[2]);
	   str3 = str3 % 100;

		System.out.println("Your login name: " + str1 + str2 + str3);

	}
}
```

