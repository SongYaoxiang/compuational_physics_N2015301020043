```python
import pylab as pl
t=[]
x=[]
x1=[]
z1=[]
y=[]
z=[]

sigma=10
b=8/3
dt=0.0001
r=25

r2=470/19
x.append(0)
y.append(1)
z.append(1)
x1.append(0)
z1.append(1)


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
   
   
    
pl.plot(x1,z1,'.',label='r=25')


pl.legend(loc='best')

pl.xlabel('x')
pl.ylabel('z')
pl.title('lorenz model  z versus x when y=0')
pl.show()


```
