```python
import pylab as pl
t=[]
x=[]
x1=[]
z1=[]
y=[]
z=[]
x2=[]
x12=[]
z12=[]
y2=[]
z2=[]

sigma=10
b=8/3
dt=0.0001
r=25

r2=470/19
x.append(1)
y.append(0)
z.append(0)
x1.append(1)
z1.append(0)

x2.append(0)
y2.append(1)
z2.append(1)
x12.append(0)
z12.append(1)


t.append(0)
for i in range (5000000):
    
    x_1=x[i]+sigma*(y[i]-x[i])*dt
    y_1=y[i]-x[i]*z[i]*dt+r*x[i]*dt-y[i]*dt
    z_1=z[i]+x[i]*y[i]*dt-b*z[i]*dt
    x.append(x_1)
    y.append(y_1) 
    z.append(z_1)
    if abs(y[i])<0.0001:
        x1.append(x[i])
        z1.append(z[i])
    else:
        pass
for i in range (5000000):
    
    x2_1=x2[i]+sigma*(y2[i]-x2[i])*dt
    y2_1=y2[i]-x2[i]*z2[i]*dt+r*x2[i]*dt-y2[i]*dt
    z2_1=z2[i]+x2[i]*y2[i]*dt-b*z2[i]*dt
    x2.append(x2_1)
    y2.append(y2_1) 
    z2.append(z2_1)
    if abs(y2[i])<0.0001:
        x12.append(x2[i])
        z12.append(z2[i])
    else:
        pass
   
   
    
pl.plot(x1,z1,'.',label='r=25,x=1,y=z=0')
pl.plot(x12,z12,'.',label='r=25,x=0,y=z=1')

pl.legend(loc='best')

pl.xlabel('x')
pl.ylabel('z')
pl.title('lorenz model  z versus x when y=0')
pl.show()

```
