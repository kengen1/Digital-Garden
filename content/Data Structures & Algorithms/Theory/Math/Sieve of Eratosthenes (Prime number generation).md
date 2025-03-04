
*An efficient method to find all primes smaller than or equal to n (given n is smaller than 10 million)*

---

**What is a prime number?**: *a natural number that is greater than 1 and has exactly two distinct divisors: 1 and itself*

**Key properties of Prime Numbers:**:
- the smallest prime number is 2 (it is the only even prime)
- any even prime number greater than 2 is composite
- all composite numbers can be factored into smaller primes

---


```cpp
void SieveOfEratosthenes(int n)
{
    // Create a boolean array "prime[0..n]" and initialize
    // all entries it as true. A value in prime[i] will
    // finally be false if i is Not a prime, else true.
    vector<bool> prime(n + 1, true);

  for (int p = 2; p * p <= n; p++) {

        if (prime[p] == true) {
            
            // Update all multiples of p greater than or
            // equal to the square of it numbers which are
            // multiple of p and are less than p^2 are
            // already been marked.
            for (int i = p * p; i <= n; i += p)
                prime[i] = false;
        }
    }

    // Print all prime numbers
    for (int p = 2; p <= n; p++)
        if (prime[p])
            cout << p << " ";
}
```