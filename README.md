# The MTwister C Library

The **Mersenne twister** is a pseudo-random number generation
algorithm that was [developed in 1997 by Makoto Matsumoto (松本 眞) and
Takuji Nishimura (西村 拓
士)](http://www.math.sci.hiroshima-u.ac.jp/~m-mat/MT/emt.html).
Although [improvements on the original algorithm have since been
made](http://www.math.sci.hiroshima-u.ac.jp/~m-mat/MT/SFMT/index.html),
the original algorithm is still both faster and "more random" than the
built-in generators in many common programming languages (C and Java
included).

There are already many implementations of the algorithm, so why did I
write one myself?  There are a number of reasons:

1. the [pseudocode on Wikipedia](http://en.wikipedia.org/wiki/Mersenne_twister#Pseudocode) suggested that it was relatively simple to implement;
2. I never trust pseudocode on Wikipedia, so I wanted an implementation from [the original academic paper](http://www.math.sci.hiroshima-u.ac.jp/~m-mat/MT/ARTICLES/mt.pdf); and
3. it would have been just as easy to implement it myself than to figure out the API of someone else's ugly C code.

Note that this code has not been tested to a sufficient extent to be
confidently used for cryptography.

# Example

The following code will create a new random generator seeded at <code>1337</code> and print out one thousand random doubles between 0 and 1.

```C
#include <stdio.h>
#include "mtwister.h"

int main() {
  MTRand r = seedRand(1337);
  int i;
  for(i=0; i<1000; i++) {
    printf("%f\n", genRand(&r));
  }
  return 0;
}
```

# License

Public domain.  Have fun!