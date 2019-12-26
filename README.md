# Flex Layout

目录
[toc]

## 文件目录介绍

Flex Attr - flex 属性

Dice Layout - 骰子布局

Classical Layout - 经典布局

Image - 示例图片

## FlexBox
### 布局方案
* 传统布局方案：基于盒状模型，display + position + flex
* flex布局方案：Flex是Flexible Box的缩写，意为”弹性布局”。简便、完整、响应式地实现各种页面布局

### 兼容性
* ie10+

### 指定为flex布局
* 块状元素 `.box { display: flex; }`
* 行内元素 `.box { display: inline-flex; }`
```css
/* 1.Webkit内核的浏览器，必须加上-webkit前缀 */
.box{
  display: -webkit-flex; /* Safari */
  display: flex;
}
/* 2.设为Flex布局以后，子元素的float、clear和vertical-align属性将失效*/
```

## 容器的属性
### flex-direction  排列方向
> flex-direction属性决定主轴的方向（即项目的排列方向）
```html
<div class="box">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
    <div class="item">4</div>
</div>
```

#### 值
1. **row**（默认值）：主轴为水平方向，起点在左端
    
    ```mermaid
        graph LR
        1-->2
        2-->3
        3-->4
    ```
    
    ```css
    .box {
        display: -webkit-flex; /* Safari */
        display: flex;
        flex-direction: row;
    }
    ```
2. **row-reverse**：主轴为水平方向，起点在右端。
    ```mermaid
        graph RL
        1-->2
        2-->3
        3-->4
    ```

    ```css
    .box {
        display: -webkit-flex; /* Safari */
        display: flex;
        flex-direction: row-reverse;
    }
    ```
3. **column**：主轴为垂直方向，起点在上沿。
    ```mermaid
        graph TB
        1-->2
        2-->3
        3-->4
    ```

    ```css
    .box {
        display: -webkit-flex; /* Safari */
        display: flex;
        flex-direction: column;
    }
    ```
4. **column-reverse**：主轴为垂直方向，起点在下沿。
    ```mermaid
        graph BT
        1-->2
        2-->3
        3-->4
    ```

    ```css
    .box {
        display: -webkit-flex; /* Safari */
        display: flex;
        flex-direction: column-reverse;
    }
    ```
### flex-wrap 换行
> flex-wrap（flex-wrap属性定义，如果一条轴线排不下，如何换行）

```html
<div class="box">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
    <div class="item">4</div>
    <div class="item">5</div>
    <div class="item">6</div>
    <div class="item">7</div>
    <div class="item">8</div>
    <div class="item">9</div>
    <div class="item">10</div>
</div>
```

#### 值
1. **nowrap**（默认）：不换行(固宽容纳不下一行，会改变宽度)

| 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
| --- | --- | --- | --- | --- | --- | ---- | --- | --- | --- |

```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    flex-wrap: nowrap;
}
```

2. **wrap**: 换行，第一行在上方

| 1 | 2 | 3 |
| --- | --- | --- |
| **4** | **5** | **6** |
| **7** | **8** | **9** |
| **10** | &nbsp; | &nbsp; |

```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    flex-wrap: wrap;
}
```

3. **wrap-reverse**： 换行，第一行在下方

| 10 | &nbsp; | &nbsp; |
| --- | --- | --- |
| **7** | **8** | **9** |
| **4** | **5** | **6** |
| **1** | **2** | **3** |

```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    flex-wrap: wrap-reverse;
}
```
### flex-flow = flex-direction + flex-wrap
> flex-flow: 是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。

```html
.box {
  display: flex;
  flex-direction: row | row-reverse | column | column-reverse;
  flex-wrap: nowrap | wrap | wrap-reverse;
}
```
### justify-content 水平对齐，主轴上的对齐方式
> justify-content属性定义了项目在主轴上的对齐方式

```html
<div class="box">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
</div>
```

#### 值
1. **flex-start**：左对齐


| 1 | 2 | 3 | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| ---| --- | --- | --- | --- | --- | --- |


```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    justify-content: flex-start;
}
```

2. **flex-end**：右对齐

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | 1 | 2 |3 |
| ---| --- | --- | --- | --- | --- | --- |


```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    justify-content: flex-end;
}
```

3. **center**：居中

| &nbsp; | &nbsp; | 1 | 2 |3 | &nbsp;| &nbsp; |
| ---| --- | --- | --- | --- | --- | --- |

```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    justify-content: center;
}
```
4. **space-between**：两端对齐，项目之间的间隔都相等

| 1 | &nbsp; | &nbsp; |  2 | &nbsp; | &nbsp; | 3 |
| ---| --- | --- | --- | --- | --- | --- |

```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    justify-content: space-between;
}
```

5. **space-around**：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍

| &nbsp; | 1 | &nbsp; | 2 | &nbsp; | 3 | &nbsp; |
| ---| --- | --- | --- | --- | --- | --- |


```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    justify-content: space-around;
}
```
### align-items 垂直对齐，交叉轴上如何对齐
> align-items属性定义项目在交叉轴上如何对齐

```html
<div class="box">
    <div class="item">1</div> <!-- 1*height -->
    <div class="item">2</div> <!-- 3h -->
    <div class="item">3</div> <!-- 1h -->
</div>
```

1. **flex-start**：交叉轴的起点对齐

| 1 | 2 | 1 |
| --- | --- | --- |
|&nbsp; | **2** | &nbsp; |
|&nbsp; | **2** | &nbsp; |
|&nbsp; | &nbsp; | &nbsp; |
|&nbsp; | &nbsp; | &nbsp; |


```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    align-items: flex-start;
}
```

2. **flex-end**：交叉轴的终点对齐

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| &nbsp; | &nbsp; | &nbsp; |
| &nbsp; | **2** | &nbsp; |
| &nbsp; | **2** | &nbsp; |
| **1** | **2** | **1** |


```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    align-items: flex-end;
}
```

3. **center**：交叉轴的中点对齐

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
|&nbsp; | **2**  | &nbsp; |
| **1** | **2**  | **1**  |
|&nbsp; | **2**  | &nbsp; |
|&nbsp; | &nbsp; | &nbsp; |


```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    align-items: center;
}
```

4. **baseline**: 项目的第一行文字的基线对齐

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| **1** | **2** | **1** |
|&nbsp; | **2** | &nbsp; |
|&nbsp; | **2** | &nbsp; |
|&nbsp; | &nbsp; | &nbsp; |

```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    align-items: baseline;
}
```

5. **stretch**: 如果项目未设置高度或设为auto，将占满整个容器的高度

* 若有高度,等同`flex-start`

| 1 | 2 | 1 |
| --- | --- | --- |
|&nbsp; | **2** | &nbsp; |
|&nbsp; | **2** | &nbsp; |
|&nbsp; | &nbsp; | &nbsp; |
|&nbsp; | &nbsp; | &nbsp; |

* 若无高度,将占满整个容器的高度

| 1 | 2 | 1 |
| --- | --- | --- |
| **1** | **2** | **1** |
| **1** | **2** | **1** |
| **1** | **2** | **1** |
| **1** | **2** | **1** |


```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    align-items: stretch;
}
```
### align-content 多根轴线的对齐方式
> align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用

```html
<div class="box">
    <div class="item">1</div> <!-- 1h -->
    <div class="item">2</div> <!-- 2h -->
    <div class="item">3</div> <!-- 1h -->
    <div class="item">4</div> <!-- 1h -->
    <div class="item">5</div> <!-- 1h -->
    <div class="item">6</div> <!-- 2h -->
</div>
```

1. **flex-start**：与交叉轴的起点对齐。

| 1 | 2 | 3 |
| --- | --- | --- |
| &nbsp; | **2** | &nbsp; |
| **4** | **5** | **6** |
| &nbsp; | &nbsp; | **6** |
| &nbsp; | &nbsp; | &nbsp; |
| &nbsp; | &nbsp; | &nbsp; |


```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    flex-wrap: wrap;
    align-content: flex-start;
}
```

2. **flex-end**：与交叉轴的终点对齐。

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| &nbsp; | &nbsp; | &nbsp; |
| **1** | **2** | **3** |
| &nbsp; | **2** | &nbsp; |
| **4** | **5** | **6** |
| &nbsp; | &nbsp; | **6** |

```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    flex-wrap: wrap;
    align-content: flex-start;
}
```
3. **center**：与交叉轴的中点对齐。

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| **1** | **2** | **3** |
| &nbsp; | **2** | &nbsp; |
| **4** | **5** | **6** |
| &nbsp; | &nbsp; | **6** |
| &nbsp; | &nbsp; | &nbsp; |

```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    flex-wrap: wrap;
    align-content: center;
}
```
4. **space-between**：与交叉轴两端对齐，轴线之间的间隔平均分布。

| 1 | 2 | 3 |
| --- | --- | --- |
| &nbsp; | **2** | &nbsp; |
| &nbsp; | &nbsp; | &nbsp; |
| &nbsp; | &nbsp; | &nbsp; |
| **4** | **5** | **6** |
| &nbsp; | &nbsp; | **6** |

```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    flex-wrap: wrap;
    align-content: space-between;
}
```
5. **space-around**：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。

| &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- |
| **1** | **2** | **3** |
| &nbsp; | **2** | &nbsp; |
| &nbsp; | &nbsp; | &nbsp; |
| &nbsp; | &nbsp; | &nbsp; |
| **4** | **5** | **6** |
| &nbsp; | &nbsp; | **6** |
| &nbsp; | &nbsp; | &nbsp; |

```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    flex-wrap: wrap;
    align-content: space-around;
}
```
6. **stretch**（默认值）：轴线占满整个交叉轴。

* 若有高度，与`flex-start`一致

| 1 | 2 | 3 |
| --- | --- | --- |
| &nbsp; | **2** | &nbsp; |
| **4** | **5** | **6** |
| &nbsp; | &nbsp; | **6** |
| &nbsp; | &nbsp; | &nbsp; |
| &nbsp; | &nbsp; | &nbsp; |

* 若无高度

| 1 | 2 | 3 |
| --- | --- | --- |
| **1** | **2** | **3** |
| **1** | **2** | **3** |
| **4** | **5** | **6** |
| **4** | **5** | **6** |
| **4** | **5** | **6** |

```css
.box {
    display: -webkit-flex; /* Safari */
    display: flex;
    flex-wrap: wrap;
    align-content: flex-start;
}
```


## 项目的属性
### order 项目排列顺序
> order属性定义项目的排列顺序。数值越小，排列越靠前，默认为0

3 | 4 | 5 | 6 | *1 | *2 |
---|---|---|---|---|---|
 
```html
<div class="box">
    <div class="item" style="order: 1;">*1</div>
    <div class="item" style="order: 2;">*2</div>
    <div class="item">3</div>
    <div class="item">4</div>
    <div class="item">5</div>
    <div class="item">6</div>
</div>
```
### flex-grow 项目的放大比例
> flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。

> 如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。

> 如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍

> 如果项目已存在固定宽度，则按照比例瓜分剩余空间

1 | 2 | 2 | 3 | 3 | 3 |
---|---|---|---|---|---|

```html
<div class="box">
    <div class="item" style="flex-grow: 1;">1</div>
    <div class="item" style="flex-grow: 2;">2</div>
    <div class="item" style="flex-grow: 3;">3</div>
</div>
```
### flex-shrink 项目的缩小比例
> flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。

> 如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小

> 如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小。

> 负值对该属性无效。


1 | 1 | 2 | 2 | 2 | 3 |
---|---|---|---|---|---|

```html
<div class="box">
    <div class="item" style="flex-shrink: 1;">1</div>
    <div class="item" style="flex-shrink: 0;">2</div>
    <div class="item" style="flex-shrink: 3;">3</div>
</div>
```
### flex-basis 占据主轴的空间
> flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间（main size）

> 浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。

> 空间足够定义的值，大小则为定义值

1 | 1 | 2 | 2 | 3 | 3 | &nbsp; | &nbsp; |
---|---|---|---|---|---|---|---|

```html
<div class="box">
    <div class="item" style="flex-basis: 400px;">1</div>
    <div class="item" style="flex-basis: 400px;">2</div>
    <div class="item" style="flex-basis: 400px;">3</div>
</div>
```
### flex = flex-grow + flex-shrink + flex-basis
> flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。

> 该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)。建议优先使用这个属性，而不是单独写三个分离的属性。

> auto：均分的效果

> none: `inline-block`的效果

1 | 1 | 2 | 2 | 3 | 3 |
---|---|---|---|---|---|

```html
<div class="box">
    <div class="item" style="flex: auto;">1</div>
    <div class="item" style="flex: auto;">2</div>
    <div class="item" style="flex: auto;">3</div>
</div>
```
### align-self 单个项目的对齐方式
> align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。

> 默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。


```css
.item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```


1 | &nbsp; | 3 |
---|---|---|
 &nbsp; | &nbsp; | &nbsp; |
 &nbsp; | 2 | &nbsp; |
 
```html
<!--  align-items: flex-start; -->
<div class="box">
    <div class="item">1</div>
    <div class="item" style="align-self: flex-end;">2</div>
    <div class="item">3</div>
</div>
```

## 经典布局
1. 流式布局
    ![流式布局](/Image/flow.png)
2. 网格布局
    ![网格布局](/Image/grid.png)
3. 圣杯布局
    ![网格布局](/Image/holyGrail.png)
4. 输入框的布局
    ![圣杯布局](/Image/input.png)
5. 悬挂式布局
    ![悬挂式布局](/Image/media.png)
6. 骰子布局
    ![骰子布局](/Image/number.png)
7. 百分比布局
    ![百分比布局](/Image/precent.png)
8. 固定的底栏布局
    ![固定的底栏布局](/Image/stickyFooter.png)