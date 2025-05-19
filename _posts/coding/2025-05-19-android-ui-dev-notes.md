---
title: Android视图层编程笔记
category: coding
tags: android ui
published: true
---
19/05/2025 Android UI编程笔记

## 如何为Android应用创建视图布局

### 0. 创建视图布局的大致思路

1. 使用layout组件进行视图布局
2. 使用`layout_margin`控制视图间距
3. 使用`layout_width`和`layout_height`控制视图宽度和高度
4. 使用`layout_weight`控制多个视图间的大小比例

### 1. 使用layout组件进行视图布局

- 简单布局可以通过嵌套`LinearLayout`(horizontal or vertical)来实现；
- 复杂布局可以使用`ConstraintLayout`。

### 2. 使用layout_margin控制视图间距

- 在layout组件内设置`layout_margin`可以为所有子组件与父组件间提供外边距；
- 如果希望在水平布局的组件间增加间距，可以在靠后的组件上添加`layout_marginStart`（相比于`layout_marginLeft`对RightToLeft语言的支持更好）。

### 3. 使用`layout_width`和`layout_height`控制视图宽度和高度

如果希望组件占满整个布局空间的宽度或者高度，可以将组件的`layout_width` / `layout_height`设置为`match_parent`；
如果希望组件仅仅占有自身所需宽度或者高度，可以将组件的`layout_width` / `layout_height`设置为`wrap_content`。

### 4. 使用`layout_weight`控制多个视图组件在间的大小比例

在决定子组件视图的宽度时，`LinearLayout`使用的是`layout_width`与`layout_weight`参数的混合值。

`LinearLayout`是分两个步骤来设置视图宽度的。

- 第一步，LinearLayout查看layout_width属性值(竖直方位则查看layout_height属性值)。

![f60b6edb28f028e15f12ce3faab9bd17.png](:/5e91eb8d2c404d6c928fd19c83d3ec07)

- 第二步，LinearLayout依据layout_weight属性值进行额外的空间分配。

![ef8a860b314d12cc4501017662f034b1.png](:/a91db0d18d84416cabe786a70e5b6ad5)

`layout_weight`代表该视图组件在其父组件的布局空间中所占有的权重，例如，如果A组件的`layout_weight`为2，B组件的`layout_weight`为1，则A将获得父组件2/3的额外宽度，而B则将获得父组件1/3的额外宽度。

![b3bc1d8d77be7269c8517fdf11aeb1e7.png](:/d3fe22869ec944f99c82b772430c5983)

weight设置值也可以是浮点数。一种常见的设定方式是各组件属性值加起来等于1.0或100。比如，在上一个例子中，A组件的`layout_weight`应该为0.66，B组件的`layout_weight`则为0.37。

如想让`LinearLayout`分配完全相同的宽度给各自的视图，则只需设置各组件的`layout_width`属性值为0dp以避开第一步的空间分配就可以了。这样`LinearLayout`就会只考虑使用`layout_weight`属性值（而忽视组件自身的宽度）来完成所需的空间分配。

![63324cfb92395d51ac565a89e6cb98fc.png](:/c521f3fb6af344dbb7f7ebdc7b88ab5c)

注意，如果不小心将某个组件的layout_weight`设置为1，可能会导致该组件占满整个布局空间，导致其他组件在UI中不可见。

### 5. 例子：创建以下布局

![cdd3650630b74c2de0c65408f611533b.png](:/0c2aad541dce4f6f9aa6e9e034efc028)

所需步骤如下：

1. 添加1个Layout(vertical)组件；
2. 在Layout(vertical)组件内添加所需的视图元素，以及1个Layout(horizontal)组件（将Save和Clear按钮置于其中，以对其进行水平布局）；
3. 将Layout(vertical)的`layout_margin`设置为15dp，为所有子组件提供距离屏幕边框15dp的外边距；
4. 将Clear按钮的`layout_marginStart`设置为30dp，以在两个按钮间提供30dp的间距；
5. 将StudentName和StudentEmail的layout_width设置为`match_parent`以占满水平宽度；
6. Layout(horizontal)默认将Save和Clear按钮的`layout_weight`设置为1，因此2个按钮占据相等的水平宽度。