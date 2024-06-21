# Assignment #7: April 月考

Updated 1557 GMT+8 Apr 3, 2024

2024 spring, Complied by 张羽扬 数学科学学院



**说明：**

1）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

2）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

3）如果不能在截止前提交作业，请写明原因。



**编程环境**

操作系统：Windows 11 家庭中文版 22H2

Python编程环境：Spyder IDE 5.2.2

C/C++编程环境：无



## 1. 题目

### 27706: 逐词倒放

http://cs101.openjudge.cn/practice/27706/



思路：



代码

```python
a=input().split(' ')
a.reverse()
print(' '.join(a))
```



代码运行截图 ![image-20240409215733643](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240409215733643.png)





### 27951: 机器翻译

http://cs101.openjudge.cn/practice/27951/



思路：



代码

```python
A=[]
m,n=[int(i) for i in input().split()]
b=[int(i) for i in input().split()]
k=0
r=0
t=0
for i in b:
    if i not in A:
        if r==0:
            A.append(i)
            k=k+1
            if len(A)==m:
                r=1
        else:
            A[t]=i
            t=(t+1)%m
            k=k+1
print(k)
```



代码运行截图 ![image-20240409215755972](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240409215755972.png)





### 27932: Less or Equal

http://cs101.openjudge.cn/practice/27932/



思路：需要注意一下边界情况

如果没有sort函数我会选择二分



代码

```python
n,k=[int(i) for i in input().split()]
a=[int(i) for i in input().split()]
a.sort()
if k==n:
    print(a[-1])
elif k==0:
    if a[0]==1:
        print(-1)
    else:
        print(a[0]-1)
else:
    if a[k]==a[k-1]:
        print(-1)
    else:
        print(a[k-1])

```



代码运行截图 ![image-20240409215838097](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240409215838097.png)





### 27948: FBI树

http://cs101.openjudge.cn/practice/27948/



思路：



代码

```python
class node:
    def __init__(self,x):
        self.val=x
        self.left=None
        self.right=None
def f(x):
    if '1' not in x:
        return 'B'
    if '0' not in x:
        return 'I'
    else:
        return 'F'
def g(a):
    x=node(f(a))
    t=len(a)
    if t==1:
        return x
    else:
        b=a[:t//2]
        c=a[t//2:]
        x.left=g(b)
        x.right=g(c)
        return x
def h(u):
    a=''
    if u==None:
        return a
    else:
        a+=h(u.left)
        a+=h(u.right)
        a+=u.val
        return a
n=int(input())
a=input()
x=g(a)
y=h(x)
print(y)
```



代码运行截图 ![image-20240409215938080](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240409215938080.png)





### 27925: 小组队列

http://cs101.openjudge.cn/practice/27925/



思路：



代码

```python
# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





### 27928: 遍历树

http://cs101.openjudge.cn/practice/27928/



思路：



代码

```python
# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





## 2. 学习总结和收获

前4道题共花了50分钟 剩下两道题目之后会研究



