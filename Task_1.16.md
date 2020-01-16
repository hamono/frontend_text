## 主要做了QQ注册页（暂未完成）
### 收获

1. 加深了对`input`标签的理解。

```
<input
  tpye=""       //input元素的种类
  max/min=""    //输入字段的最大/最小值
  maxlength     //输入字段的最大长度
  size          //输入字段的宽度
  value         //input元素的值
>
```
`type`的一些常用可选值

|名称|含义|
|:-:|:--|
|text|定义单行的输入字段，用户可在其中输入文本。默认宽度为 20 个字符。|
|submit|定义提交按钮。提交按钮会把表单数据发送到服务器。|
|radio|定义单选按钮|
|password|定义密码字段。该字段中的字符被掩码。|
|reset|定义重置按钮。重置按钮会清除表单中的所有数据。|
|checkbox|定义复选框。复选框允许用户在一定数目的选择中选取一个或多个选项。|
2. [常用的表单](https://www.w3school.com.cn/tags/tag_input.asp)
3. `label`标签
    label 元素不会向用户呈现任何特殊效果。不过，它为鼠标用户改进了可用性。如果您在 label 元素内点击文本，就会触发此控件。就是说，当用户选择该标签时，浏览器就会自动将焦点转到和标签相关的表单控件上。

    包含两个属性`for`,`form`.
    |属性|含义|
    |:-:|:--|
    |for|规定 label 绑定到哪个表单元素。(id的值)|
    |form|规定 label 字段所属的一个或多个表单。|
4. `z-Index`属性

    `z-index `属性设置元素的堆叠顺序。拥有更高堆叠顺序的元素总是会处于堆叠顺序较低的元素的前面。

    直观的说：该属性设置一个定位元素沿 z 轴的位置，z 轴定义为垂直延伸到显示区的轴。如果为正数，则离用户更近，为负数则表示离用户更远。

    js语法：object.style.zIndex="1"。

    注：css属性中间带`-`的，在js中全部替换为小驼峰命名。
### 问题
1. 未解决

    函数的两种写法，造成了不同的结果。

  第一种：
```
    const labels=document.querySelectorAll("label");

    for (let i = 0; i < labels.length; i++) {
      labels[i].onclick = function (e) {
        e.target.style.display="none";
      }
    }
```
第二种：
```
    const labels=document.querySelectorAll("label");
    function changeStyle(name){
          name.style.display="none";
        }
    for (let i = 0; i < labels.length; i++) {
          labels[i].onclick =changeStyle(labels[i]);
    }
```
  第一种在点击`label`后产生相应效果，第二种在刷新后直接产生效果（与预期不符）。