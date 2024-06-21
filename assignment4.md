# Assignment #4: 排序、栈、队列和树

Updated 0005 GMT+8 March 11, 2024

2024 spring, Complied by 张羽扬 数学科学学院



**说明：**

1）The complete process to learn DSA from scratch can be broken into 4 parts:

Learn about Time complexities, learn the basics of individual Data Structures, learn the basics of Algorithms, and practice Problems.

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



**编程环境**

操作系统：Windows 11 家庭中文版 22H2

Python编程环境：Spyder IDE 5.2.2

C/C++编程环境：无



## 1. 题目

### 05902: 双端队列

http://cs101.openjudge.cn/practice/05902/



思路：



代码

```python
t=int(input())
for i in range(t):
    n=int(input())
    a=[]
    for i in range(n):
        x=[int(i) for i in input().split()]
        if x[0]==1:
            a.append(str(x[1]))
        else:
            if x[1]==0:
                a.pop(0)
            else:
                a.pop(-1)
    if a:
        print(' '.join(a))
    else:
        print('NULL')
```



代码运行截图 ![image-20240319174948045](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240319174948045.png)



### 02694: 波兰表达式

http://cs101.openjudge.cn/practice/02694/



思路：题目没说要保留几位小数 直接输出就死了...



代码

```python
a=input().split()
n=len(a)
b=[]
c=0
for i in range(n):
    x=a.pop()
    if x=='+':
        t=b.pop()
        b[-1]=b[-1]+t
    elif x=='-':
        t=b.pop()
        b[-1]=t-b[-1]
    elif x=='*':
        t=b.pop()
        b[-1]=b[-1]*t
    elif x=='/':
        t=b.pop()
        b[-1]=t/b[-1]
    else:
        b.append(float(x))
print('{:.6f}'.format(b[0]))
```



代码运行截图![image-20240319171759249](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240319171759249.png)





### 24591: 中序表达式转后序表达式

http://cs101.openjudge.cn/practice/24591/



思路：这也太难了...从输入处理开始就不知道怎么做 栈的操作多花些时间应该也可以想出来 但是我选择看题解了



代码

```python
# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==





### 22068: 合法出栈序列

http://cs101.openjudge.cn/practice/22068/



思路：采用了抛出异常的方法来解决输入不知道何时结束的问题

RE了半天发现输入不一定和原字符串长度一样...有点病 我还以为是我抛异常写错了，最后照着计概时候邮箱验证的异常处理重新写了一遍。



代码

```python
x=str(input())
n=len(x)
while 1:
    try:
        y=str(input())
        a=[]
        if len(y)!=n:
            print('NO')
            continue
        for i in x:
            if i==y[0]:
                y=y[1:]
                if len(a)!=0:
                    while a[-1]==y[0]:
                        a.pop()
                        y=y[1:]
                        if len(a)==0:
                            break
            else:
                a.append(i)
        if len(y)==0:
            print('YES')
        else:
            print('NO')
    except EOFError:
        break
```



代码运行截图 ![image-20240319175215041](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240319175215041.png)





### 06646: 二叉树的深度

http://cs101.openjudge.cn/practice/06646/



思路：



代码

```python
n=int(input())
a=[0]
S=set(range(1,n+1))
T=set()
for i in range(1,n+1):
    x=[int(j) for j in input().split()]
    a.append(x)
    S.discard(x[0])
    S.discard(x[1])
for t in range(1,n+1):
    T.clear()
    for i in S:
        T.add(a[i][0])
        T.add(a[i][1])
    T.discard(-1)
    S.clear()
    S.update(T)
    if len(S)==0:
        break
print(t)
```



代码运行截图![image-20240319165243324](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240319165243324.png)





### 02299: Ultra-QuickSort

http://cs101.openjudge.cn/practice/02299/



思路：学习了归并排序

一开始很不想使用递归，后来想了半天也没有别的办法就只好写了



代码

```python
def f(a,b):
    global x
    c=[]
    while a and b:
        if a[-1]>b[-1]:
            c.append(a.pop())
            x=x+len(b)
        else:
            c.append(b.pop())
    c.reverse()
    c=a+b+c
    return c
def g(a):
    n=len(a)
    t=n//2
    if t==0:
        return a
    u=g(a[:t])
    v=g(a[t:])
    x=f(u,v)
    return x


while 1:    
    n=int(input())
    if n==0:
        break
    a=[]
    x=0
    for i in range(n):
        a.append(int(input()))
    g(a)
    print(x)
```



代码运行截图

![image-20240319165329923](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240319165329923.png)

## 2. 学习总结和收获

需要多学习树的写法了，最后一题搜索发现可以用树状数组做，但我不会





