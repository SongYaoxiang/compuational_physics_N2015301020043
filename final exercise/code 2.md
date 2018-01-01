```python
import math, random, pylab

class Location:
    def __init__(self,x,y):  #定义醉汉的位置，即平面上的一点，用x和y坐标表示
        self.x=x
        self.y=y
    def move(self,xc,yc):  #输入x和y坐标的变动值，返回变动后的坐标
        return Location(self.x+xc,self.y+yc)
    def getLocation(self):
        return self.x,self.y
    def getDistance(self,other):  #输入另一个点的坐标，根据x轴和y轴变动的距离，算出原点和另一个点之间的直线距离
        ox,oy=other.getLocation()
        xDist=ox-self.x
        yDist=oy-self.y
        return math.sqrt(xDist**2+yDist**2)

class Direction:
    possibleDirection=("S","W","E","N")  #可能的四种方向
    def __init__(self,direc):  #定义方向，如果此方向不在可能的四种方向里面，那么报错
        if direc in self.possibleDirection:
            self.direc=direc
        else:
            raise ValueError("in direction:__init__")
    def move(self,dist):  #输入移动距离，根据不同的方向返回平面距离
        if self.direc=="S": return (0,-dist)
        if self.direc=="W": return (-dist,0)
        if self.direc=="E": return (dist,0)
        if self.direc=="N": return (0,dist)
        else: raise ValueError("in direction: move")

class Field:
    def __init__(self,drunk,loc):  #定义醉汉和其所在的平面
        self.drunk=drunk
        self.loc=loc
    def move(self,direc,dist):  #输入方向和移动距离，获得x和y坐标的变动值，在原点上移动该值，获得变动后的坐标
        oldLoc=self.loc
        xc,yc=direc.move(dist)
        self.loc=oldLoc.move(xc,yc)
    def getLocation(self):
        return self.loc
    def getDrunk(self):
        return self.drunk

class Drunk:
    def __init__(self,name):
        self.name=name
    def move(self,field,step=1):
        if field.getDrunk()!=self:
            raise ValueError("No such drunk is found on the field")
        for i in range(step):
            direc=Direction(random.choice(Direction.possibleDirection))
            field.move(direc,1)

def performTrial(step,f):
    startLoc=f.getLocation()
    distances=[0]
    for t in range(1,step+1):
        f.getDrunk().move(f)
        newLoc=f.getLocation()
        distance=newLoc.getDistance(startLoc)
        distances.append(distance)
    return distances

drunk=Drunk("Baichi")
for i in range(3):
    f=Field(drunk,Location(0,0))
    distances=performTrial(5000,f)
    pylab.plot(distances)
pylab.title("Random Walk")
pylab.xlabel("steps(=time)")
pylab.ylabel("Distance")
pylab.show()
