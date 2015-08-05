---
layout: post
title: Prime Number
tags: C
---
###Return the first N primes in a pointer

The first part of this problem is asking the user for the number of primes he wants:

```c
int input() {
    int N;
    printf("Number of primes you want: \n");
    scanf("%d", &N);
    return N;
}
```

Pretty straightforward this part not much to it.   

Next we need a function to check if a number is prime or not:

```c
int prime(int x) {
    int i;
    if(x % 2 == 0)
        return 0;

    for (i = 3; i <= (int)sqrt(x); i+=2) {
        if (x % i == 0)
            return 0;
    }
    return 1;
}
```
The tricky part about this function is the way you think about it. It's fairly easy to see if a number is prime or not, I made the function this way to have speed on my side, by eliminating the possibility of even numbers, only iterating through the odd numbers and only going until the square root of the number.

So now we  are able to ask the user for the number of primes he wants and check if a number is prime, the only thing missing is the function that receives N and returns the pointer with all the primes in it:

```c
int *pointerOfPrimes(int N) {
    int *pointer;
    int j = 0;
    int i = 1;
    pointer = (int *) malloc(N * sizeof(int));

    while (j < N) {
        if (prime(i)) {
            pointer[j] = i;
            j++;
        }
        i++;
    }
    return pointer;
}

```

The var j counts the number of primes and i is the value for the possible prime number. Every time a prime i is discovered, we append(not sure if good choice of word) it to the pointer and increment j, this is made until N - 1.