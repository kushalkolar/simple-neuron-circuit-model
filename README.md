# simple-neuron-circuit-model
A really simple 3 neuron circuit model that I made in 2013 during my undergrad

# Background

The model combines the Goldberg equation and the equations that describe the decay of membrane potential along the length of an axon due to membrane capacitance etc. (forgot if those have a name?)

Goldberg equation:

<img src="https://render.githubusercontent.com/render/math?math=E_{m} = \frac{RT}{F} \ln{ \left( \frac{ \sum_{i}^{n} P_{M^{+}_{i}}[M^{+}_{i}]_\mathrm{out} + \sum_{j}^{m} P_{A^{-}_{j}}[A^{-}_{j}]_\mathrm{in}}{ \sum_{i}^{n} P_{M^{+}_{i}}[M^{+}_{i}]_\mathrm{in} + \sum_{j}^{m} P_{A^{-}_{j}}[A^{-}_{j}]_\mathrm{out}} \right) }">

Membrane potential decay over distance:

<img src="https://render.githubusercontent.com/render/math?math=V(x) = V_{max}(e^{-x/C})">

Membrane potential decay over time:

<img src="https://render.githubusercontent.com/render/math?math=V(t) = V_{max}(e^{-t/T})">

# Implementation

At ti Find out if neuron is stimulated
  - Stimulation causes change in PNa and PK
    - Find Em-source with the Goldman Equation

Quantify dynamics of the Em at the axon hillock
  - This Em-source decays over distance, find the Em at the Axon hillock which is at a distance x from the source of stimulation.
  - At the Axon hillock, Em-hillock decays over time. Therefore keep track of Em-hillock at ti and find how much it has decayed from ti-1. Then add the “new” Em which has decayed over distance x from the source
  
![equation](https://latex.codecogs.com/gif.latex?E_%7Bhillock%20t_%7Bi%7D%7D%20%3D%20E_%7Bhillock%20t_%7Bi%7D%20-%201%7D*e%5E%7B1/T%7D%20&plus;%20E_%7Bm-source%7D*e%5E%7B-x/L%7D)

If Em-hillock > threshold, fire

# Examples

![image](https://user-images.githubusercontent.com/9403332/126059755-29356fe5-072c-4f79-be98-fe2353089edf.png)

![image](https://user-images.githubusercontent.com/9403332/126059781-76675705-6046-4670-bcdf-e25b8de80561.png)
