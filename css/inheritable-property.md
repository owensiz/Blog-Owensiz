# css中可继承的属性

## 注意

虽然不可继承的属性很多，但可继承的属性容易记忆。
只有颜色，文字，字距，行高，对齐方式，和列表的样式可以继承。


所有元素可继承：visibility和cursor。
内联元素可继承：
letter-spacing、word-spacing、white-space、line-height、color、
font、font-family、font-size、font-style、font-variant、font-weight、text-decoration、text-transform、direction。
终端块状元素可继承：text-indent和text-align。
列表元素可继承：list-style、list-style-type、list-style-position、list-style-image。


  1、字体系列属性

        font：组合字体

        font-family：规定元素的字体系列

        font-weight：设置字体的粗细

        font-size：设置字体的尺寸

        font-style：定义字体的风格

        font-variant：设置小型大写字母的字体显示文本，这意味着所有的小写字母均会被转换为

        大写，但是所有使用小型大写字体的字母与其余文本相比，其字体尺寸更小。

        font-size-adjust：为某个元素规定一个 aspect 值，字体的小写字母 "x" 的高度与

        "font-size" 高度之间的比率被称为一个字体的 aspect 值。这

        样就可以保持首选字体的 x-height。

2、文本系列属性

        text-indent：文本缩进

        text-align：文本水平对齐

        line-height：行高

        word-spacing：增加或减少单词间的空白（即字间隔）

        letter-spacing：增加或减少字符间的空白（字符间距）

        text-transform：控制文本大小写

        direction：规定文本的书写方向

        color：文本颜色

  3、元素可见性：visibility

  4、表格布局属性：caption-side、border-collapse、border-spacing、

        empty-cells、table-layout

  5、列表属性：list-style-type、list-style-image、list-style-position、list-style

  6、生成内容属性：quotes

  7、光标属性：cursor

  8、页面样式属性：page、page-break-inside、windows、orphans

  9、声音样式属性：speak、speak-punctuation、speak-numeral、speak-header、

        speech-rate、volume、voice-family、pitch、pitch-range、

        stress、richness、、azimuth、elevation