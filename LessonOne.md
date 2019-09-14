markdown的语法教程：[原文链接](https://www.markdown.cn/#overview)

一个 Markdown 段落是由一个或多个连续的文本行组成，它的前后要有一个以上的空行（空行的定义是显示上看起来像是空的，便会被视为空行。比方说，若某一行只包含空格和制表符，则该行也会被视为空行）。普通段落不该用空格或制表符来缩进。

「由一个或多个连续的文本行组成」这句话其实暗示了 Markdown 允许段落内的强迫换行（插入换行符），这个特性和其他大部分的 text-to-HTML 格式不一样（包括 Movable Type 的「Convert Line Breaks」选项），其它的格式会把每个换行符都转成 ```<br /> ``` 标签。

如果你确实想要依赖 Markdown 来插入 ```<br />``` 标签的话，在插入处先按入两个以上的空格然后回车。

的确，需要多费点事（多加空格）来产生 ```<br />``` ，但是简单地「每个换行都转换为 ```<br />``` 」的方法在 Markdown 中并不适合， Markdown 中 email 式的区块引用和多段落的列表在使用换行来排版的时候，不但更好用，还更方便阅读。

# 标题 Title

Markdown 支持两种标题的语法

- 用底线的形式，利用 = （最高阶标题）和 - （第二阶标题），例如：

        ```
        这是 H1
        =============

        这是 H2
        -------------
        ```

    这是 H1
    =============

    这是 H2
    -------------

-
    - 在行首插入 1 到 6 个 # ，对应到标题 1 到 6 阶，例如：
        ```
        # 这是 H1

        ## 这是 H2

        ###### 这是 H6
        ```  
        # 这是 H1

        ## 这是 H2

        ###### 这是 H6

    - 你可以选择性地「闭合」类 atx 样式的标题，这纯粹只是美观用的，若是觉得这样看起来比较舒适，你就可以在行尾加上 #，而行尾的 # 数量也不用和开头一样（行首的井字符数量决定标题的阶数）：

        # 这是 H1 #

        ## 这是 H2 ##

        ### 这是 H3 ######
# 区块引用 Blockquote

- Markdown 标记区块引用是使用 > 符号。

```
> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
> consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
> Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
```

> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
> consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
> Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

- Markdown 也允许你偷懒只在整个段落的第一行最前面加上 > ：
```
> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
```

> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

- 区块引用可以嵌套（例如：引用内的引用），只要根据层次加上不同数量的 > 

``` This is the first level of quoting.
>
> > This is nested blockquote.
>
> Back to the first level.
```

 This is the first level of quoting.
>
> > This is nested blockquote.
>
> Back to the first level.

- 引用的区块内也可以使用其他的 Markdown 语法，包括标题、列表、代码区块等：

```
> ## 这是一个标题。
> 
> 1. 这是第一行列表项。
> 2. 这是第二行列表项。
> 
> 给出一些例子代码：
> 
>     return shell_exec("echo $input | $markdown_script");
```

> ## 这是一个标题。
> 
> 1. 这是第一行列表项。
> 2. 这是第二行列表项。
> 
> 给出一些例子代码：
> 
>     return shell_exec("echo $input | $markdown_script");

# 列表

- 无序列表使用星号(*)、加号(+)或是减号(-)作为列表标记：
    ```
    *   Red
    *   Green
    *   Blue
    ```
    *   Red
    *   Green
    *   Blue

    等同于：

    ```
    +   Red
    +   Green
    +   Blue
    ```
    +   Red
    +   Green
    +   Blue

    也等同于：
    ```
    -   Red
    -   Green
    -   Blue
    ```
    -   Red
    -   Green
    -   Blue

- 有序列表则使用数字接着一个英文句点：

    ```
    1.  Bird
    2.  McHale
    3.  Parish
    ```
    1.  Bird
    2.  McHale
    3.  Parish

    
    ```
    1.  Bird
    4.  McHale
    3.  Parish
    ```
    1.  Bird
    4.  McHale
    3.  Parish

# 代码块

但是好像使用 ``` 符号包裹起来更合适

和程序相关的写作或是标签语言原始码通常会有已经排版好的代码区块，通常这些区块我们并不希望它以一般段落文件的方式去排版，而是照原来的样子显示，Markdown 会用 ```<pre>``` 和 ```<code>``` 标签来把代码区块包起来。

要在 Markdown 中建立代码区块很简单，只要简单地缩进 4 个空格或是 1 个制表符就可以，例如，下面的输入：


```
/**
 * bfq_stat_add - add a value to a bfq_stat
 * @stat: target bfq_stat
 * @val: value to add
 *
 * Add @val to @stat.  The caller must ensure that IRQ on the same CPU
 * don't re-enter this function for the same counter.
 */

static inline void bfq_stat_add(struct bfq_stat *stat, uint64_t val) {
	percpu_counter_add_batch(&stat->cpu_cnt, val, BLKG_STAT_CPU_BATCH);
}
```

# 分隔线

```
* * *

***

*****

---

- - -

---------------------------------------
```

* * *

***

*****

---

- - -

---------------------------------------