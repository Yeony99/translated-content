---
title: Flow Layout and Writing Modes 流布局和书写模式
slug: Web/CSS/CSS_Flow_Layout/Flow_Layout_and_Writing_Modes
---
The CSS 2.1 specification, which details how normal flow behaves, assumes a horizontal writing mode. [Layout](/zh-CN/docs/Web/CSS/CSS_Flow_Layout/Block_and_Inline_Layout_in_Normal_Flow) properties should work in the same way in vertical writing modes. In this guide, we look at how flow layout behaves when used with different document writing modes.
CSS 2.1 规范详细描述了正常流的行为，它采用了水平写入模式。布局属性在垂直写入模式中的工作方式应该相同。在本指南中，我们将研究流布局在与不同的文档写入模式一起使用时的行为。

This is not a comprehensive guide to the use of writing modes in CSS, the aim here is to document the areas where flow layout interacts with writing modes in possibly unanticipated ways. The [external resources](#External_Resources) and [see also](#See_Also) sections of this document link to more writing modes resources.
这不是 CSS 中书写模式使用的全面指南，这里的目的是以可能未预料到的方式记录流布局与书写模式交互的区域。外部资源，请参阅本文档的章节，链接到更多写作模式资源。

## The Writing Modes Specification<br>书写模式规范

The CSS Writing Modes Level 3 Specification defines the impact a change the document writing mode has on flow layout. In the writing modes introduction, [the specification says](https://drafts.csswg.org/css-writing-modes-3/#text-flow),
CSS 编写模式级别 3 规范定义了文档编写模式更改对流布局的影响。在书写模式介绍中，规范说：

> “A writing mode in CSS is determined by the {{cssxref("writing-mode")}}, {{cssxref("direction")}}, and {{cssxref("text-orientation")}} properties. It is defined primarily in terms of its inline base direction and block flow direction.”
> “CSS 中的书写模式由书写模式、方向和文本方向属性决定。它主要是根据其内联基础方向和块流方向来定义的。”

The specification defines the _inline base direction_ as the direction in which content is ordered on a line. This defines the start and end of the inline direction. The start is where sentences start and the end is where a line of text ends before it would begin to wrap onto a new line.
规范将内联基方向定义为内容在行上的排序方向。这定义了内联方向的开始和结束。开始是句子开始的地方，结束是一行文本在开始换行之前结束的地方。

The _block flow direction_ is the direction in which boxes, for example paragraphs, stack in that writing mode. The CSS writing-mode property controls the block flow direction. If you want to change your page, or part of your page, to `vertical-lr` then you can set `writing-mode: vertical-lr` on the element and this will change the direction of the blocks and therefore the inline direction as well.
块流方向是框（例如段落）以该写入模式堆叠的方向。CSS 写入模式属性控制块流方向。如果要将页面或页面的一部分更改为垂直 lr，则可以在元素上设置书写模式：垂直 lr，这将更改块的方向，因此也会更改内联方向。

While certain languages will use a particular writing mode or text direction, we can also use these properties for creative effect, such as running a heading vertically.
虽然某些语言将使用特定的书写模式或文本方向，但我们也可以使用这些属性来产生创造性效果，例如垂直运行标题。

{{EmbedGHLiveSample("css-examples/flow/writing-modes/creative-use.html", '100%', 720)}}

## The `writing-mode` property and block flow<br>写入模式属性和块流

The {{cssxref("writing-mode")}} property accepts the values `horizontal-tb`, `vertical-rl` and `vertical-lr`. These values control the direction that blocks flow on the page. The initial value is `horizontal-tb`, which is a top to bottom block flow direction with a horizontal inline direction. Left to right languages, such as English, and Right to left languages. such as Arabic, are all `horizontal-tb`.
写入模式属性接受值水平 tb、垂直 rl 和垂直 lr。这些值控制阻止页面流动的方向。初始值是水平 tb，这是一个顶部到底部的块流方向，具有水平的内联方向。从左到右的语言，如英语和从右到左的语言。如阿拉伯语，都是水平结核。

The following example shows blocks using `horizontal-tb`.
下面的示例显示了使用水平 TB 的块。

{{EmbedGHLiveSample("css-examples/flow/writing-modes/horizontal-tb.html", '100%', 720)}}

The value `vertical-rl` gives you a right-to-left block flow direction with a vertical inline direction, as shown in the next example.
值 vertical rl 为您提供了一个从右到左的块流方向和一个垂直的内联方向，如下一个示例所示。

{{EmbedGHLiveSample("css-examples/flow/writing-modes/vertical-rl.html", '100%', 720)}}

The final example demonstrates the third possible value for `writing-mode` — `vertical-lr`. This gives you a left-to-right block flow direction and a vertical inline direction.
最后一个示例演示了第三个可能的写入模式值 - 垂直 lr。这将为您提供一个从左到右的块流方向和一个垂直的内联方向。

{{EmbedGHLiveSample("css-examples/flow/writing-modes/vertical-lr.html", '100%', 720)}}

## Boxes with a different writing mode to their parent<br>对父级具有不同写入模式的框

When a nested box is assigned a different writing mode to its parent, then an inline level box will display as if it has `display: inline-block`.
当一个嵌套框被分配给它的父级的不同的写入模式时，一个内联级别的框将显示，就好像它有 display:inline 块一样。

{{EmbedGHLiveSample("css-examples/flow/writing-modes/inline-change-mode.html", '100%', 720)}}

A block-level box will establish a new block formatting context, meaning that if its inner display type would be `flow`, it will get a computed display type of `flow-root`. This is shown in the next example where the box which displays as `horizontal-tb` contains a float which is contained due to its parent establishing a new BFC.
块级别的框将建立一个新的块格式上下文，这意味着如果其内部显示类型为“流”，则它将获得“流根”的计算显示类型。这在下一个示例中显示，其中显示为水平 tb 的框包含一个浮动，该浮动是由于其父级建立了一个新的 bfc 而包含的。

{{EmbedGHLiveSample("css-examples/flow/writing-modes/block-change-mode.html", '100%', 720)}}

## Replaced elements 更换的元件

Replaced elements such as images will not change their orientation based on the `writing-mode` property. However, replaced elements such as form controls which include text, should match the writing mode in use.
替换的元素（如图像）不会根据“写入模式”属性更改其方向。但是，替换的元素（如包含文本的表单控件）应与使用中的写入模式匹配。

{{EmbedGHLiveSample("css-examples/flow/writing-modes/replaced.html", '100%', 720)}}

## Logical Properties and Values<br>逻辑属性和值

Once you are working in writing modes other than `horizontal-tb` many of the properties and values that are mapped to the physical dimensions of the screen seem strange. For example, if you give a box a width of 100px, in `horizontal-tb` that would control the size in the inline direction. In `vertical-lr` it controls the size in the block direction because it does not rotate with the text.
一旦您在编写模式（而不是水平 tb）时，许多映射到屏幕物理维度的属性和值看起来很奇怪。例如，如果为一个框提供 100px 的宽度，以水平 tb 表示，它将控制内联方向的大小。在垂直 lr 中，它控制块方向的大小，因为它不随文本旋转。

{{EmbedGHLiveSample("css-examples/flow/writing-modes/width.html", '100%', 720)}}

Therefore, we have new properties of {{cssxref("block-size")}} and {{cssxref("inline-size")}}. If we give our block an `inline-size` of 100px, it doesn’t matter whether we are in a horizontal or a vertical writing mode, `inline-size` will always mean the size in the inline direction.
因此，我们有了块大小和内联大小的新属性。如果我们给块一个 100px 的内联大小，不管我们是处于水平还是垂直写入模式，内联大小总是指内联方向的大小。

{{EmbedGHLiveSample("css-examples/flow/writing-modes/inline-size.html", '100%', 720)}}

The [CSS Logical Properties and Values](/zh-CN/docs/Web/CSS/CSS_Logical_Properties) specification includes logical versions of the properties that control margins, padding and borders as well as other mappings for things that we have typically used physical directions to specify.
CSS 逻辑属性和值规范包括用于控制页边距、填充和边框的属性的逻辑版本，以及用于我们通常使用物理方向指定的内容的其他映射。

## Summary 总结

In most cases, flow layout works as you would expect it to when changing the writing mode of the document or parts of the document. This can be used to properly typeset vertical languages or for creative reasons. CSS is making this easier by way of introducing logical properties and values so that when working in a vertical writing mode sizing can be based on element's inline and block size. This will be useful when creating components which can work in different writing-modes.
在大多数情况下，流程布局的工作方式与您在更改文档或文档部分的写入模式时所期望的一样。这可以用于正确排版垂直语言或出于创造性的原因。CSS 通过引入逻辑属性和值使这变得更容易，这样在垂直写入模式下工作时，大小调整可以基于元素的内联和块大小。这在创建可以在不同写入模式下工作的组件时很有用。

## See Also 另请参见

- [Writing Modes](/zh-CN/docs/Web/CSS/CSS_Writing_Modes)

## External Resources 外部资源

- _[CSS Writing Modes](https://24ways.org/2016/css-writing-modes/)_, Jen Simmons on 24 Ways

{{QuickLinksWithSubpages("/en-US/docs/Web/CSS/CSS_Flow_Layout/")}}
