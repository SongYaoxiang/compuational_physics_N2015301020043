```python
import pylab as pl
import math
pi=3.14
dt=0.001
kjs=0.8
kes=0.000003

xe=[]
ye=[]
vex=[]
vey=[]
re=[]
xj=[]
yj=[]
vjx=[]
vjy=[]
rj=[]
rej=[]

xe.append(1)
ye.append(0)
vex.append(0)
vey.append(2*pi)
re.append(1)

xj.append(5)
yj.append(0)
vjx.append(0)
vjy.append(2.8)
rj.append(5)
rej.append(4)

for i in range(100000):
    
    
    vex_1=vex[i]-4*pi*pi*xe[i]*dt/re[i]**3-4*pi*pi*kjs*(xe[i]-xj[i])*dt/rej[i]**3
    vey_1=vey[i]-4*pi*pi*ye[i]*dt/re[i]**3-4*pi*pi*kjs*(ye[i]-yj[i])*dt/rej[i]**3
    
    vjx_1=vjx[i]-4*pi*pi*xj[i]*dt/rj[i]**3-4*pi*pi*kes*(xj[i]-xe[i])*dt/rej[i]**3
    vjy_1=vjy[i]-4*pi*pi*yj[i]*dt/rj[i]**3-4*pi*pi*kes*(yj[i]-ye[i])*dt/rej[i]**3
    
    xe_1=xe[i]+vex_1*dt
    ye_1=ye[i]+vey_1*dt
    xj_1=xj[i]+vjx_1*dt
    yj_1=yj[i]+vjy_1*dt
    
    re_1=math.sqrt(xe_1**2+ye_1**2)
    rj_1=math.sqrt(xj_1**2+yj_1**2)
    rej_1=math.sqrt((xe_1-xj_1)**2+(ye_1-yj_1)**2)
    
    re.append(re_1)
    rj.append(rj_1)
    rej.append(rej_1)
    vex.append(vex_1)
    vey.append(vey_1)
    vjx.append(vjx_1)
    vjy.append(vjy_1)
    xe.append(xe_1)
    ye.append(ye_1)
    xj.append(xj_1)
    yj.append(yj_1)
    
pl.plot(xe,ye)
pl.plot(xj,yj)
pl.xlabel('x(AU)')
pl.ylabel('y(AU)')
pl.title('3-body simulation Earth plus Jupiter')
pl.xlim(-6,6)
pl.ylim(-6,6)
pl.show()  
