# Python

## 用python解高数作业
1、计算不定积分
>>> integrate(x**3/(x**4+x**2+2), x)
log(x**4 + x**2 + 2)/4 - sqrt(7)*atan(2*sqrt(7)*x**2/7 + sqrt(7)/7)/14

2、泰勒展开
>>> sin(x).series(x,0,6)
x - x**3/6 + x**5/120 + O(x**6)

## 用python解线代作业
1、求逆矩阵
>>> b = np.array([[8,6],[5,4]])
>>> np.linalg.inv(b)
array([[ 2. , -3. ],
       [-2.5,  4. ]])

2、求dot
>>> i = np.array([[1,2],[4,7]])
>>> np.dot(i,i)
array([[ 9, 16],
       [32, 57]])

>>> i = np.array([[1,2],[3,4]])
>>> j = np.array([[3,5],[2,8]])
>>> np.dot(i,j)
array([[ 7, 21],
       [17, 47]])