# SVG



## 1. svg标签

```html
<svg version="1.1" xmlns="http://www.w3.org/2000/svg" width="100" height="100">
  
</svg>
```



## 2.rect

```html
<rect x ="10" y="10" width="30" height="30" rx="5" ry="5"/>
```



## 3.circle

```html
<circle cx="25" cy="25" r="20"/>
```



## 4.ellipse

```htm
<ellipse cx="75" cy="75" rx="20" ry="10">
```



## 5.line

```
<line x1="10" x2="50" y1="110" y2="150"/>
```



## 6.polyline

```html
<polyline points="60 110, 65 120, 70 115, 75 130, 80 125, 85 140, 90 135, 95 150, 100 145"/>
```



## 7.polygon

```html
<polygon points="50 160, 55 180, 70 180, 60 190, 65 205, 50 195, 35 205, 40 190, 30 180, 45 180"/>
```



## 8.path

```html
<path d="M 20 230 Q 40 205, 50 230 T 90230"/>
```

如下大写命令为确定的位置，小写命令为相对当前点移动的距离。

### 直线命令

**（1）Move to命令**

> M x y 或 m dx dy

Move to命令，只是将画笔移动到(x,y)点

**（2）Line to命令**

> L x y 或 l dx dy

Line to命令，将画笔移动到新位置，并划线

**（3）垂直或水平**

> H x (或 h dx)
>
> V y (或 v dy)

**（4）闭合 ** 

> L x y 或 l dx dy

闭合，将当前位置与起点相连接



### 曲线命令

**（1）三次贝塞尔曲线**

> C x1 y1, x2 y2, x y (or c dx1 dy1, dx2 dy2, dx dy)

坐标(x,y)表示的是曲线的终点，另外两个坐标是控制点，(x1,y1)是起点的控制点，(x2,y2)是终点的控制点。

**（2）s命令**

> S x2 y2, x y (or s dx2 dy2, dx dy)

S命令可以用来创建与前面一样的贝塞尔曲线，但是，如果S命令跟在一个C或S命令后面，则它的第一个控制点会被假设成前一个命令曲线的第二个控制点的中心对称点。如果S命令单独使用，前面没有C或S命令，那当前点将作为第一个控制点。

**（3）二次贝塞尔曲线**

> Q x1 y1, x y (or q dx1 dy1, dx dy)

**(4) t命令**

> T x y (or t dx dy)

快捷命令T会通过前一个控制点，推断出一个新的控制点



### 弧形命令

> A rx ry x-axis-rotation large-arc-flag sweep-flag x y
>  a rx ry x-axis-rotation large-arc-flag sweep-flag dx dy

rx ry x轴和y轴半径

x-axis-rotation 弧形旋转程度

large-arc-flag 角度大小 

sweep-flag 弧线方向

x y (dx dy) 弧形终点位置



## 9.填充和边框

* **fill**设置对象内部的眼神

* **stroke**设置对象的线条颜色
* 可以使用css部分属性

```html
<style type="text/css">
  #MyRect {
    stroke: black;
    fill: red;
  }
</style>
<rect x="10" height="180" y="10" width="180" id="MyRect"/>
```



## 10.渐变

```html
<defs>
  <linearGradient />
  <radialGradient />
</defs>
```





























