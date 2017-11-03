```python
import pylab as pl
n=[]

x=[]

n.append(1)
x.append(0.4)

u=3.8


for i in range (50):
    x_1=x[i]*u*(1-x[i])
    x.append(x_1)
    n.append(n[i]+1)

pl.plot(n,x,'b.-',label=r'$\mu$=3.8')
pl.xlabel('n')
pl.ylabel('x')
pl.title('logistic map')
pl.legend(loc='best')
pl.ylim(0,1)
pl.show()    
```
