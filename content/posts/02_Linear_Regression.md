---
title: "Linear Regression"
date: "2021-05-08"
weight: 1
tags: ["Machine Learning", "Linear Regression"]
categories: ["Data Science", "Machine Learning"]
---


Regression is a method of modelling a target value based on independent predictors. This method is mostly used for forecasting and finding out **cause and effect relationship between variables**. Regression techniques mostly differ based on the number of independent variables and the type of relationship between the independent and dependent variables. Regression problems usually have one continuous and unbounded dependent variable. The inputs, however, can be continuous, discrete, or even categorical data such as gender, nationality, brand, and so on.

<div align="center">
<img src="/posts/images/2_Regression.SVG" width=500px/>
</div>

<br>

## **Linear Regression**

Linear regression with multiple variables is also known as "**multivariate linear regression**". The multivariable form of the hypothesis function accommodating these multiple features is as follows:

{{< katex display=true >}}
\begin{align*}
&\mathrm{Hypothesis}: h_{\theta}(x) = \theta_{0} + \theta_{1}x_{1} + \theta_{2}x_{2} + \theta_{3}x_{3} + \cdot\cdot\cdot + \theta_{n}x_{n} \\
&\mathrm{Cost \ Function}: J(\theta) = \frac{1}{2m}\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})^2 \\
&\mathrm{Goal}: \min_{\theta}J(\theta) \\
\end{align*}
{{< /katex >}}

Using the definition of matrix multiplication, our multivariable hypothesis function can be concisely represented as:

{{< katex display=true >}}
 h_{\theta}(x) =
\begin{bmatrix}
\theta_{0} & \theta_{1} & \cdot\cdot\cdot & \theta_{n}
\end{bmatrix}
\begin{bmatrix}
x_{0} \\
x_{1} \\
\cdot\cdot\cdot \\
x_{n}
\end{bmatrix}
= \theta^{T}x \\
{{< /katex >}}

### **Gradient Descent for Linear Regression**

Gradient descent is a generic optimization algorithm used in many machine learning algorithms. It iteratively tweaks the parameters of the model in order to minimize the cost function. We do this is by taking the **derivative** (the tangential line to a function) of our cost function. The slope of the tangent is the derivative at that point and it will give us a direction to move towards. We make steps down the cost function in the direction with the steepest descent. The size of each step is determined by the parameter **{{< katex >}}\alpha{{< /katex >}}**, which is called the **learning rate**. The **gradient descent algorithm** can be represented as:

{{< katex display=true >}}
\begin{align*}  
&\frac{\partial J(\theta)}{\partial \theta_{0}}= \frac{1}{m}\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)}) \\
&\frac{\partial J(\theta)}{\partial \theta_{j}}= \frac{1}{m}\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})x_{j}^{(i)} \\
\end{align*}
{{< /katex >}}

{{< katex display=true >}}
\begin{bmatrix}
\frac{\partial J(\theta)}{\partial \theta_{0}} \\
\frac{\partial J(\theta)}{\partial \theta_{1}} \\
\cdot\cdot\cdot \\
\frac{\partial J(\theta)}{\partial \theta_{n}}
\end{bmatrix}=\frac{1}{m}x^{T}(h_{\theta}(x)-y) \\
{{< /katex >}}

{{< katex display=true >}}
\begin{bmatrix}
\theta_{0} \\
\theta_{1} \\
\cdot\cdot\cdot \\
\theta_{n}
\end{bmatrix}=\begin{bmatrix}
\theta_{0} \\
\theta_{1} \\
\cdot\cdot\cdot \\
\theta_{n}
\end{bmatrix}-\alpha\begin{bmatrix}
\frac{\partial J(\theta)}{\partial \theta_{0}} \\
\frac{\partial J(\theta)}{\partial \theta_{1}} \\
\cdot\cdot\cdot \\
\frac{\partial J(\theta)}{\partial \theta_{n}}
\end{bmatrix} \\
{{< /katex >}}

{{< katex display=true >}}
\begin{align*}  
&\mathrm{Repect\ until \ convergence} \{ \\
&\ \ \ \ \theta_{j}^{new} :=\theta_{j}^{old} - \alpha\frac{1}{m}\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})x_{j}^{(i)}) \ \ \ \ \mathrm{for} \ j = 0 \cdot\cdot\cdot n \\
&\} \\
\end{align*}
{{< /katex >}}

To demonstrate the gradient descent algorithm, we initialize the model parameters with 0. The equation becomes {{< katex >}}h_{\theta}(x) = 0{{< /katex >}}. Gradient descent algorithm now tries to update the value of the parameters so that we arrive at the best fit line.

We should adjust our parameter {{< katex >}}\alpha{{< /katex >}} to ensure that the gradient descent algorithm converges in a reasonable time. **If {{< katex >}}\alpha{{< /katex >}} is too small**, gradient descent can be slow. **If {{< katex >}}\alpha{{< /katex >}} is too large**, gradient descent can overshoot the minimum. It may fail to converge, or even diverge. Failure to converge or too much time to obtain the minimum value imply that our step size is wrong.

<div align="center">
<img src="/posts/images/2_Gradient_Descent.PNG" width=400px/>
</div>

We can **speed up gradient descent** by having each of our input values in roughly the same range. This is because {{< katex >}}\theta{{< /katex >}} will descend quickly on small ranges and slowly on large ranges, and so will oscillate inefficiently down to the optimum when the variables are very uneven.

Two techniques to help with this are feature scaling and mean normalization. **Feature scaling** involves dividing the input values by the range (i.e. the maximum value minus the minimum value) of the input variable, resulting in a new range of just 1. **Mean normalization** involves subtracting the average value for an input variable from the values for that input variable resulting in a new average value for the input variable of just zero. To implement both of these techniques, adjust your input values as shown in this formula:

{{< katex display=true >}}
x_{i} := \frac{(x_{i}-\mu_{i})}{s_{i}} \\
{{< /katex >}}

Where {{< katex >}}\mu_{i}{{< /katex >}} is the average of all the values for feature (i) and {{< katex >}}s_{i}{{< /katex >}} is the range of values (max - min), or {{< katex >}}s_{i}{{< /katex >}} is the standard deviation. Note that dividing by the range, or dividing by the standard deviation, give different results.

### **Normal Equation for Linear Regression**

Gradient descent gives one way of minimizing J. In the "**Normal Equation**" method, we will minimize J by explicitly taking its derivatives with respect to the {{< katex >}}\theta_{j}{{< /katex >}} ’s, and setting them to zero. This allows us to find the optimum theta without iteration. The normal equation formula is given below:


{{< katex display=true >}}
\theta = (X^{T}X)^{-1}X^{T}y \\
{{< /katex >}}

The following is a comparison of gradient descent and the normal equation:

| **Gradient Descent**      | **Normal Equation** |
| :-------------------------------------------- | :-------------------------------------------- |
| Need to choose alpha            | No need to choose alpha       |
| Needs many iterations   | No need to iterate        |
| {{< katex >}}O(kn^{2}){{< /katex >}}      | {{< katex >}}O(n^{3}){{< /katex >}}, need to calculate inverse of {{< katex >}}X^{T}X{{< /katex >}}       |
| Works well when n is large     | Slow if n is very large       |

With the normal equation, computing the inversion has complexity {{< katex >}}O(n^{3}){{< /katex >}}. So if we have a very large number of features, the normal equation will be **slow**. In practice, when n exceeds 10,000 it might be a good time to go from a normal solution to an iterative process.

If {{< katex >}}X^{T}X{{< /katex >}} is **noninvertible**, the common causes might be having :
* Redundant features, where two features are very closely related (i.e. they are linearly dependent)
* Too many features (e.g. {{< katex >}}m ≤ n{{< /katex >}}). In this case, delete some features or use "regularization".

Solutions to the above problems include deleting a feature that is linearly dependent with another or deleting one or more features when there are too many features.

### **Evaluating the performance of the Linear Regression Model**

We will be using **Root mean squared error(RMSE)** and **Coefficient of Determination(R² score)** to evaluate our model. RMSE is the square root of the average of the sum of the squares of residuals. RMSE is defined by:

{{< katex display=true >}}
RMSE = \sqrt{\frac{1}{m}\sum_{i=1}^{m}(h(x^{(i)})-y^{(i)})^2} \\
{{< /katex >}}

{{< katex >}}R^{2}{{< /katex >}} score or the coefficient of determination explains how much the total variance of the dependent variable can be reduced by using the least square regression. It can be defined by:

{{< katex display=true >}}
R^{2} = 1- \frac{SS_{r}}{SS{t}} \\
{{< /katex >}}

Where {{< katex >}}SS_{t}{{< /katex >}} is the total sum of errors if we take the mean of the observed values as the predicted value and {{< katex >}}SS_{r}{{< /katex >}} is the sum of the square of residuals.

{{< katex display=true >}}
\begin{align*}
SS_{t} &= \sum_{i=1}^{m}(y^{(i)}-\bar{y})^2 \\
SS_{r} &= \sum_{i=1}^{m}(h(x^{(i)})-y^{(i)})^2 \\
\end{align*}
{{< /katex >}}

<br>

## **References**

[1]  Agarwal, A. (2018, November 14). Linear Regression using Python. Medium. https://towardsdatascience.com/linear-regression-using-python-b136c91bf0a2.

[2]  Ng, A. (n.d.). Machine Learning. Coursera. https://www.coursera.org/learn/machine-learning.

<br>
<div align="center">
{{<button relref="/posts/">}}Blog{{</button>}}
{{<button relref="/">}}Home{{</button>}}
</div>
