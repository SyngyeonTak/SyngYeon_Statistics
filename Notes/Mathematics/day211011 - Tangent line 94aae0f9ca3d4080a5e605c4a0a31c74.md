# day211011 - Tangent line

Wrong Definition: A tangent line to a curve is a line that touches the curve at only one point

Better Definition (But Wrong): A tangent line to a curve is a line that just touches the curve at only one point

→ it captures an idea that the line gradually approaches the curve and touches at only  one point

Better Definition (But Still wrong): A tangent line to a curve is a line that, **up close**, just touches the curve at only one point in a way that if you rotate the line even slightly, it will become a secant line and cross the curve at a second, nearby point...

It would be time-consuming to find the fitting definition...

So let's use calculus, precisely using a Limit

![Untitled](day211011%20-%20Tangent%20line%2094aae0f9ca3d4080a5e605c4a0a31c74/Untitled.png)

You can define the tangent line to A as the limit of the secant lines as P approaches 2, negative 3

1. The tangent line must touch the curve
2. Limit from the left = Limit from the right (ruling out a flatten graph)
3. Tangent Line = Best approximation by a line (Tangent line become from one another)

Derivative = Slope of Tangent Line

![Untitled](day211011%20-%20Tangent%20line%2094aae0f9ca3d4080a5e605c4a0a31c74/Untitled%201.png)

Alternative Definition for Tangent Line (Using Derivative)

The tangent line through a point A is the line that passes through A and whose slope is the derivative at A