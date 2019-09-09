# octave/matlab 编程

5 / 8 = 0.625
2^6 = 64
1 == 2 用来进行逻辑判断1是否等于2， 如果为真 返回1 否则返回0
1 ~= 2 用来进行判断1是否不等于2
% 表示注释  
1 && 0 表示逻辑与
1 || 0 表示逻辑或
xor(1,0) 表示异或运算
PS1('>> ') 将命令提示符改为>>
a = 3 给变量a赋值，同时打印变量a的值，如果我们不想打印可以在末尾加上分号 a = 3;
a = pi 赋值圆周率
disp(a) 打印a的值, disp命令用来打印复杂字符串
disp(sprintf('2 decimals: %0.2f', a))

```octave
>> sprintf("2 decimals %0.2f", a)
ans = 2 decimals 3.00
>> disp(sprintf("2 decimals %0.2f", a))
2 decimals 3.00
```

format long 可以让字符串显示默认的位数，将会显示更多的小数点位数
format short 默认输出少量的小数点后位数


A = [1 2; 3 4; 5 6] 会产生一个3行2列的矩阵, 分号的作用是矩阵换行到下一行
另一种等价方式是如下：
```octave
>> A = [1 2;
> 3 4;
> 5 6;
> ]
A =

   1   2
   3   4
   5   6

>> 
```

v = [1 2 3] 建立一个行向量
v = [1; 2; 3] 建立一个列向量
v = 1 : 0.1 : 2 将v理解为一组值，从1开始，步长为0.1，加到2
v = 1 : 6 赋值1-6
ones(2, 3) 生成2行3列的全部为1的矩阵
zeros(1, 3) 生成1行3列的零矩阵
rand(1, 3) 得到随机的1行3列矩阵
rand(3, 3) 得到随机的3行3列矩阵
randn(1, 3) 得到服从高斯分布（均值为0，标准差或方差为1）的1行3列的矩阵
sqrt(22) 求算数平方根
hist(m) 将m绘制成一个直方图
hist(m, 50) 将m绘制成一个直方图，同时展示50个竖条的直方图
eye(4) 生成4维的单位矩阵
help eye 帮助命令，查询eye的作用

size(A) 返回矩阵A的大小
size(A, 1) 返回矩阵A的第1维大小
length(向量或矩阵) 返回矩阵或向量的最大维度 



## 存储和加载数据
pwd 显示当前所在路径

load 数据集路径+名字 载入数据集
load('数据集路径+名字') 载入数据集 **octave中使用单引号**

who 显示当前在内存中存储的变量
whos 可以更加详细的展示内存中存储的变量，显示变量的维度大小，以及内存大小
clear 变量名 直接删除对应名字的变量， **直接输入clear 将会删除工作空间的所有变量**

v = priceY(1:10) 表示将将向量priceY的前10个元素赋值给v

save hello.mat v; 将会使变量v的数据保存到文件hello.mat中
save hello.txt v -ascii 将变量v的数据采用ascii编码保存到hello.txt文件中

## 操作数据
A(3, 2) 第3行的第2列数据
A(: , 2)  所有行的第2列数据
A(2, :) 第2行的所有列数据
A([1 3], :) 得到第1和第3行的所有数据
A(:, 2) = [10; 11; 12] 修改A的第2列数据为10 11 12
A = A[A, [100; 101; 102]]; 表示在A的最右边加上了一列新向量
A(:) 把A中所有元素放入到一个列向量中
C = [A B] 把A矩阵和B矩阵结合在一起
C = [A ; B] 把矩阵A和B上下排列

## 计算数据

A * B 两个矩阵相乘
A .* B 会将A中各个元素与B相乘, **.号一般用于表示元素的运算**
log(v) 分别对v中各个元素求对数
exp(v) 以e为底，以v中元素为指数的运算
abs(v) 来对v中每个元素求绝对值
对v中每个元素都加1  v+1 或者 v + ones(length(v), 1)
A' 表示A的转置
max(A) 获得矩阵A每列的最大值
max(a) 获得a向量的最大值以及索引
[mx, inc] = max(a) mx将会被赋值最大值，inc将会被赋值最大值的索引
find(a < 3) 返回小于3的索引集
magic(n) 生成一个n维的幻方矩阵，指的是对角线，每行每列的元素和都相等
sum(a) 得到所有元素的和
prod(a) 得到所有元素的乘积
floor(a) 对a中的每个元素下取整
ceil(a) 对a中的每个元素上取整
rand(3) 返回3*3的随机矩阵  
max(rand(3), rand(3)) 取两个矩阵对应元素的最大值组合而成的矩阵
max(A, [], 1) 按照第1维(列)返回A矩阵最大值
max(A, [], 2) 按照第2维(行)返回A矩阵最大值
max(max(A)) 或者 max(A(:)) 获得矩阵A的最大值
sum(A, 1) 矩阵按照列求和
sum(A, 2) 矩阵按照行求和
flipud(A) 矩阵A进行翻转
pinv(A) 求矩阵A的逆矩阵

## 数据绘制

t = [0:0.01:0.98]
y1 = sin(2 * pi * 4 * t)
plot(t, y1) 

y2 = cos(2 * pi * 4 * t)
plot(t, y1)
plot(t, y2)
hold on; 意思就是在该图的基础上绘图，而不是重新制作一张图
plot(t, y2, 'r') 绘图，并使用红色绘制
xlabel('time') x轴加上time标签
ylabel('value') y轴加上标签
legend('sin', 'cos') 图片的右上角加上提示符
title('my plot') 给图加上标题
cd 'c:\'; print -dpng 'myplot.png' 将图片保存到C盘
close 关掉图像
figure(1) plot(t, y1) 绘制正弦，绘制之后不会关闭之前的图像
figure(2) plot(t, y2) 绘制余弦，绘制之后不回关闭之前的图像
subplot(1, 2, 1) 将图像分解为1*2的格子，我现在使用第1(第3个参数)个格子
plot(t, y1) 将会绘制在第1个格子上
subplot(1, 2, 2) 
plot(t, y2)
axis([0.5 1 -1 1]) 设置x轴的范围从0.5到1， 设置y轴的范围从-1到1
clf 清除图像
imagesc(A) 
imagesc(A), colorbar, colormap gray;
imagesc(magic(15)), colorbar, colormap gray;
a=1, b=2, c=3 命令是一个接一个执行的，将会输出3个变量的值
a=1; b=2; c=3 命令也是一个接一个执行，将不会输出3个变量的值


## 控制语句

```octave
for i = 1:10,
   v(i)=2^i
end;
```

```octave
indices=1:10;
for i=indices,
   disp(i);
end;
```

```octave
i=1
while true,
   v(i) = 999;
   i = i + 1
   if i == 6,
      break;
   end;       结束if语句
end;          结束while循环
```

```octave
v(1) = 2;
if v(i) = 999,
   disp('The value is one');
elseif v(i) == 2,
   disp('The value is one');
else
   disp('The value is not one or two.');
end;
```

在octave环境中定义函数，需要定义一个文件，文件名就是函数名，文件末尾以.m结尾
使用函数的时候需要提前进入到函数文件所在的路径
