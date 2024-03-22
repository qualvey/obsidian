# 字体样式属性  

CSS 字体属性主要包括：`字体设置(font-family)`、`字号大小(font-size)`、`字体粗细(font-weight)`、`字体风格(font-style)`、`字体颜色(color)`。

###### font-family:
1. 英文字体不需要加引号。
2. 字体名称包含特殊字符需要加引号，比如空格{font-family:"Microsoft yahei";}


##### font简写
```
{font: font-style font-weight font-size/line-height font-family;}
```

size和family必须指定，其他可以跳过。





# 文本样式属性  

CSS外观属性包含：`行间距(line-height)`、`水平对齐方式(text-align)`、`首行缩进(text-indent)`、`文本的装饰(text-decoration)`

1em就是一个字的宽度

# 选择器  
1. 并集选择器
2. 交集选择器
3. 相邻兄弟选择器
4.  属性选择器
		attr=v               唯一等于
			attr~=v       包含
			attr|=v         包含v-开头
			
		    



# 优先级涉及到计算
内联style拥有最高优先级  
##### 一个选择器的优先级可以说是由三个不同的值（或分量）相加，可以认为是百（ID）十（类）个（元素）——三位数的三个位数：

- **ID**：选择器中包含 ID 选择器则百位得一分。
- **类**：选择器中包含类选择器、属性选择器或者伪类则十位得一分。
- **元素**：选择器中包含元素、伪元素选择器则个位得一分。

**备注：** 通用选择器（[`*`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Universal_selectors)）、组合符（`+`、`>`、`~`、' '）和调整优先级的选择器（[`:where()`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:where)）不会影响优先级。
下面是一些例子： 

| 选择器                                       | ID  | 类   | 元素  | 优先级   |
| ----------------------------------------- | --- | --- | --- | ----- |
| `h1`                                      | 0   | 0   | 1   | 0-0-1 |
| `h1 + p::first-letter`                    | 0   | 0   | 3   | 0-0-3 |
| `li > a[href*="en-US"] > .inline-warning` | 0   | 2   | 2   | 0-2-2 |
| `#identifier`                             | 1   | 0   | 0   | 1-0-0 |
| `button:not(#mainBtn, .cta)`              | 1   | 0   | 1   | 1-0-1 |

样式化表单
