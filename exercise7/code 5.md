```python
import pylab as pl
t=[]
x=[]
y=[]
z=[]
x1=[]
y1=[]
z1=[]

sigma=10
b=8/3
dt=0.0001
r=10
r1=22
r2=470/19
x.append(1)
y.append(0)
z.append(0)
x1.append(1)
y1.append(0)
z1.append(0)

t.append(0)
for i in range (500000):
    t_1=t[i]+dt
    x_1=x[i]+sigma*(y[i]-x[i])*dt
    y_1=y[i]-x[i]*z[i]*dt+r*x[i]*dt-y[i]*dt
    z_1=z[i]+x[i]*y[i]*dt-b*z[i]*dt
    x.append(x_1)
    y.append(y_1) 
    z.append(z_1)
    x1_1=x1[i]+sigma*(y1[i]-x1[i])*dt
    y1_1=y1[i]-x1[i]*z1[i]*dt+r1*x1[i]*dt-y1[i]*dt
    z1_1=z1[i]+x1[i]*y1[i]*dt-b*z1[i]*dt  
    x1.append(x1_1)
    y1.append(y1_1)
    z1.append(z1_1)
   
    t.append(t_1)  
    
pl.plot(x,z,label='r=10')
pl.plot(x1,z1,label='r=22')

pl.legend(loc='best')

pl.xlabel('x')
pl.ylabel('z')
pl.title('lorenz model  z versus x')
pl.show()```
