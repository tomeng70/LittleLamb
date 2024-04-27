# The Exponential Growth Problem
Imagine you had a colony of bacteria that lives in an ideal environment.  In this ideal environment, the bacteria have virtually unlimited food and space to grow.

<p align="center">
  <img  src="https://github.com/tomeng70/LittleLamb/assets/12796159/7a31187d-b532-4c8b-9800-4442517adb0f">  
</p>

In this scenario, the rate at which the population size of the colony changes is directly proportional to the size of the population itself.
The more bacteria you have, the faster the population will grow.

This rate equation for population growth can be expressed as follows,

<p align="center">
  $\dfrac{dN}{dt} = r \cdot N$
</p>

In this equation, $N$ represents the population size, $t$ represents time, and the variable $r$ is a constant value know as the <i>rate of growth</i> of the population.

## An Exact Solution
An analytical solution for this rate equation can be obtained using calculus. Using algebra, you can rearrange the terms so you get the following equation,

<p align="center">
  $\dfrac{dN}{N} = r \cdot dt$
</p>

You can integrate this equation to solve for $N$ in terms of $t$.

<p align="center">
  $\int{\dfrac{dN}{N}} = \int{ r \cdot dt }$
</p>

Which gives us the following equation,  
<p align="center">
  $ln(N) = r \cdot t + C$
</p>

where the variable $C$ represents a constant value.  This equation can be rewritten in the following form,

<p align="center">
  $N = N_0 \cdot e^{rt}$
</p>

This equation is an exact solution for the population size, $N$, as a function of time, $t$. $N_0$ is the initial population size at time $t = 0$.  If you know the value of your rate of growth, $r$, and the initial population size, $N_0$, then you can calculate the population size at any time $t$.

## A Simple Numerical Solution
Some rate problems are not as tractable as this example problem and do not have an analytical solution. If a rate equation does not have a clean analytical solution, a numerical method can often be used instead to approximate a solution for the equation. A numerically derived solution, which often requires the power of a digital computer to generate the solution, can be useful when solving various scientific, engineering, or business-related problems.

The exponential growth rate equation can be used to demonstrate how a numerical or computational solution can be used to calculate an approximate solution for a differential equation.

Imagine we have a bacterial colony that has a growth rate of $r$ and an initial population size of $N_0$ (at time $t = t_0$).  Suppose we wanted to estimate the size of the colony at some later time, where $t = t_1$.  

We can use our rate equation (which tells us what the slope of our solution is at time $t$) and the previous population size to estimate the size at time $t = t_1$:


<p align="center">
  $N(t_1) = N(t_0) + (t_1 - t_0) \cdot \dfrac{dN}{dt}$ 
</p>

If we use the variable $\Delta t$ for the expression $(t_1 - t_0)$, we get the following equation

<p align="center">
  $N(t_1) = N(t_0) + \Delta t \cdot \dfrac{dN}{dt}$ 
</p>

We can substitute our rate equation in place of $\frac{dN}{dt}$ to estimate the slope of the population curve at time $t_1$:

<p align="center">
  $N(t_1) = N(t_0) + \Delta t \cdot r \cdot N(t_1)$ 
</p>

Note that the numerical method that we are using to solve for $N(t_1)$ is an _implicit_ method, since in order to solve for $N(t_1)$ we have to solve an equation that involves both $N(t_1)$ and the previous value $N(t_0)$. Solving this implicit equation for $N(t_1)$ we get the following equation,

<p align="center">
  $N(t_1) = \dfrac{N(t_0)} {1 -  r \cdot \Delta t}$ 
</p>

This equation gives us an approximate value of $N$ at time $t = t_1$ in terms of $N$ at time $t = t_0$.  We can then use our estimate of $N(t_1)$ to solve for $N(t_2)$ and continue this process iteratively to generate an estimate of the population size as a function of time.

Our generic equation looks like the following,

<p align="center">
  $N(t_{i+1}) = \dfrac{N(t_i)} {1 -  r \cdot h}$ 
</p>

Note that by convention, the variable $h$ is used in place of $\Delta t$.  The variable $h$ is referred to as the _time step_. 

A computer program can use this equation to generate an array of values that represent the estimated population size at sequential, discrete instances in time.

## Runge Kutta Fourth Order Method
The previous numerical method is considered to be an _implicit method_ because in order to solve for the value of our population function at the current time, we have to solve an equation that involves both the previous value of the population function as well as the current value of the population function.  

The Runge-Kutta methods are a set of popular _explicit_ numerical methods that generate estimated values of a function at the current time based on the values of the function at a previous time.  The Runge-Kutta 4th order (RK4) method is a popular numerical method that is used to solve ordinary differential equations.

Take a look at the following equation,

<p align="center">
  $N(t_{i+1}) = N(t_i) + \Delta t \cdot \dfrac{dN}{dt} = N(t_i) + \Delta t \cdot r \cdot N(t_i)$
</p>

In this equation above, we multiply the slope of our population function, $\dfrac{dN}{dt}$ by the size of our time step, $\Delta t$, to estimate how much our population will change from time $t = t_i$ to time $t = t_{i+1}$.  We add this change in population to our previous population value, $N(t_i)$ and the result is an estimate for the population value, $N(t_{i+1}$.  

This simplified approach is a version of the Runge-Kutta method (also known as Euler's method) that uses the first derivative of the population function as the _rate equation_ for the problem.  

The Runge-Kutta family of methods attempt to model the _rate equation_ that is used to estimate the change in a function like our population function more accurately:

<p align="center">
  $N(t_{i+1}) = N(t_i) + h \cdot f(N(t_i), t_i)$
</p>

In the equation above, the variable $h$ represents our time step, and the function $f(N(t_i), t_i)$ is our rate equation that is evaluated when the population is equal to $N(t_i)$ and the time is equal to $t_i$.  


