# Assignment #3: March月考

Updated 1537 GMT+8 March 6, 2024

2024 spring, Complied by 张羽扬 数学科学学院



**说明：**

1）The complete process to learn DSA from scratch can be broken into 4 parts:
- Learn about Time and Space complexities
- Learn the basics of individual Data Structures
- Learn the basics of Algorithms
- Practice Problems on DSA

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



**编程环境**

操作系统：Windows 11 家庭中文版 22H2

Python编程环境：Spyder IDE 5.2.2, PyCharm 2023.1.4 (Professional Edition)

C/C++编程环境：无



## 1. 题目

**02945: 拦截导弹**

http://cs101.openjudge.cn/practice/02945/

用时5min

思路：“以第j个位置的数为结尾的最长递减列“可以很好的递推计算



##### 代码

```python
n=int(input())
a=[int(i) for i in input().split()]
u=[1]*n
for i in range(n):
    for j in range(i):
        if a[i]<=a[j]:
            u[i]=max(u[j]+1,u[i])
print(max(u))

```



代码运行截图 

![image-20240306223215340](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240306223215340.png)

**04147:汉诺塔问题(Tower of Hanoi)**

http://cs101.openjudge.cn/practice/04147

用时10min

思路：先把前n-1行移到b上 所以是把b和c交换进行n-1情况的操作，然后把第n行移到c上，接着把b处的n-1个移到c上，所以是交换a与b进行n-1情况的操作



##### 代码

```python
def f(n,a,b,c):
    if n==0:
        return
    f(n-1,a,c,b)
    print(str(n)+':'+str(a)+'->'+str(c))
    f(n-1,b,a,c)
n,a,b,c=input().split()
n=int(n)
f(n,a,b,c)

```



代码运行截图 ![image-20240306224424164](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240306224424164.png)





**03253: 约瑟夫问题No.2**

http://cs101.openjudge.cn/practice/03253

不记得用时了 总之好像很快？

思路：模拟，想不明白细节就先试试，根据输出再调整是p还是p-1，m还是m-1之类的事



##### 代码

```python
while 1:
    n,p,m=[int(i) for i in input().split()]
    if n==0:
        break
    u=[]
    a=[str(i) for i in range(1,n+1)]
    x=p-1
    for i in range(n):
        x=(x+m-1)%len(a)
        u.append(a.pop(x))
    print(','.join(u))
```

代码运行截图

![image-20240306230429054](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240306230429054.png)



**21554:排队做实验 (greedy)v0.2**

http://cs101.openjudge.cn/practice/21554

用时15min

思路：把xi排序让Σ(n-i)xi最小(这里的i是1到n)

所以（由排序不等式）时间越短越先做，所以排一下序就好了

将x保留两位小数输出的方法是'%.2f'%x，需要记一下



##### 代码

```python
n=int(input())
a=[int(i) for i in input().split()]
b=[]
for i in range(n):
    b.append((a[i],i+1))
b.sort()
c=[]
d=0
for i in range(n):
    c.append(str(b[i][1]))
    d=d+(n-i-1)*b[i][0]
d=d/n
print(' '.join(c))
print('%.2f'%d)
```



代码运行截图![image-20240307001255520](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240307001255520.png)





**19963:买学区房**

http://cs101.openjudge.cn/practice/19963

用时约1h...

思路：把序列排序找出中位数 然后把原始序列一个个比对中位数看是否满足条件

花了很久时间一个在于写错了关于性价比的不等号，另一个在于忘记了浅拷贝和深拷贝，直接令b=B试图复制一个列表，在一开始这两个错误负负得正导致我两个样例都过了... 所以查了很久错

这题的数据预处理也很麻烦 自己写了一遍才看到提示，不太喜欢这种一眼看出思路然后剩下的都是脏活的题，如果参加了月考上机的话多半会跳过这个。



##### 代码

```python
n=int(input())
pairs=[i[1:-1] for i in input().split()]
A=[sum(map(int,i.split(','))) for i in pairs]
B=[int(i) for i in input().split()]
C=[]
c=[]
a=A
b=[]
for i in range(n):
    C.append(a[i]/B[i])
    c.append(C[i])
    b.append(B[i])
b.sort()
c.sort()
if n%2==1:
    x=b[n//2]
    y=c[n//2]
else:
    x=(b[n//2-1]+b[n//2])/2
    y=(c[n//2-1]+c[n//2])/2
u=[1]*n
for i in range(n):
    if B[i]>=x or C[i]<=y:
        u[i]=0
print(sum(u))
```



代码运行截图 ![image-20240307010003398](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240307010003398.png)



**27300: 模型整理**

http://cs101.openjudge.cn/practice/27300

用时约20min

思路：定义一个函数来翻译带有B和M的数，然后根据这个函数值来排列，因为不太会字典相关的函数用法索性就另外维护一个字典键的集合了



##### 代码

```python
def f(a):
    if a[-1]=='M':
        return(float(a[:-1]))
    if a[-1]=='B':
        return(float(a[:-1])*1000)

n=int(input())
a=set()
b=dict()
for i in range(n):
    x=input().split('-')
    if x[0] in a:
        b[x[0]].append(x[1])
    else:
        a.add(x[0])
        b[x[0]]=[x[1]]
a=list(a)
a.sort()
for i in a:
    b[i].sort(key=f)
    t=', '.join(b[i])
    print(i+': '+t)
```



代码运行截图![image-20240307012404764](C:\Users\ZYY\AppData\Roaming\Typora\typora-user-images\image-20240307012404764.png)





## 2. 学习总结和收获

将x保留两位小数输出的方法是'%.2f'%x

可以定义一个函数f然后使用key=f按函数值排序

使用‘=’复制可变对象是浅拷贝 其中一个改变另一个会一起改变 想要深拷贝列表的时候可以把列表元素一个个拿出来加到新列表里

然后我写的代码好像都挺短的 比较高兴



