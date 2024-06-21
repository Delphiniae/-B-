# Assignment #2: 编程练习

Updated 0953 GMT+8 Feb 24, 2024

2024 spring, Complied by 张羽扬 数学科学学院



**说明：**

1）The complete process to learn DSA from scratch can be broken into 4 parts:
- Learn about Time and Space complexities
- Learn the basics of individual Data Structures
- Learn the basics of Algorithms
- Practice Problems on DSA

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）课程网站是Canvas平台, https://pku.instructure.com, 学校通知3月1日导入选课名单后启用。**作业写好后，保留在自己手中，待3月1日提交。**

提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



**编程环境**

操作系统：Windows 11 家庭中文版 22H2

Python编程环境：Spyder IDE 5.2.2, PyCharm 2023.1.4 (Professional Edition)

C/C++编程环境：无



## 1. 题目

### 27653: Fraction类

http://cs101.openjudge.cn/2024sp_routine/27653/



思路：



##### 代码

```python
def gcd(m,n):
    while m%n!=0:
        c=n
        n=m%n
        m=c
    return n
class fraction:
    def __init__(self,num,deno):
        self.num=num
        self.deno=deno
        if self.deno<0:
            self.deno=-self.deno
            self.num=-self.num
        if gcd(self.deno, self.num)>1:
            self.deno=self.deno//gcd(self.deno, self.num)
            self.num=self.num//gcd(self.deno, self.num)
    def __str__(self):
        return(str(self.num)+'/'+str(self.deno))
    def __add__(self,otherfraction):
        a=self.deno*otherfraction.num+self.num*otherfraction.deno
        b=self.deno*otherfraction.deno
        return fraction(a,b)
a,b,c,d=[int(i) for i in input().split()]
x=fraction(a,b)
y=fraction(c,d)
z=x+y
print(z)
```



代码运行截图 ![image-20240302134644908](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240302134644908.png)





### 04110: 圣诞老人的礼物-Santa Clau’s Gifts

greedy/dp, http://cs101.openjudge.cn/practice/04110



思路：不停把最贵的糖果往袋里装直到袋子装满或者糖果装完为止



##### 代码

```python
n,w=[int(i) for i in input().split()]
a=[]
b=[]
c=[]
u=0
for i in range(n):
    x,y=[int(i) for i in input().split()]
    a.append(x)
    b.append(y)
    c.append(x/y)
k=c.index(max(c))
while w>=b[k] and max(c)!=0:
    c[k]=0
    w=w-b[k]
    u=u+a[k]
    k=c.index(max(c))
u=u+w*max(c)
print(format(u,'.1f'))
```



代码运行截图![image-20240302134907544](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240302134907544.png)





### 18182: 打怪兽

implementation/sortings/data structures, http://cs101.openjudge.cn/practice/18182/



思路：将时间排序，每个时间对应的伤害用字典表示并排序



##### 代码

```python
cases=int(input())
for i in range(cases):
    n,m,b=[int(i) for i in input().split()]
    D={}
    T=set()
    for i in range(n):
        t,x=[int(i) for i in input().split()]
        d=D.get(t,0)
        if d==0:
            D[t]=[x]
        else:
            D[t].append(x)
        T.add(t)
    T=list(T)
    T.sort()
    for t in T:
        if len(D[t])<=m:
            b=b-sum(D[t])
        else:
            D[t].sort(reverse=True)
            s=0
            for i in range(m):
                s+=D[t][i]
            b=b-s
        if b<=0:
            print(t)
            break
    else:
        print('alive')
```



代码运行截图 

![image-20240302230057938](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240302230057938.png)



### 230B. T-primes

binary search/implementation/math/number theory, 1300, http://codeforces.com/problemset/problem/230/B



思路：一年半前做的，思路大概就是打素数表，打素数表的过程中跳过已经确认是合数的数。



##### 代码

```python
import math
def f(m):
        b=[False]*2+[True]*(m-1)
        p=2
        while p*p<=m:
            if b[p]:
                for i in range(p**2,m+1,p):
                    b[i]=False
            p=p+1
        return b
x=f(10**6)
n=int(input())
a=[int(i) for i in input().split()]
for i in range(n):
    p=a[i]
    m=round(math.sqrt(p))
    if m**2==p:
        if x[m]:
            print('YES')
        else:
            print('NO')
    else:
        print('NO')

```



代码运行截图 ![image-20240302145820275](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240302145820275.png)





### 1364A. XXXXX

brute force/data structures/number theory/two pointers, 1200, https://codeforces.com/problemset/problem/1364/A



思路：一开始直接暴力计算发现超时，然后去除了一些多余计算以后成功。



##### 代码

```python
t=int(input())
for l in range(t):
    n,x=[int(i) for i in input().split()]
    a=[int(i) for i in input().split()]
    A=[0]*(n+1)
    A[0]=0
    ans=0
    D=set()
    for i in range(n):
        A[i+1]=(A[i]+a[i])%x
    for i in range(n+1):
        if A[i] in D:
            continue
        else:
            D.add(A[i])
        for j in range(n,i,-1):
            if A[i]!=A[j]:
                ans=max(ans,j-i)
                break
    if ans==0:
        ans=-1
    print(ans)
```

代码运行截图 ![image-20240302134241465](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240302134241465.png)





### 18176: 2050年成绩计算

http://cs101.openjudge.cn/practice/18176/



思路：筛素数的时候可以把已经筛选过是合数的数跳过

但是我自己写的代码不知道为什么一直超时 只好抄了题解



##### 代码

```python
from math import sqrt
N = 10005

s = [True] * N
p = 2
while p * p <= N:
	if s[p]:
		for i in range(p * 2, N, p):
			s[i] = False
	p += 1

m, n = [int(i) for i in input().split()]

for i in range(m):
	x = [int(i) for i in input().split()]
	sum = 0
	for num in x:
		root = int(sqrt(num))
		if num > 3 and s[root] and num == root * root:
			sum += num
	sum /= len(x)
	if sum == 0:
		print(0)
	else:
		print('%.2f' % sum)
        
        
以下为我自己的代码     
import math
P=[1]*10000
P[0]=0
P[1]=0
for i in range(2,100):
    if P[i]==1:
        j=2
        for j in range(i*2,10000,i):
            P[j]=0
m,n=[int(i) for i in input().split()]
for t in range(m):
    a=[int(i) for i in input().split()]
    x=0
    for i in range(len(a)):
        m=round(math.sqrt(a[i]))
        if m**2==a[i] and P[m]==1:
            x=x+a[i]
    if x==0:
        print(0)
    else:
        t=x/len(a)
        print(f"{t:.2f}")
```



代码运行截图![image-20240302230418142](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240302230418142.png)



## 2. 学习总结和收获

除了算法之外还是有很多麻烦的东西需要熟悉和掌握，我会努力掌握python语法的。

集合语法：.add



