# Safari Translate 网页对照翻译

最理想的网页翻译效果，恐怕就是一段原文一段译文，如此既不妨碍阅读，也能够对照原文，避免错漏。专于这一功能的工具偶有复现，但要么难以为继，要么转为封闭的软件并且坐收买路钱（在此就不点名了，毕竟挣钱并不寒碜）。本方案将“对照”和“翻译”分开，模块化操作，更为鲁棒。

- 1.0：原始版本；
- 1.1：由会员 @Felz33 修改，可以保留原始文本的样式；
- 1.2：适配了部分论坛，比如 Zettelkasten forum；
- 1.3：适配了 XHTML 文件，可以翻译某些网站下载的 EPUB 和论文了。

系列文章：

- [《一种几乎永不失效的网页中英对照翻译方案》](https://utgd.net/article/4991)：最基础的对照翻译方案，支持网页和 HTML/XHTML 文件，是下面所有方案的基础。
- [《用 Safari 翻译外文电子书和文档》](https://utgd.net/article/6901)：对照翻译电子书，输出双语 PDF 或 Word 文档，目前该方案已经被下一项取代，毕竟你可以随时把 EPUB 转换成 PDF，但不能反过来操作。
- [《将外文电子书翻译成双语对照版本，并在任何设备上阅读》](https://utgd.net/article/10001)：对照翻译电子书，输出双语 EPUB，已经取代输出 PDF 的旧方案。
- [《在 DEVONthink 中对照翻译外文 Newsletter》](https://utgd.net/article/10005)：在 DEVONthink 中翻译 Newsletter。
- [《UNTAG Premium 第九期》](https://utgd.net/article/9628)：适配了部分论坛页面。
- [《UNTAG Premium 年度特辑 01》](https://utgd.net/article/9760)：全文翻译 DEVONthink 中的 RSS 文章（前提是你订阅的 RSS 源了你全文）。

为方便没有 Keyboard Maestro 的读者，下面也提供 Bookmarklet 版本源代码。Bookmarklet 仅负责“对照”，不负责“翻译”，“翻译”需要使用各个浏览器自带的翻译功能，或者使用翻译插件。我仅测试了 Safari、Chrome、Firefox 和 Edge 的自带翻译功能（20230226），没有精力一一测试其他软件，插件更是一个都没有测过，有需要的请自行测试。

```
javascript:var%20%24jscomp%3D%24jscomp%7C%7C%7B%7D%3B%24jscomp.scope%3D%7B%7D%3B%24jscomp.arrayIteratorImpl%3Dfunction(a)%7Bvar%20d%3D0%3Breturn%20function()%7Breturn%20d%3Ca.length%3F%7Bdone%3A!1%2Cvalue%3Aa%5Bd%2B%2B%5D%7D%3A%7Bdone%3A!0%7D%7D%7D%3B%24jscomp.arrayIterator%3Dfunction(a)%7Breturn%7Bnext%3A%24jscomp.arrayIteratorImpl(a)%7D%7D%3B%24jscomp.makeIterator%3Dfunction(a)%7Bvar%20d%3D%22undefined%22!%3Dtypeof%20Symbol%26%26Symbol.iterator%26%26a%5BSymbol.iterator%5D%3Breturn%20d%3Fd.call(a)%3A%24jscomp.arrayIterator(a)%7D%3B(function()%7Bfunction%20a(b)%7B%22img%22%3D%3D%3Db.nodeName.toLowerCase()%26%26b.parentElement.removeChild(b)%3Bb.setAttribute(%22translate%22%2C%22no%22)%3Bb.setAttribute(%22class%22%2Cb.getAttribute(%22class%22)%2B%22%20notranslate%22)%3Bb%3D%24jscomp.makeIterator(b.children)%3Bfor(var%20e%3Db.next()%3B!e.done%3Be%3Db.next())a(e.value)%7Dfor(var%20d%3D%24jscomp.makeIterator(document.querySelectorAll(%22li%3Anot(%3Ahas(p))%2C%20div%3Anot(%3Ahas(div%2C%20p))%2C%20p%2C%20h1%2C%20h2%2C%20h3%2C%20h4%22))%2Cc%3Dd.next()%3B!c.done%3Bc%3Dd.next())if(c%3Dc.value%2C%22no%22!%3D%3Dc.getAttribute(%22translate%22))%7Bvar%20f%3Dc.cloneNode(!0)%3Bc.parentElement.insertBefore(f%2Cc.nextElementSibling)%3Ba(c)%7D%7D)()%3Bvoid+0
```

![title](img.png)

如您对左右分屏翻译感兴趣，可以查看我的另一个项目 [Safari Translate V](https://github.com/BlackwinMin/Keyboard-Maestro-gallery/tree/master/Safari%20Translate%20V)——其实不限于 Safari，基本任何浏览器都可以。