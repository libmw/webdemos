---
  layout: api
  title: HTML
---

## MDN之learn篇


# html

## [html基本](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started)

HTML5重定义了元素分类，不通过block和inline来划分。

empty element结尾没必要再打斜杠

disabled这种布尔属性，即使写值，也仅有一个值，就是本身，所以通常不用写值

属性的值可以是单引号、双引号、无引号

对于空格，不管你打多少个，浏览器只显示一个，除非加pre标签

## [metadata](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML)

keywords不再被搜索引擎支持，因为这个东西完全可以和页面实际内容不符，搜索引擎不是傻逼对吧？

对于lang属性，可以让搜索引擎更快速的分析文档，也可以让读屏软件正确的读取，但是对于中文，应该用处不是很大

## [链接](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks)

对于链接的最佳实践：文字应该让用户明白点击后会跳转到哪里、不要让相同文字的链接连接到不同地方防止读屏困难、尽量使用相对路径(代码更加易读，浏览器不需要在解析域名)、链接到文件的时候说明文件大小和类型

对于mailto，可以用cc、bcc、title、subject

## [文本包裹](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting)

dl代表描述列表，dt代表描述项，dd代表描述定义，一个dt应该只对应一个dd才对

对于时间，我们应该用time标签加datetime属性包裹，方便机器识别

对于缩略词，我们应该用abbr标签加title属性包裹

## [图片包裹](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML)

使用figure和figcaption标签对图片进行包裹和说明，但是figure标签不仅仅包裹图片，也包裹视频

## [视频音频](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content)

使用track标签可以原生显示字幕，字幕还可以指定语言

## [iframe](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies)

iframe: https可以防止iframe访问父https页面，反之亦然，所以使用https后的站点是不能通过iframe访问的

通过sandbox我们可以阻止ifram里面的网页执行script、弹出窗口等等

## [表格](https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_boxes/Styling_tables)

table: table需要用了table-layout:fixed，才会认设置的宽度，否则table会根据内容自适应，给table或者td设置宽度也无效

关于这个属性，有专门的文章探讨：https://css-tricks.com/fixing-tables-long-strings/

colgroup和col结合可以定义每一列的样式，但是现在来看css3完全可以解决这个问题了。

tbody总是存在的，即使你在代码里不写，浏览器也会自动加上。

对于视力障碍的table优化：使用th来定义表头，对th使用scope来指定此表头代表的列(col)还是行(row)，或者列集合(colgroup)/行集合(rowgroup)。还可以使用id和headers替代本方案，但是过于复杂，一般不做推荐。

## `WebSockets`

[WebSockets同源策略](https://www.christian-schneider.net/CrossSiteWebSocketHijacking.html)

由于WebSockets不遵循同源策略，而WebSockets在第一次握手的时候是使用的http/s协议，会携带cookie信息，所以：
WebSockets如果后端鉴权没做好，会导致较为严重的安全问题。后端在建立连接的时候不应该使用cookie鉴权，并应该鉴定Origin头部字段

## `表单`

[form-data](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Sending_and_retrieving_form_data)

multipart/form-data的意思是传输的内容被分成多个部分，文件和文本分成不同的部分传输，因为http是基于文本的协议，所以必须指定为form-data才能传输文件

对于Xss，在输出内容到前端的时候默认应该把内容里的特殊符号都进行转义，除非是富文本。对于csrf，应该在form提交的时候带上token

[表单验证](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Form_validation)

可以使用:valid和:invalid伪类对表单进行验证通过和不通过的样式展现。 浏览器api也提供了丰富的原生valid功能如validationMessage、validity.valid等。表单也有checkValidity、setCustomValidity等方法

[自定义表单](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/How_to_build_custom_form_widgets)

对于自定义的表单，可以使用role属性来使tab有用，这样增强了访问性。比如表示select的div的role为rolebox，option的role为option

[手动构造formdata](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Sending_forms_through_JavaScript)

手动构造formdata，可以用字符串拼接任意形式的formdata，然后用xhr.send方法发送，formdata的格式和chrome调试工具里的字符串格式一致。

[浏览器兼容](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/HTML_forms_in_legacy_browsers)

查找兼容性除了can i use，还有quirks mode等网站

[各个表单的可设置属性](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Property_compatibility_table_for_form_widgets)

这个列表里有不同的表单元素对不同的css属性浏览器的支持情况。

## [页面focus](https://developer.mozilla.org/en-US/docs/Web/API/Document/hasFocus)

var focused = document.hasFocus(); 可以检测当前的页面是否被聚焦

## [页面可见性](https://developer.mozilla.org/en-US/docs/Web/API/Page_Visibility_API)

通过document的onvisibilitychange事件和判断hidden/visibilityState属性来判断当前页面是否被因此，从而暂停一些功能如视频播放、幻灯片等

## `音视频格式`

浏览器的video和audio标签对音视频格式的支持是有限的，参考[此表](https://developer.mozilla.org/en-US/docs/Web/HTML/Supported_media_formats)

## `分类`

传统对标签分类一般分为inline和block两大类，但是[新式的分类](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Content_categories)却不是按照这样来分。

## `MIME type`

[Multipurpose Internet Mail Extensions](https://developer.mozilla.org/en-US/docs/Glossary/MIME_type)意为多功能Internet邮件扩展，它设计的最初目的是为了在发送电子邮件时附加多媒体数据，让邮件客户程序能根据其类型进行处理。然而当它被HTTP协议支持之后，它的意义就更为显著了。它使得HTTP传输的不仅是普通的文本，而变得丰富多彩。
每个MIME类型由两部分组成，前面是数据的大类别，例如声音audio、图象image等，后面定义具体的种类。

## `颜色`

可以通过[caret-color](https://developer.mozilla.org/en-US/docs/Web/CSS/caret-color)改变光标的颜色