It's quite possible to approximate the integral of the Gamma function with the notation we provided in "basic-integration" section.

That's because

![image](https://github.com/user-attachments/assets/92d96b9d-abc9-435d-8e91-cf868fc9d396)


and

![image](https://github.com/user-attachments/assets/b700b915-6afc-41c4-93b1-126f4d10571b)






If you have no idea about what's that sigma notation for or what's meaning of that delta x. Please first see basic-integration.md file 

# Converting to Code
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

print(integrate(100,0,gamma,0.000001)) #output: 362879.9999749526 (real value: 362880 which is only 0.0001 higher than approximated value)
```
If you write the program in C++ you can have better approximations in significantly short time.

```c
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
