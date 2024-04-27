# The Exponential Growth Problem
Imagine you had a colony of bacteria that lives in an ideal environment.  In this ideal environment, the bacteria have virtually unlimited food and space to grow.

![image](https://github.com/tomeng70/LittleLamb/assets/12796159/7a31187d-b532-4c8b-9800-4442517adb0f)


In this scenario, the rate at which the population size of the colony changes is directly proportional to the size of the population itself.
The more bacteria you have, the faster the population will grow.

This rate equation for population growth can be expressed as follows,

$\frac{dN}{dt} = r \cdot N$

In this equation, $N$ represents the population size, $t$ represents time, and the variable $r$ is a constant value know as the <i>rate of growth</i> of the population.

An analytical solution for this rate equation can be obtained using calculus. Using algebra, you can rearrange the terms so you get the following equation,

$\frac{dN}{N} = r \cdot dt$

You can integrate this equation to solve for $N$ in terms of $t$.

$\int{\frac{dN}{N}} = \int{ r \cdot dt }$

$ln(N) = r \cdot t + C$

where the variable $C$ represents a constant value.  This equation can be rewritten in the following form,

$N = N_0 \cdot e^{r \cdot t}$



