```python
import pylab as pl
t=[]
x=[]
y=[]
z=[]

sigma=10
b=8/3
dt=0.0001
r=25

r2=470/19
x.append(1)
y.append(0)
z.append(0)


t.append(0)
for i in range (500000):
    t_1=t[i]+dt
    x_1=x[i]+sigma*(y[i]-x[i])*dt
    y_1=y[i]-x[i]*z[i]*dt+r*x[i]*dt-y[i]*dt
    z_1=z[i]+x[i]*y[i]*dt-b*z[i]*dt
    x.append(x_1)
    y.append(y_1) 
    z.append(z_1)
   
   
    t.append(t_1)  
    
pl.plot(x,z,label='r=25')


pl.legend(loc='best')

pl.xlabel('x')
pl.ylabel('z')
pl.title('lorenz model  z versus x')
pl.show()
```
