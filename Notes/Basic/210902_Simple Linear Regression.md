# Statistics_day210902=7

With only one variable, and no other information, the best prediction for the next measurement is the mean of the sample itself. The variability on y-axis can only be explained by the given dependent values themselves.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ced34b24-cd19-4c42-82a0-70fe13597bae/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a940048c-2fb8-44d2-a5eb-5f22e8e14908/Untitled.png)

The goal of simple linear regression is to create a linear model that minimizes the sum of squares of the residuals / error (SSE)

If our regression model is significant, it will "eat up" much of the raw SSE we had when we assumed (like this problem) that the independent variable did not even exist. The regression line will/should literally "fit" the data better. It will minimize the residuals.

When conducting simple linear regression with TWO variables, we will determine how good that line "fits" the data by comparing it to THIS TYPE; where we pretend the second variable does not even exist.

If a two-variable regression model looks like this example, what does the other variable do to help explain the dependent variable? → Nothing

### Review

Simple linear regression is really a comparison of two models

- One is where the independent variable does not even exist
- And the other uses the best fit regression line

If there is only one variable, the best prediction for other values is the mean of the "dependent" variable

The difference between the best-fit line and the observed value is called the residual (or error)

The residuals are squared and then added together to generate sum of squares (Litterally) residuals / error, SSE

Simple linear regression is designed to find the best fitting line through the data that minimizes the SSE