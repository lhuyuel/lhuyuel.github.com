---
layout: post
title: "Prime Number Problems"
description: ""
category: Algorithm
tags: [Algorithm]
---
{% include JB/setup %}
Basically, there are problems like these:
+ Given a number N, test if it is a prime number
+ Print out prime numbers that are less than N
+ Print out the first N prime number

###Problem 1: Primality Test
For the first problem, the trial division test could imediately come up to our mind:
####1.Trial division
This is based on the definition of a prime number:
	A number is prime if it has no divisors other than itself and one.
Devide the number by 1 to ¡ÌN, if the all remainning != 0, then it is a prime number. Else, it's not.

Notice that if a number cannot be divided by 2 then it cannot be dived by 2x. So we only need to check if N can be diveded by prime numbers. To do this, use an array to store primeNumberList will help. It will cost a litte more space. We are exchanging time with space.

####2.Fermat's little theorem
According to Fermat's little theorem(http://en.wikipedia.org/wiki/Fermat%27s_little_theorem)

{% highlight cpp linenos %}
unsigned Montgomery(unsigned n, unsigned p, unsigned m)
{ // 
    unsigned r = n % m; // 
    unsigned k = 1;
    while (p > 1)
    {
        if ((p & 1)!=0)
        {
            k = (k * r) % m;
        }
        r = (r * r) % m;
        p /= 2;
    }
    return (r * k) % m; 
}

bool IsPrimeFermat(unsigned n)
{
    if ( n < 2 )
    {
        return false;
    }
    static unsigned aPrimeList[] = {
        2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41,
        43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97
    };
    const int nListNum = sizeof(aPrimeList) / sizeof(unsigned);
    for (int i=0;i<nListNum;++i)
    { 
        if (1!=Montgomery(aPrimeList[i],n-1,n))
        {
            return false;
        }
    }
    return true;
}
{% endhighlight %}

Optimized Montgomery algorithm code:
{% highlight cpp linenos %}
unsigned Montgomery(unsigned n,unsigned p,unsigned m)
{
      unsigned k=1;
      n%=m;
     while(p!=1)
     {
         if(0!=(p&1))k=(k*n)%m;
         n=(n*n)%m;
         p>>=1;
    }
    return(n*k)%m;
}
{% endhighlight %}


	Note: Technically, Fermat's test is a test for compositeness, rather than for primeness. This is because, if the test fails, the number is certainly composite, but if the test passes, the number is very likely prime, but might possibly be a composite pseudoprime.	
	
####3.Miller-Rabin primality test
http://en.wikipedia.org/wiki/Miller_rabin
The Miller-Rabin test works similarly to Fermat's but handles pathological cases like the Carmichael numbers better.
{% highlight cpp linenos %}
bool RabbinMillerTest( unsigned n ) 
{
    if (n<2)
    { 
        return false;
    }

    const unsigned nPrimeListSize=sizeof(g_aPrimeList)/sizeof(unsigned);
    for(int i=0;i<nPrimeListSize;++i)
    {
        if (n/2+1<=g_aPrimeList[i])
        {
            return true;
        }
        if (0==n%g_aPrimeList[i])
        {
            return false;
        }
    }
  
    int r = 0, m = n - 1; 
    while ( 0 == ( m & 1 ) )
    {
        m >>= 1; 
        r++; 
    }
    const unsigned nTestCnt = 8; 
    for ( unsigned i = 0; i < nTestCnt; ++i )
    { 
        int a = g_aPrimeList[ rand() % nPrimeListSize ];
        if ( 1 != Montgomery( a, m, n ) )
        {
            int j = 0;
            int e = 1;
            for ( ; j < r; ++j )
            {
                if ( n - 1 == Montgomery( a, m * e, n ) ) 
                {
                    break;
                }
                e <<= 1;
            }
            if (j == r)
            {
                return false;
            }
        }
    }
    return true;
}
{% endhighlight %}

###Problem 2: Print Primes Numbers Less Than N
A straight forward solution is: for each number, start from 0 to N, test if it is a prime number using the algorithms above.
	
We could also use *Sieve of Eratosthenes* method.
####Sieve of Eratosthenes
http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes

###Problem 3: Print the First N Prime Numbers
If we could get the range of the Nth number, this problem is similar to *Problem 2*.
By applying *Prime number theorem*, we could estimate the upper bound of the Nth number.

```
	PN ~ Nln(N)
```

To make sure the Nth number is less than the estimated number, I multiply Nln(N) by 1.5.   
