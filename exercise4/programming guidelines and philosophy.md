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

