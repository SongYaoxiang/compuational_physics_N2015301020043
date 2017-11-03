```python
import pylab as pl
x=[]
x1=[]
y=[]
y1=[]
y2=[]
y3=[]
x.append(0)
y.append(0)

x1.append(0)
y1.append(0)
y2.append(0)
y3.append(0)
dx=0.01
for i in range (100):
    x_1=x[i]+dx
    y_1=x_1
    y1_1=x_1*1.5*(1-x_1)
    y2_1=x_1*2*(1-x_1)
    y3_1=x_1*3*(1-x_1)
    x.append(x_1)
    y.append(y_1)
    y1.append(y1_1)
    y2.append(y2_1)
    y3.append(y3_1)

   
pl.plot(x,y,label=r'$y=x$')
pl.plot(x,y1,label=r'$y=1.5x(1-x)$')
pl.plot(x,y2,label=r'$y=2x(1-x)$')
pl.plot(x,y3,label=r'$y=3x(1-x)$')
pl.xlabel('x')
pl.ylabel('y')
pl.title('logistic map')
pl.legend(loc='best')
pl.ylim(0,1)
pl.show()    
```
