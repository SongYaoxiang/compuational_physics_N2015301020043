```python
import pylab as pl
import math
pi=3.14
dt=0.001
e=0.99

x=[]
y=[]
vx=[]
vy=[]
r=[]

x.append(1)
y.append(0)
vx.append(0)
vy.append(2*pi)
r.append(1)

for i in range(3000):
    vx_1=vx[i]-4*pi*pi*x[i]*dt/r[i]**3
    x_1=x[i]+vx_1*dt
    vy_1=vy[i]-4*pi*pi*y[i]*dt
    y_1=y[i]+vy_1*dt
    r_1=1/(1-e*x[i]/math.sqrt(x[i]**2+y[i]*y[i]))
    x.append(x_1)
    y.append(y_1)
    
    vx.append(vx_1)
    vy.append(vy_1)
    r.append(r_1)
    
    
pl.plot(x,y)
pl.xlabel('x(AU)')
pl.ylabel('y(AU)')
pl.title('simulation of elliptical orbit e=0.99')
pl.show()  
```
