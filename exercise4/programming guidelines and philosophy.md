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
<img src="http://chart.googleapis.com/chart?cht=tx&chl=x_{i+1}=x_i+v_{x,i}\Delta%20t" style="border:none;">
