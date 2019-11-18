# bk-vue-template

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Run your end-to-end tests
```
npm run test:e2e
```

### Run your unit tests
```
npm run test:unit
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).


项目知识点：
css网格布局：参考资料 http://www.ruanyifeng.com/blog/2019/03/grid-layout-tutorial.html
1、容器（container）:
容器属性：
display: grid | inline-grid;
grid-template-rows 定义每行的高度
grid-template-columns 定义每列的宽度
(1) fr 定义比例 如：grid-template-columns: 1fr 2fr;
(2) repeat(times, value) 重复属性值
(3) auto-fill 自动填充 如：grid-template-columns: repeat(auto-fill, 100px)
(4) minmax(min, max) 表示长度在min~max范围内
(5) auto 浏览器自己决定长度 如： grid-template-columns: 100px auto 100px
(6) [] 表示网格线的名字 如： grid-template-columns: [c1] 100px [c2] 100px [c3] 100px [c4]
(7) 布局实例
.wrap {
  display: grid;
  grid-template-columns: 30% 70%;
}

十二网格布局
.wrap {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
}
(8) grid-row-gap and grid-column-gap 分别表示行间距和列间距
grid-gap: <grid-row-gap> <grid-column-gap>

**最新标准该属性去掉前缀grid
(9) grid-template-areas 作用和表现？
可以在容器的每个项目上指定从区域的哪里开始和哪里结束
如：
grid-template-areas:  'a b c'
								      'd e f'
								      'g h i';

.item {
  grid-column-start: a;
  grid-column-end: c;
}
注意，区域的命名会影响到网格线。每个区域的起始网格线，会自动命名为区域名-start，终止网格线自动命名为区域名-end。

比如，区域名为header，则起始位置的水平网格线和垂直网格线叫做header-start，终止位置的水平网格线和垂直网格线叫做header-end。
（10）grid-auto-flow: 决定容器子元素的排列顺序，默认为row “先列后行”，可改为column
取值可为：row | column | row dense | column dense
dense表示尽可能填充空白区域
（11）justify-items  align-items  place-items 表示单元格内容的排列方式
.container {
  justify-items: start | center | end | stretch;
  align-items: start | center | end | stretch;
}

place-items: <align-items> <justify-items>

(12) justify-content align-content place-content 表示整个内容区域在容器中的排列方式
属性取值类似flex

(13) grid-auto-columns and grid-auto-rows
设置浏览器自动创建的多余的网格的列宽和行高。用法同grid-template-rows

(14) grid-template grid 前面属性的简写，建议少用。

2、项目（item）:
注：只有容器的直接子元素才是项目。
（1）grid-column-start
    grid-column-end
    grid-row-start
    grid-row-end
    指定项目启示和结束所在的**网格线位置**
属性取值可以是 span <number> 表示跨越几个网格
如 item {
  grid-column-start: span 2 // 表示项目的左边框距其有边框相距两个网格
}
**如果项目产生重叠，使用z-index确认顺序**

（2）grid-column: <grid-column-start> / <grid-column-end>
    grid-row: <grid-row-start> / <grid-row-end>

（3）grid-area
用法如下
item {
  grid-area: e;
}
或
item {
  grid-area: <grid-row-start> / <grid-column-start> / <grid-row-end> / <grid-row-end>
}

（4）justify-self  align-self  place-self
用法和justify-items align-items place-items完成相同，但只作用于一个单元格，用来设置该单元格
内容的水平或者垂直位置（上中下）
justify-self: start | center | end | stretch

place-self: <align-self> <justify-self>