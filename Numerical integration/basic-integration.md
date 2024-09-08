# Introduction
Integration is not always straight forward operation in mathematics as we all know. There are some kind of functions such as 1/ln(x) for which it's impossible to find a single closed-form solution for its indefinite integral due to its non-continuous nature or something else.
That's why, we may need to use approximated notations to develop programming algorithms that are supposed to calculate definite integrals of complicated functions sometimes. 

To approximate definite integral of a function, we can use a very simple notation as follows.

![image](https://github.com/user-attachments/assets/34fe212e-e931-4248-85fe-6342e1e46f25) ,

where "b" is the point on x-axis to which we want to integrate between b and 0, "Δx" is an infinitesimal which means that less Δx, more accurate result we have.

If you apply a limit with which Δx goes to 0, you will have the classic expression of definite integral which means our notation is approximated for definite integrals.

![image](https://github.com/user-attachments/assets/8b9a9d56-08f8-4ec1-b96a-da57b42a98a8)


# Derivation of the Notation
Before we jump to coding practises, I want to give a basic derivation of this notation to make you grasp why this works (you might want to skip this part If you're already familiar with the Riemann sum).

Consider a simple function such as log(x+1)
![image](https://github.com/user-attachments/assets/04a2b13f-5f7e-4b39-8411-c944c6f46ae4)

Let's say you want to find the value for area under curve.
You could do an approximation by drawing rectangles under curve and calculating their total areas like in the image.

![image](https://github.com/user-attachments/assets/2e82b346-87a3-4c3c-804c-ff315e8ee0bc)

You will realise that If you increase the number of rectangles, you will have more accurate results.

![image](https://github.com/user-attachments/assets/4b09d889-6955-48a1-a1ae-ce8528eb0fbe)

![image](https://github.com/user-attachments/assets/c690512b-16e0-4432-85a1-22c0bb97579e)

Denote Δx as horizontal length of each rectangle and denote "b" as point on x-axis to which we want to integrate just like this.
![image](https://github.com/user-attachments/assets/cd08c2ec-d6a5-475a-82ee-8f47d9640629)


This definitions mean that there are rectangles with number of approximately b/Δx that are part of the area we want to find.
So If you want to get first rectangle's area, It's "Δx * f(1 * Δx)"
If you want to get second rectangle's area, It's "Δx * f(2 * Δx)" and so on.
If you were to do it for all rectangles in a range between 0 and "b" you will get a notation with sigma sum which is already given in the Introduction part.

# Converting to Code
Easiest way to calculate definite integral of a function from 0 to b
```python
import math

#Function we want to integrate
def parabole(x):
	return x**2

def integrate(b,f,r):
	end = (b)/r
	temp = 0
	for p in range(0,math.floor(end)+1):
		temp = temp + (f((p+1)*r)*r)
	return temp

print(integrate(3,parabole,0.000001)) #output: 9.000013500006666
```





