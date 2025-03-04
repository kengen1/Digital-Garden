
*The GCD (Greatest Common Divisor) **or** HCF (Highest Common Factor) of two numbers is the largest number that exactly divides both numbers

**Example**:

```
input: 
	a = 12
	b = 16

output: 4
explanation: 4 is the largest number which is divisible by both 12 and 16
```

We can find the GCD of two numbers in C++
- uses **Euclidean Algorithm** 
- `gcd(a,b) = gcd(b, a mod b)`
- Time Complexity: `O(log n)` as at each step we reduce the problem space by a factor of at least 2. 

``` cpp
// call this in cpp for practical use
gcd(a, b)

// under the hood implementation
int gcd(int a, int b) {
	while(b != 0) {
		int temp = b;
		b = a % b;
		a = temp;
	}
	return a;
}
```
