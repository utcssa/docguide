# Markdown 风格指南

Markdown 的伟大之处很大程度在于它能够通过编写纯文本并获得优美的格式化输出。文档的本质在于协作共建，为了给协作者一个干净的环境，你写的 Markdown 应该尽可能简单并且维持一个统一的语料库。

我们力求平衡三个目标：

1. *源文本具有可读性和可移植性。*
2. *Markdown 文件保持可维护性，不论时间或是跨团队的情形。*
3. *语法简单、易记忆。*

## 文档布局

一般来说，大多数文档都受益于以下布局的某种变体：

```markdown
# 文档标题

简短的介绍。

## 话题

内容。

## 另见

- https://link-to-more-info
```

1. `# 文档标题`：第一个标题应该是一个一级标题，并且最好与文件名相同或几乎相同。第一个一级标题被用作页面的 `<title>`
1. `作者`：*可选*。如果你想对该文档宣称所有权或是对它感到非常自豪，可以在文档标题下加上你自己的名字。然而，修订历史通常就包含这些信息了。
1. `简短的介绍。`：用 1-3 句话对该主题进行高层级的概述。想象一下，一个完全陌生的人读到你的文档「办理 I-20」，需要知道你认为理所当然的最基本的假设：「I-20 是什么？我为什么要办理它？」。
1. `## 话题`：除了第一个标题以外，其余的标题应该从二级开始。
1. `## 另见`：为想了解更多信息或没有找到所需内容的用户在底部放置杂项链接。

## 行尾空白

请勿使用行尾空白来换行，使用行尾反斜线（`\`）。原因暂不翻译：

> The [CommonMark spec](http://spec.commonmark.org/0.20/#hard-line-breaks) decrees that two spaces at the end of a line should insert a `<br />` tag. However, many directories have a trailing whitespace presubmit check in place, and many IDEs will clean it up anyway.
>
> Best practice is to avoid the need for a `<br />` altogether. Markdown creates paragraph tags for you simply with newlines: get used to that.

## 标题

### ATX 风格标题

```markdown
## 二号标题
```

带有 `=` 或 `-` 下划线的标题维护起来很麻烦，而且与标题的其他语法不相容。`---` 是指一级标题还是二级标题令人感到疑问。

```markdown
标题 - 你记得这是几级标题吗？别这么做！
---------
```

### 向标题加入空白

在 `#` 后加入空格，并在标题行前后加入空行：

```markdown
…前面的文字

# 一级标题

后面的文字…
```

缺少空格和空行降低了源文本的可读性：

```markdown
…前面的文字

#一级标题
后面的文字… 别这么做！
```

## 列表

### 对长列表使用「懒编号」

Markdown 足够智能，可以渲染出正确呈现编号列表的 HTML。\
对于可能发生变化的较长的列表，特别是长的嵌套列表，使用「懒编号」：

```markdown
1. 歪比巴卜
1. 阿巴阿巴
  1. 阿巴阿巴阿巴阿巴
  1. 歪比巴卜歪比巴卜
1. 叽里呱啦
```

如果列表很小而且不太可能变化，则建议使用全编号的列表，因为它的源文本可读性更好：

```markdown
1. 歪比巴卜
2. 阿巴阿巴
3. 叽里呱啦
```

### 不用星号（*）开始项目列表

因为 `*` 在 Markdown 中有其他用途，为避免歧义，请用 `-` 开始项目列表：

```markdown
* 不要使用这种列表

- 请使用减号开始项目列表
```

### 嵌套列表的缩进

不论编号列表还是项目列表：

- 在嵌套列表时使用 2 格缩进
- 列表编号后跟 1 个空格

```markdown
- 歪比巴卜
  - 阿巴阿巴
    - 叽里呱啦

1. 歪比巴卜
  1. 阿巴阿巴
```

## 代码

### 行内代码

&#96;反引号&#96;（译者注：该符号按键通常在 <kbd>Esc</kbd> 键下方）用作 `行内代码`，并会渲染所有被其包裹的内容，把他们用作简短的代码或是字段名称：

用例：包裹文件名

```markdown
记得更新你的 `README.md`！
```

反引号也是转义 Markdown 元字符最常用的方法。

### 代码块

对于超过一行的代码，使用代码块：

<pre>
```python
def main():
    print('Hello World')
```
</pre>

#### 声明语言

最佳实践是明确声明语言，这样语法高亮器和其他编辑者都不需要猜测这是什么语言。

#### 将代码块嵌套在列表中

如果你需要在列表中置入一个代码块，请确保给它缩进以防打断列表：

```markdown
- 一个列表项

    ```c++
    int foo;
    ```

- 另一个列表项
```

## 链接

长链接破坏了 Markdown 源文本的可读性，**尽可能缩短链接**。

### 不使用空洞的 Markdown 链接标题

Markdown 链接语法允许你为链接设置一个标题。当你将链接命名为「链接」或是「这里」时，读者在快速浏览时无法准确知道任何信息，也很浪费空间：

```markdown
查看语法指南以获取更多信息：[链接](syntax_guide.md)。
或者，在 [这里](style_guide.md) 查看风格指南。

别这么做！
```

相反，你应该自然地写出这句话，然后回去用链接包住最合适的短语：

```markdown
查看 [语法指南](syntax_guide.md) 以获取更多信息。
或者，看看 [风格指南](style_guide.md)。
```

## 图片

尽量少用图片，最好只用简单的屏幕截图。本指南的设计理念是：纯文本能让用户更快地进入交流的状态，减少读者的注意力和作者的拖延。当然，可以配上能够帮助你传达和梳理信息的图片。

## 建议用列表替换表格

Markdown 中所配的表格应尽可能小。复杂的大型表格在源文本中难以阅读，最重要的是也**难以修改**。

```markdown
水果 | 属性 | 备注
--- | --- | --- | ---
苹果 | [多汁](https://example.com/SomeReallyReallyReallyReallyReallyReallyReallyReallyLongQuery)，紧实，甜 | 一天一苹果，医生远离我。
香蕉 | [方便](https://example.com/SomeDifferentReallyReallyReallyReallyReallyReallyReallyReallyLongQuery)，软，甜 | 与流行的看法相反，大多数猿猴其实更喜欢吃芒果。

别这么做
```

[列表](#列表) 和子标题通常足够用于展示相同的信息——以一种不那么紧凑但是对编辑更加友好的形式：

```markdown
## 水果

### 苹果

* [多汁](https://SomeReallyReallyReallyReallyReallyReallyReallyReallyReallyReallyReallyReallyReallyReallyReallyReallyLongURL)
* 紧实
* 甜

一天一苹果，医生远离我。

### Banana

* [方便](https://example.com/SomeDifferentReallyReallyReallyReallyReallyReallyReallyReallyLongQuery)
* 软
* 甜

与流行的看法相反，大多数猿猴其实更喜欢吃芒果。
```

## 强烈建议用 Markdown 代替 HTML

请尽可能选择标准的Markdown语法，避免使用 HTML Hack。如果你无法完成你想要的东西，请重新考虑你是否真的需要它。除了大的表格，Markdown 已经满足了几乎所有的需求。

每一点 HTML 或 Javascript Hack 都会降低 Markdown 的可读性和可移植性。这反过来又限制了 Markdown 与其他工具的整合，因为这些工具可能会将源文本呈现为纯文本，也有可能将其渲染。参见「[指导思想](philosophy.md)」。
