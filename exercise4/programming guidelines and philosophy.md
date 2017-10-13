# Promblem 2.9

## Question
Calculate the trajectory of our cannon shell including both air drag and the reduced air density at high altitude so that you can reproduce the results in Figure 2.5. Perform your calculation for different firing angles and determine the value of the angle that gives the maximum range.
## analysis
According to Newton's second law, the equations can be written as <br/>
<img src="http://chart.googleapis.com/chart?cht=tx&chl=\frac{d^{2}x}{dt^{2}}=0" style="border:none;"> <br/>
<img src="http://chart.googleapis.com/chart?cht=tx&chl=\frac{d^{2}y}{dt^{2}}=-g" style="border:none;"> <br/>
Write each of these second-order equations as two first order equations  <br/>
<img src="http://chart.googleapis.com/chart?cht=tx&chl=\frac{dx}{dt}}=v_x" style="border:none;"> <br/> 
<img src="http://chart.googleapis.com/chart?cht=tx&chl=\frac{dy}{dt}}=v_y" style="border:none;"> <br/>
<img src="http://chart.googleapis.com/chart?cht=tx&chl=\frac{dv_x}{dt}}=0" style="border:none;"> <br/>
<img src="http://chart.googleapis.com/chart?cht=tx&chl=\frac{dv_y}{dt}}=-g" style="border:none;"> <br/>
To use Euler method,we can write each derivative in finite difference form, which leads to <br/>
<img src="http://latex.codecogs.com/gif.latex?x_{i+1}=x_i+v_{x,i}\Delta%20t" alt="" title="" /> <br/>
<img src="http://latex.codecogs.com/gif.latex?v_{x,i+1}=v_{x,i}" alt="" title="" /> <br/>
<img src="http://latex.codecogs.com/gif.latex?y_{i+1}=y_i+v_{x,i}\Delta%20t" alt="" title="" /> <br/>
<img src="http://latex.codecogs.com/gif.latex?v_{y,i+1}=v_{y,i}-g\Delta%20t" alt="" title="" /> <br/>
As the drag force on cannon shell is given by <br/>
<img src="http://latex.codecogs.com/gif.latex?F_{drag}=-B_2v^{2}" alt="" title="" /> <br/>
Think about the reduced air density at high altitude,the equation is given  <br/>
<img src="http://chart.googleapis.com/chart?cht=tx&chl=F_{drag}^{*}=(1-\frac{ay}{T_0})^{\alpha}F_{drag}(y=0)" style="border:none;"> <br/>
Where <img src="http://latex.codecogs.com/gif.latex?v=\sqrt{x^{2}+y^{2}}" alt="" title="" /> so we can have <br/> We can get <br/>
<img src="http://latex.codecogs.com/gif.latex?F_{drag,x}=-(1-\frac{ay}{T_0})^{\alpha}B_2vv_{x}" alt="" title="" /> <br/>
<img src="http://latex.codecogs.com/gif.latex?F_{drag,y}=-(1-\frac{ay}{T_0})^{\alpha}B_2vv_{y}" alt="" title="" /> <br/>
Add the force to the equations of motion leads to <br/>
<img src="http://latex.codecogs.com/gif.latex?x_{i+1}=x_i+v_{x,i}\Delta%20t" alt="" title="" /> <br/>
<img src="http://latex.codecogs.com/gif.latex?v_{x,i+1}=v_{x,i}-\frac{(1-\frac{ay}{T_0})^{\alpha}B_2vv_{x,i}}{m}\Delta%20t" alt="" title="" /> <br/>
<img src="http://latex.codecogs.com/gif.latex?y_{i+1}=y_i+v_{y,i}\Delta%20t" alt="" title="" /> <br/>
<img src="http://latex.codecogs.com/gif.latex?v_{y,i+1}=v_{y,i}-g\Delta%20t-\frac{(1-\frac{ay}{T_0})^{\alpha}B_2vv_{y,i}}{m}\Delta%20t" alt="" title="" /> <br/>
## code
### 有无空气阻力对比
```prthon
from math import *
from pylab import *

x=[0]
y=[0]
x1=[0]
y1=[0]
vx=[500]
vy=[500]
vx1=[500]
vy1=[500]
g=9.8
b2m=4e-5
a=6.5e-3
t=100000
dt=0.1
T_0=288

for i in range(int(t/dt)):
	c=sqrt(vx1[i]**2+vy1[i]**2)
	p=(2.71828)**(-(y1[i]*0.00001))
	f=b2m*c**2*p*(1-a*y1[i]/T_0)**2.5
	theta_x=vx1[i]/c
	theta_y=vy1[i]/c
	v_x1=vx1[i]-f*theta_x*dt
	v_y1=vy1[i]-f*theta_y*dt-g*dt
	vx1.append(v_x1)
	vy1.append(v_y1)
	temp_x1=x1[i]+vx1[i]*dt
	temp_y1=y1[i]+vy1[i]*dt
	if y1[i]>=0:
		x1.append(temp_x1)
		y1.append(temp_y1)
	else:
		break
plot(x1,y1,color='r',label="Air drag with altitude")

for i in range(int(t/dt)):
	v_x=vx[i]
	v_y=vy[i]-g*dt
	vx.append(v_x)
	vy.append(v_y)
	temp_x=x[i]+vx[i]*dt
	temp_y=y[i]+vy[i]*dt
	if y[i]>=0:
		x.append(temp_x)
		y.append(temp_y)
	else:
		break
plot(x,y,color='y',label="No air drag")

title('Cannon shell trajectory')
xlabel('x(m)')
ylabel('y(m)')
legend(loc='upper right')
show()
```
![result](https://github.com/SongYaoxiang/compuational_physics_N2015301020043/blob/master/exercise4/Figure_1.png)

### 不同角度对比
```python
from math import *
from pylab import *

g=9.8
dt=0.1
t=100000
b2m=4e-5
a=6.5e-3

def cannon(vx,vy):
	x=[0.]
	y=[0.]
	for i in range(int(t/dt)):
		c=sqrt(vx[i]**2+vy[i]**2)
		p=2.71828**(-(y[i])*0.00001)
		f=b2m*c**2*p*(1-a*y[i]/288)**2.5
		theta_x=vx[i]/c
		theta_y=vy[i]/c
		v_x=vx[i]-f*theta_x*dt
		v_y=vy[i]-g*dt-f*theta_y*dt
		vx.append(v_x)
		vy.append(v_y)
		x_temp=x[i]+vx[i]*dt
		y_temp=y[i]+vy[i]*dt
		if y[i]>=0:
			x.append(x_temp)
			y.append(y_temp)
		else:
			break
	plot(x,y)

for j in [30,35,40,45,50,55,60,70,75]:
	theta=j*3.1415926/180
	vx=[1000*cos(theta)]
	vy=[1000*sin(theta)]
	cannon(vx,vy)
title('Cannon shell trajectory')
xlabel('x(m)')
ylabel('y(m)')
plot()
show()
```
![result](https://github.com/SongYaoxiang/compuational_physics_N2015301020043/blob/master/exercise4/Figure_2.png)
