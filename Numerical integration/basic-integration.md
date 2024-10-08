# Introduction
Integration is not always a straightforward operation in mathematics as we all know. There are some kind of functions such as 1/ln(x) for which it's impossible to find a single closed-form solution for its indefinite integral in terms of explicit functions.
That's why, we may need to use numerical analysis methods to develop programming algorithms that are supposed to calculate definite integrals of complicated functions sometimes. 

To approximate definite integral of a function, we can use a very simple notation as follows.

![image](https://github.com/user-attachments/assets/d4e03e6f-b9a8-4e27-95e8-8adb785727ed)
,

where "b" and "a" are points represent the interval in which we integrate the function, "Δx" is an infinitesimal which means that less Δx, more accurate result we have.

If you apply a limit as Δx goes to 0, you will have the classic expression of definite integral which means our notation is approximated for definite integrals.

![image](https://github.com/user-attachments/assets/8f6eed32-b335-404c-9fcf-2a2a002f51a4)






# Derivation of the Notation
Before we jump to coding practises, I want to give a basic derivation of this notation to make you grasp why this works (If you are already familiar with the Riemann sum, you may proceed to the section of code examples).
I'm not a real mathematician so don't expect me to write formal proof.
Consider a simple function such as log(x+1)
![image](https://github.com/user-attachments/assets/04a2b13f-5f7e-4b39-8411-c944c6f46ae4)

Let's say you want to find the value for area under curve.
You could do an approximation by drawing rectangles under curve and calculating their total areas like in the image.

![image](https://github.com/user-attachments/assets/2e82b346-87a3-4c3c-804c-ff315e8ee0bc)

You will realise that If you increase the number of rectangles, you will have more accurate results.

![image](https://github.com/user-attachments/assets/4b09d889-6955-48a1-a1ae-ce8528eb0fbe)

![image](https://github.com/user-attachments/assets/c690512b-16e0-4432-85a1-22c0bb97579e)

Denote Δx as horizontal length of each rectangle and denote "b" and "a" as the points on x-axis which are representing the interval in which we want to do integration.

![image](https://github.com/user-attachments/assets/0436177e-18ca-49ea-81c0-00acc36f1539)



This definitions mean that there are rectangles with number of approximately (b-a)/Δx that are forming the area we want to find.
So If you want to get first rectangle's area, It's "Δx * f(0 + 1 * Δx)"
If you want to get second rectangle's area, It's "Δx * f(0 + 2 * Δx)" and so on. By the way, if you are confused about zeros, it's because starting point of interval is 0 in our case. If it's any other number, you need to replace it. 
If you were to do it for all rectangles in an interval [a,b] you will get a notation with sigma sum which is already given in the Introduction part.

# Converting to Code
Let's say you have a simple function with a formula "x^2" and you want to integrate it between 0 and 3.
Easiest way to approximate definite integral of this function from 0 to 3 in Python:
```python
import math

#Function we want to integrate
def parabole(x):
	return x**2

def integrate(b,a,f,delta_x):
	end = (b-a)/delta_x
	temp = 0
	for p in range(0,math.floor(end)):
		temp = temp + (f(a+(p+1)*delta_x)*delta_x)
	return temp

print(integrate(3,0,parabole,0.000001)) #output: 9.000013500006666
```
delta_x must be very small just like in the code (0.000001) you can edit this to have a better approximation if it's vital for you.
If you increase the complexity of function or values, your task will take longer. So if you need to work with extremely big numbers, you may want to use a language like C, C++ rather than python since low-level languages are much faster than high-level ones such as Python.

This approach will approximate exact mathematical value so if you have a negative graph, you will have a negative value or if you're integrating a function whose graph lies both above and below the x-axis, you will have a subtracted value just like you do with real integrals.

So if you need to calculate areas regardless of their signs and if you want to integrate whole areas as positive. You need a minor edit in the code as follows.
```python
import math

#Function we want to integrate(we changed it to x^2 - 5 to demonstrate example of functions with negative values)
def parabole(x):
	return (x**2 - 5)

def integrate(b,a,f,delta_x):
	end = (b-a)/delta_x
	temp = 0
	for p in range(0,math.floor(end)):
		if 0>f(a+(p+1)*delta_x):
			temp = temp + ((-1)*f(a+(p+1)*delta_x)*delta_x)
			continue
		temp = temp + (f(a+(p+1)*delta_x)*delta_x)
	return temp

print(integrate(3,0,parabole,0.000001)) #output is 8.907123350004452 instead of -5.999991499993089
```
Code can be used even for really complicated integrals like notorious the Gamma function. See gamma-function.md file for code examples of approximation of the Gamma function. 

If you want to use a data set as a function graph and then integrate, you need very simple another code:
```python
#Example matrix n x 2 (n is 4 in this case)
matrix = [
    [1.3,4],
    [1.6,8],
    [2,10],
    [4.3,7.3]
]

def integrate(matx):
	temp = 0
	for x in range(1, len(matx)):
		horizontal=matx[x][0] - matx[x-1][0]
		base=matx[x][1]+matx[x-1][1]
		temp = temp+(base*horizontal)/2
	return "that's finale output: "+str(temp)

print(integrate(matrix))
```
First column of the matrix consists of ```x``` values in the graph while second column of the matrix consists of corresponding ```y``` values in the graph.



