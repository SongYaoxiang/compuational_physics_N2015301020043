``` python
import pylab as pl
pi=3.14
dt=0.001

x=[]
y=[]
vx=[]
vy=[]

x.append(1)
y.append(0)
vx.append(0)
vy.append(2*pi)

for i in range(1000):
    vx_1=vx[i]-4*pi*pi*x[i]*dt
    x_1=x[i]+vx_1*dt
    vy_1=vy[i]-4*pi*pi*y[i]*dt
    y_1=y[i]+vy_1*dt
    x.append(x_1)
    y.append(y_1)
    vx.append(vx_1)
    vy.append(vy_1)
    
    
pl.plot(x,y)
pl.xlabel('x(AU)')
pl.ylabel('y(AU)')
pl.title('earth orbiting the sun')
pl.show()  
```
