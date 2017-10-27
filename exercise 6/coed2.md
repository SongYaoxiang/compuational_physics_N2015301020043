```python
import pylab as pl
import math
l=1
g=9.8
dt=0.01
dt1=0.02
dt2=0.03
theta=[]
theta1=[]
theta2=[]
w=[]
w1=[]
w2=[]
time=[]
time1=[]
time2=[]
theta.append(0.5)
theta1.append(0.5)
theta2.append(0.5)
w.append(0)
time.append(0)
time1.append(0)
time2.append(0)
w1.append(0)
w2.append(0)

for i in range (1000):
    w_1=w[i]-(g/l)*theta[i]*dt
    w.append(w_1)
    theta_1=theta[i]+w[i+1]*dt
    time_1=time[i]+dt
    theta.append(theta_1)
    time.append(time_1)
    
    w_11=w1[i]-(g/l)*theta1[i]*dt1
    w1.append(w_11)
    theta_11=theta1[i]+w1[i+1]*dt1
    time_11=time1[i]+dt1
    theta1.append(theta_11)
    time1.append(time_11)
    
    w_12=w2[i]-(g/l)*theta2[i]*dt2
    w2.append(w_12)
    theta_12=theta2[i]+w2[i+1]*dt2
    time_12=time2[i]+dt2 
    theta2.append(theta_12)
    time2.append(time_12)
    
pl.plot(time,theta,'g', label="dt=0.01")
pl.plot(time1,theta1,'r',label="dt=0.02")
pl.plot(time2,theta2,'b',label="dt=0.03")
pl.xlim(0,10)
pl.ylim(-3,3)
pl.xlabel('x time(s)')
pl.ylabel('y theta(rad)')
title('Euler-cromer method')
legend(loc='upper left')

pl.show()
```
