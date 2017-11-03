``` python
import pylab as pl
n=[]
n1=[]
x=[]
x1=[]
n.append(1)
x.append(0.4)
n1.append(1)
x1.append(0.4)
u=2
u1=3.1
for i in range (50):
    x_1=x[i]*u*(1-x[i])
    x.append(x_1)
    n.append(n[i]+1)
for i in range (50):
    x1_1=x1[i]*u1*(1-x1[i])
    x1.append(x1_1)
    n1.append(n1[i]+1)
pl.plot(n,x,'y.-',label=r'$\mu$=2')
pl.plot(n1,x1,'g.-',label=r'$\mu$=3.1')
pl.legend(loc='best')
pl.ylim(0,1)
pl.xlabel('n')
pl.ylabel('x')
pl.title('logistic map')
pl.show()    
  ```  
