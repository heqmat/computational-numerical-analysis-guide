It's quite possible to approximate the integral of the Gamma function with the notation we provided in "basic-integration" section.

That's because

![image](https://github.com/user-attachments/assets/7d2790f7-b841-4d9e-8ac9-f239e3c3bc82)

and

![image](https://github.com/user-attachments/assets/58d47c04-b077-474f-8a9b-2d8e2f6986a0)

If you have no idea about what's that sigma notation for or what's meaning of that delta x. Please first see basic-integration.md file 

Let's assume you want to find Γ(10) which is actually 9!
```python
import math

z=10
#Function we want to integrate
def gamma(x):
	return (x**(z-1))*math.e**(-x)

def integrate(b,a,f,delta_x):
	end = (b-a)/delta_x
	temp = 0
	for p in range(0,math.floor(end)):
		temp = temp + (gamma(a+(p+1)*delta_x)*delta_x)
	return temp

print(integrate(100,0,gamma,0.000001)) #output: 362879.9999749526 (real value: 362880)
```
If you write the program in C++ you can have better approximations in significantly short time.

```cpp
#include <iostream>
#include <cmath>

double z = 10;

// Function we want to integrate
double gamma(double x) {
    return pow(x, z - 1) * exp(-x);
}

double integrate(double b, double a, double (*f)(double), double delta_x) {
    double end = (b - a) / delta_x;
    double temp = 0.0;
    for (int p = 0; p < static_cast<int>(floor(end)); p++) {
        temp += f(a + (p + 1) * delta_x) * delta_x;
    }
    return temp;
}

int main() {
    std::cout << integrate(500, 0, gamma, 0.000001) << std::endl; // output: 3.6288e+05 (same as real value)
    return 0;
}
```
