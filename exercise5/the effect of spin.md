# Problem 2.18
 #### 宋尧祥  2015301020043
# question
Calculate the effect of backspin on a fastball. How much does an angular velocity of 1000 rpm (typical for fastball) affect the trajectory?
# 计算
当不考虑风的影响时的影响时，根据欧拉法可得下列方程 <br/>

<img src="http://latex.codecogs.com/gif.latex?x_{i+1}=x_i+v_{x,i}\Delta%20t" alt="" title="" /> <br/>
<img src="http://latex.codecogs.com/gif.latex?v_{x,i+1}=v_{x,i}-B_2vv_{x,i}}{m}\Delta%20t" alt="" title="" /> <br/>
<img src="http://latex.codecogs.com/gif.latex?y_{i+1}=y_i+v_{y,i}\Delta%20t" alt="" title="" /> <br/>
<img src="http://latex.codecogs.com/gif.latex?v_{y,i+1}=v_{y,i}-g\Delta%20t-B_2vv_{y,i}}{m}\Delta%20t" alt="" title="" /> <br/>
根据教材figure2.6
结果表明B<sub>2</sub>/m满足关系式：      
<img src="http://latex.codecogs.com/gif.latex?\frac{B_2}{m}=0.0039+\frac{0.0058}{1+exp((v-v_d)/\Delta)}" alt="" title="" /> <br/>
其中,v_d=35m/s,\Delta=5m/s,一个优秀棒球运动员击出的球速为49m/s，因此可计算出B<sub>2</sub>/m值为4.23*10<sup>-3</sup>m<sup>-1</sup>  
当我们不考虑球的自旋时，可得到如下y和x的轨迹  
![result](https://github.com/SongYaoxiang/compuational_physics_N2015301020043/blob/master/exercise5/Figure_1.png)  
当考虑棒球自旋时  
![result](https://github.com/SongYaoxiang/compuational_physics_N2015301020043/blob/master/exercise5/%E6%95%99%E6%9D%90%E5%9B%BE.png)  
由于上下面的速度不同，导致空气对其作用力也不同，所以最终产生一个向上的合力，于是根据欧拉法可得到如下方程：  

<img src="http://latex.codecogs.com/gif.latex?x_{i+1}=x_i+v_{x,i}\Delta%20t" alt="" title="" /> <br/>
<img src="http://latex.codecogs.com/gif.latex?v_{x,i+1}=v_{x,i}-\frac{B_2vv_{x,i}}{m}\Delta%20t" alt="" title="" /> <br/>
<img src="http://latex.codecogs.com/gif.latex?y_{i+1}=y_{i}+v_{y,i}\Delta%20t" alt="" title="" /> <br/>
<img src="http://latex.codecogs.com/gif.latex?v_{y,i+1}=v_{y,i}-g\Delta%20t" alt="" title="" /> <br/>
<img src="http://latex.codecogs.com/gif.latex?z_{i+1}=z_{i}+v_{z,i}\Delta%20t" alt="" title="" /> <br/>
<img src="http://latex.codecogs.com/gif.latex?v_{z,i+1}=v_{z,i}-\frac{S_0wv_{x,i}}{m}\Delta%20t" alt="" title="" /> <br/>
上面式子中S<sub>0</sub>/m=4.1*10<sup>-4</sup>，w=1000rpm=104.72rad/s，可得到如下图像：  
![result](https://github.com/SongYaoxiang/compuational_physics_N2015301020043/blob/master/exercise5/spin.png)
# 结论
当考虑风阻以及棒球自身旋转时，会使球产生偏转，而球的转速以及旋转方向等均会对球的弧线轨迹产生影响。
#### 另外，特别感谢梁旭同学，此次的三维坐标坐标系代码参考于梁旭同学





