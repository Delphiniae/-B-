# Assignment #1: 拉齐大家Python水平

Updated 0940 GMT+8 Feb 19, 2024

2024 spring, Complied by 张羽扬 数学科学学院



**说明：**

1）数算课程的先修课是计概，由于计概学习中可能使用了不同的编程语言，而数算课程要求Python语言，因此第一周作业练习Python编程。如果有同学坚持使用C/C++，也可以，但是建议也要会Python语言。

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）课程网站是Canvas平台, https://pku.instructure.com, 学校通知3月1日导入选课名单后启用。**作业写好后，保留在自己手中，待3月1日提交。**

提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



**编程环境**

操作系统：Windows 11 家庭中文版 22H2

Python编程环境：Spyder IDE 5.2.2, PyCharm 2023.1.4 (Professional Edition)

C/C++编程环境：无



## 1. 题目

### 20742: 泰波拿契數

http://cs101.openjudge.cn/practice/20742/



思路：递推



##### 代码

```python
a=[0,1,1]
n=int(input())
for i in range(n):
    a.append(a[-1]+a[-2]+a[-3])
print(a[n])
```



代码运行截图 ![image-20240221001447032](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240221001447032.png)





### 58A. Chat room

greedy/strings, 1000, http://codeforces.com/problemset/problem/58/A



思路：在b中接下去找a的下一个字母直到找齐五个



##### 代码

```python
a='hello'
b=str(input())
while a!='' and b!='':
    if b[0]==a[0]:
        b=b[1:]
        a=a[1:]
    else:
        b=b[1:]
if a=='':
    print('YES')
else:
    print('NO')
```



代码运行截图 ![image-20240221003332268](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240221003332268.png)





### 118A. String Task

implementation/strings, 1000, http://codeforces.com/problemset/problem/118/A



思路：照着他说的做就行，先转大小写再删元音字符可以少输入一半的元音字符



##### 代码

```python
t=str(input())
t=t.lower()
for i in ['a','e','i','o','u','y']:
    t=t.replace(i,'')
t='.'+'.'.join(t)
print(t)
```



代码运行截图

![image-20240221005443632](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240221005443632.png)

### 22359: Goldbach Conjecture

http://cs101.openjudge.cn/practice/22359/



思路：创建素数列表，然后挨个试



##### 代码

```python
n=int(input())
P=list(range(1,n))
Q=[]
for i in range(2,n):
    for j in range(2,n):
        if i*j<n:
            P[i*j-1]=0
        else:
            break
for i in range(0,n-1):
    if P[i]!=0:
        Q.append(P[i])
for i in Q:
    if n-i in Q:
        print(i,n-i)
        break
```



代码运行截图![image-20240221001810128](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240221001810128.png)





### 23563: 多项式时间复杂度

http://cs101.openjudge.cn/practice/23563/



思路：一开始以为系数会有正负，因此要考虑高次项系数加起来是否会是0，后来发现不用 只需剔除掉所有以0为系数的项然后找到最高次即可



##### 代码

```python
a=str(input()).split('+')
m=0
for i in a:
    if i[0]!='0':
        t=i.find('^')
        n=int(i[(t+1):])
        m=max(n,m)
m=str(m)
print('n^'+m)
```



代码运行截图 ![image-20240222004722617](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240222004722617.png)





### 24684: 直播计票

http://cs101.openjudge.cn/practice/24684/



思路：用列表的话需要创建100000长度的列表，由于数据的范围，因此应使用字典。



##### 代码

```python
a={}
t=[int(i) for i in input().split()]
for i in t:
    if i in a:
        a[i]=a[i]+1
    else:
        a[i]=1
M=max(a.values())
t=[]
for i in a:
    if a[i]==M:
        t=t+[i]
t.sort()
for i in t:
    print(i,end=' ')
```



代码运行截图![image-20240222011738578](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240222011738578.png)





## 2. 学习总结和收获

作业的算法大多很简单，但本人python语法水平有待提高，许多列表和字符串的函数和用法都是现查的。

