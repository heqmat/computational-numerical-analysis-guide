Arc length is the distance between two points along a section of a curve. Altough there are formulas for calculating exact arc length of a curve, in most cases, including even simple curves, there are no closed-form solutions for arc length and numerical integration is necessary. Numerical integration of the arc length integral is usually very efficient.

A notation for approximating arc length integral as follows.

![image](https://github.com/user-attachments/assets/ab84e843-bedb-4632-84c7-9febdafc9add)


where the "b" value on the x-axis here represents the maximum value in the range in which the curve length will be calculated, the "a" value represents the smallest value in the range. In other words, this notation tries to approximate the curve length between "b" and "a" on the x-axis. Δx represents the infinitesimal horizontal length of the infinitesimal linear lines that form the curve. So with a smaller Δx we have a better approximation.

If a limit is applied where Δx approaches 0, this notation above is equivalent to classical formula of arc length.

![equation (6)](https://github.com/user-attachments/assets/1e862390-007a-4fa2-abac-974511af3a99)






It would be nice to point out that classical arc length integral formula still works, but it is incredibly difficult, sometimes even impossible, to apply this formula to some functions.
Therefore, we should consider using the approximating notation above.

# Derivation of the Arc Length Notation (why it works)
A curve on a plane can be closely represented by linking a limited set of points along the curve with straight line segments, forming a polygonal path.
So using a progressively larger number of line segments of smaller lengths will result in better curve length approximations just like we approximate integral of a function by limits with Riemann sum (If you need to simply calculate definite integrals, please see the "basic-integration.md" file in the same folder).

![image](https://github.com/user-attachments/assets/b8ea9b8a-c52e-4cef-b41a-27951cf72182)

If you try to resolve random line segment that forms the curve into its components, you will have something like this:

![image](https://github.com/user-attachments/assets/248e22c9-816b-4a83-87e2-3d9ad5e3ffd6)

Therefore we have:

![image](https://github.com/user-attachments/assets/3364facc-21aa-4e0c-a5c4-c5ff4fbcf218)


Don't forget that it doesn't have to be positive as we're considering any line segment. Nevertheless, we will consider it positive since length cannot have negative sign.
Now remember we're in search of a notation, so we will need an expression in which all these lines are summed.

We know that the horizontal component length of each line segment is Δx while the vertical component length of each line segment that is represented by Δy changes depending on the progress on the x-axis by each Δx. For example, while the first vertical component length of the line segment is f(a + Δx * 1)-f(a + Δx * 0), the length of the vertical component of the second line segment is f(a + Δx * 2) - f(a + Δx * 1), so the difference between the factors of Δx will be 1. is constantly increasing. If we represent this with the sigma sum symbol, we encounter the first notation. I didn't include many mathematical expressions while proving how this works, however, it's quite difficult to make such a explanation as derivation of the notation is more about visual analysis.

# Converting to Code
Let's say you have an explicit function with a formula "x^2" and you want to find the curve length between the [1,3] interval.
```python
import math

def parabole(x):
	return (x**2)

def arclength(b,a,f,delta_x):
	end = (b-a)/delta_x
	temp = 0
	for p in range(0,math.floor(end)):
		temp = temp + math.sqrt(delta_x**2+(f(a+delta_x*(p+1))-f(a+delta_x*p))**2)
	return temp

print(arclength(3,1,parabole,0.000001)) 
```
Output is pretty impressive.

Calculated with exact arc length formula:     8.26814590106 

Calculated with numerical integration method: 8.26814590106416
