#### 背景全屏模糊效果

1.父元素 

```
html,body {
	height:100%;
	overflow:hidden;
	margin:0;
	padding:0;
}
```

2.背景图元素

```
position:relative;
top:-50px;
left:-50px;
background:url(img.jpg) no-repeat center center;
background-size:100% 100%;
width:120%;
height:120%;
filter:blur(50px)
```

备注：

1.父元素首先要定义高度100%，超出隐藏，去边距

2.背景图元素要定义绝对定位：relative，减去要裁剪的白边尺寸，尺寸要超出父元素，以达到裁剪白边的效果



#### 父元素与子元素的百分比关系

当父元素不确定宽高值时，**父：百分比，子：固定值**，反之！

```
.paren{
	width:100%;
}
.son{
	width:100px;	//此时子元素占父元素的相对10%
}
```



#### 无宽高定位居中效果

让盒子居中显示，

```
.box{
	position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
    width: 100%;
    height:100%;
}
```

核心原理：