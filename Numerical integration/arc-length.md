Arc length is the distance between two points along a section of a curve. Altough there are formulas for calculating exact arc length of a curve, in most cases, including even simple curves, there are no closed-form solutions for arc length and numerical integration is necessary. Numerical integration of the arc length integral is usually very efficient.

Classical notation for approximating arc length integral as follows.

![image](https://github.com/user-attachments/assets/dff12850-133a-458a-8c3f-48f91fcd9992)

where Δx is an infinitesimal value, "b" value is greater than 0 on the x-axis and is the end point of the range from which we will calculate the arc length. So If you replace "b" with 3 and replace Δx with extremely
small number such as 1 x 10^-5 you will get a very good approximation for length of curve of f(x) function in the range between 0 and 3. If you need to find curve length in a range between "a" and "b" values, you will need to approximate each arc length and get the difference between them by using same Δx value for better approximations.

# Derivation of the Arc Length Notation (why it works)
A curve on a plane can be closely represented by linking a limited set of points along the curve with straight line segments, forming a polygonal path.
So using a progressively larger number of line segments of smaller lengths will result in better curve length approximations just like we approximate integral of a function by limits with Riemann sum (If you need to simply calculate definite integrals, please see the "basic-integration.md" file in the same folder).
