# Problem 1.1

## Question
The velocity of a freely falling object near Earth's surface is described by the equation <br/>

<img src="http://latex.codecogs.com/gif.latex?\frac{dv}{dt}=-g" alt="" title="" /> <br/>       
Where _v_ is the velocity and _g_=9.8m/s<sup>2</sup> is the acceleration due to gravity. Write a program that employs the Euler method to compute the solution to the above equation; that is, calculate _v_ as a funtion of _t_. For simplicity, assume that the initial velocity is zero——that is, the object starts from rest——and calculate the solution for times _t_=0 to _t_=10 s. Repeat the calculation for several different values of the times step, and compare the results with the exact solution to the above equation. It turns out that for this case the Euler method gives the exact result. Verify this with your numerical results and prove it analytically. <br/>
## Analysis
Consider the equation given <br/>

<img src="http://latex.codecogs.com/gif.latex?\frac{dv}{dt}=-g" alt="" title="" /> <br/>
According to the definition of differential, we have <br/>

<img src="http://latex.codecogs.com/gif.latex?\frac{dv}{dt}=\frac{v(t+\Delta%20t)-v(t)}{\Delta%20t}" alt="" title="" /> <br/>
Combine the two equations, we can get <br/>

<img src="http://latex.codecogs.com/gif.latex?v(t+\Delta%20t)=v(t)-g\Delta%20t" alt="" title="" /> <br/>
So, we can calculate the velocity at any time once we know the velocity at \Delta t before.
## Code
```python
import numpy as np    
import pylab as pl    
g=9.8
v=[]
t=[]
v.append(0)
t.append(0)
dt=0.001#步长为0.001秒

for i in range (10000):
  vt=v[i]-g*dt
  tadd=t[i]+dt
  v.append(vt)
  t.append(tadd)#循环10000次，共10秒

t_max=t[-1]
v_max=v[-1]
pl.plot(t,v,'g')
pl.title('the v as a function of t')  
pl.xlabel('the time') 
pl.ylabel('the velocity')
pl.xlim(0.0,t_max)
pl.ylim(v_max,0.0)#取负g,故y轴取负半轴
pl.show()
```
## result
