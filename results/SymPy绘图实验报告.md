# SymPy 绘图实验报告

## 一、实验信息

- 小组名称：009
- 成员：杨万超，王雪涵，余维，肖婷丹
- 实验日期：2025/4/10

---

## 二、实验目的

- 熟悉SymPy的plot、plot_implicit、和plot3d_parametric_surface函数；
- 掌握曲线、隐函数和参数曲面的绘制方法。

---

## 三、实验内容与方法

分别说明三个问题的具体绘图方法和使用的函数接口。
1.绘制函数曲线 cos(tan(πx))

使用的函数：plot

绘图方法
定义符号变量：```x = sp.symbols('x')```

定义表达式：```expr = sp.cos(sp.tan(sp.pi * x))```

调用绘图函数：```plot(expr, (x, -1, 1), xlabel='x', ylabel='cos(tan(pi*x))', title='Problem 1: Plot of cos(tan(pi*x))')```
使用plot函数将上述表达式绘制在区间[-1, 1]之上，并设置了坐标轴标签和标题。

2.绘制隐函数曲线 ```e^y + cos(x)/x + y = 0```

使用的函数：```plot_implicit```

绘图方法
定义符号变量：```x, y = sp.symbols('x y')```

定义隐式表达式：```expr = sp.exp(y) + sp.cos(x)/x + y```

调用绘图函数：```plot_implicit(expr, (x, -10, 10), (y, -10, 10), xlabel='x', ylabel='y', title='Problem 2: Implicit plot of exp(y)+cos(x)/x+y=0', points=500)```
使用plot_implicit函数绘制隐函数，(x, -10, 10)和(y, -10, 10)指定绘图区域，points=500设置绘制点的数量，提高图形的细腻程度。

3.绘制参数曲面

使用的函数：plot3d_parametric_surface

绘图方法
定义符号变量：```s, t = sp.symbols('s t')```

定义参数曲面的表达式：
```
x = sp.exp(-s) * sp.cos(t)

y = sp.exp(-s) * sp.sin(t)

z = t
```
调用绘图函数：```plot3d_parametric_surface(x, y, z, (s, 0, 8), (t, 0, 5*sp.pi), xlabel='x', ylabel='y', zlabel='z', title='Problem 3: Parametric Surface Plot')```
使用plot3d_parametric_surface绘制参数化曲面，(s, 0, 8)和(t, 0, 5π)定义了参数的取值范围，并设置了坐标轴标签和标题。

---

## 四、实验结果与分析

### 问题1: 函数曲线 $\cos(\tan(\pi x))$ 绘制结果


![image](https://github.com/user-attachments/assets/de807304-f2ee-49c1-9ea3-23f41e2e759e)

曲线特点：tan(πx)为奇函数，cos(x)为偶函数，故cos(tan(πx))为偶函数,曲线沿x轴对称。cos函数是一个周期函数，因此cos(tan(πx))也具有一定的周期性。由于tan函数在其周期内会从负无穷到正无穷变化，cos(tan(πx))的图形在一定区间内表现出复杂的震荡特性。

### 问题2: 隐函数曲线 $e^y + \frac{\cos x}{x} + y = 0$ 绘制结果


![image](https://github.com/user-attachments/assets/edb34563-1ce7-487f-928d-b9af3dd26c12)

曲线特点：在y较大时，e^y值大，导致隐函数的右侧整体更可能小于0，呈现出一条向下倾斜的趋势。由于方程较为复杂，曲线展现出交错和凹凸结构。

### 问题3: 参数曲面绘制结果


![image](https://github.com/user-attachments/assets/9e262af7-41e0-4097-93b0-4ee281e8e177)

曲线特点：曲面从原点开始向外展开，形成类似于螺旋的结构，t参数增加时，x和y会以圆周运动形式向外“扩展”。这是一个三维曲面，参数s和t的变化使得该结构具有高度的视觉复杂性，展现了三维空间中的动态变化。

---

## 五、实验总结与讨论

- 通过本实验你掌握了哪些绘图技巧？

1.学会了如何使用plot()函数绘制一般的数学函数图形，plot_implicit()绘制隐函数，plot3d_parametric_surface()绘制三维参数曲面，设置合适的变量范围、标签和标题。

2.通过调整点的密度等参数，提高绘图的清晰度和细腻程度，确保图形表述准确。了解如何通过调整参数范围来控制曲面的外观，增加其视觉效果。

- 实验中你遇到了哪些问题？如何解决？

问题：在绘制隐函数e^y + cos(x)/x + y = 0时，cos(x)/x在x=0处未定义，导致绘图过程中出现错误。

解决方法：调整绘图范围：在定义绘图区间时，将x的范围设置为[-10, 10]，同时避免包含0，如将区间改为[0.1, 10]。这样可以避免计算cos(0)/0的问题。


问题：在绘制参数曲面时，初始选择的参数范围可能导致曲面显示不全或效果不佳。

解决方法：实验不同参数：通过尝试不同的s和t的范围（如(s, 0, 8)和(t, 0, 5π)），观察曲面的变化，以找到最佳的展示效果。


问题：在使用新函数（如plot_implicit和plot3d_parametric_surface）时，可能对函数的参数和用法不熟悉，导致初始绘图效果不佳或报错。

解决方法：逐步试验并进行细节调整。

- 你对SymPy的绘图功能有什么建议或意见？
在遇到错误或绘制问题时，提供更详细的错误信息和解决方案。

针对某些复杂函数的绘图性能进行优化，提升绘图的速度和效率。

增加更为多样化的配色方案、样式选项和绘图美化功能

---

## 六、参考文献

- SymPy官方文档：https://docs.sympy.org/latest/modules/plotting.html
