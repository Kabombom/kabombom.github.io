---
layout: post
title: Matrix Multiplication
tags: Java
---
###Create a program that multiplies 2 rectangular matrices. This program needs to verify if the multiplication is valid.
Some notes first:                             
->Won't explain any Algebra in this post, search for yourself the rules of matrix multiplication;                                                                                                    
->With that said, I don't have Algebra in some months, so had to search google myself for this;       
->Yes, I'm a noob;     
->Started learning Java from a python and C background;       
->Lazyness during vacations made this problem look harder to me;     
->Yes, I tend to be lazy during the summer vacations. Who isn't?
              

Onwards to the interesting part!    
The method itself is quite big so I will not post the code in one go. I will add parts of code and explain them basically.   
The first part we have to see if the multiplication is valid:

```java
public static void multiply(int[][] matrice1, int[][] matrice2) {
    int nLin1 = matrice1.length;
    int nCol1 = matrice1[0].length;
    int nLin2 = matrice2.length;
    int nCol2 = matrice2[0].length;
    if (nCol1 != nLin2) {
        System.out.println("Multiplication is invalid");
        return;
    }
}
```

The names of the variables are pretty self explanatory, nLin is the number of rows and nCol the number of columns. 1 and 2 being matrice1 or matrice2 respectavelly.


Next, we're going to create the multiplication matrice and the counters that will allow to travel through both matrices:

```java
public static void multiply(int[][] matrice1, int[][] matrice2) {
    int nLin1 = matrice1.length;
    int nCol1 = matrice1[0].length;
    int nLin2 = matrice2.length;
    int nCol2 = matrice2[0].length;
    if (nCol1 != nLin2) {
        System.out.println("Multiplication is invalid");
        return;
    }
    int[][] multMatrice = new int[nLin1][nCol2];
    int counterl1 = 0;
    int counterc1 = 0;
    int counterc2 = 0;
    int sum = 0;
}
```

In the while loops you'll understand the purpose of each var.

Onto the multiplication itself:

```java
public static void multiply(int[][] matrice1, int[][] matrice2) {
    int nLin1 = matrice1.length;
    int nCol1 = matrice1[0].length;
    int nLin2 = matrice2.length;
    int nCol2 = matrice2[0].length;
    if (nCol1 != nLin2) {
        System.out.println("Multiplication is invalid");
        return;
    }
    int[][] multMatrice = new int[nLin1][nCol2];
    int counterl1 = 0;
    int counterc1 = 0;
    int counterc2 = 0;
    int sum = 0;
    while(counterl1 < nLin1) {
        while(counterc1 < nCol1) {
            sum += matrice1[counterl1][counterc1] * matrice2[counterc1] [counterc2];
            counterc1++;
        }
        multMatrice[counterl1][counterc2] = sum;
        sum = 0;
        counterc1 = 0;
        counterc2++;
        if (counterc2 == nCol2) {
            counterc2 = 0;
            counterl1++;
        }
    }
    print(multMatriz);
}
```

To understand better by example: 2 matrices both with the size [2][2] we need to multiply [0][0] with [0][0], then [0][1] with [1][0]. After this [1][0] with [0][1] and finnaly [1][1] with [1][1].        
The counter that travels through the numbers that are in each row of matrice1 is counterc1, this counter also travels through the numbers in each column of the matrice2.      
The first part of multiplication (row 0 with column 0) it's donne in the while inside the while where the result is stored in the var sum.      
After the while is donne, the first while continues and it appends the sum onto multMatrice.       
Then it resets sum and counterc1. Counterc2 (controls the column travel in matrice2) is incremented.
When counterc2 is equal to the number of columns in matrice2, it's reseted and counterl1 (controls the row travel in matrice1) is incremented.
This was my base idea for rectangular matrice multiplication, hope I was explicit enough for you to understand.



