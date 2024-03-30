# PDF Paginate PDF加页码

macOS 是能加页码的小工具屈指可数。2023 年年底，我使用多年的 pdfPaginatePro 也在转向 iOS 套壳软件后，卡到几乎无法使用，像是开了一个套了十层的虚拟机，最终我还是将其卸载，并另寻出路。直接的产物就是本方案。

通过 GUI Scripting，在 Preview 中给 PDF 加页码。几乎可移植到任何能批注 PDF 的软件中。

【使用须知】本动作仅适用于英文系统，中文系统请根据提示修改。请将 Select “Next Item” in the Menu “Go” in Preview 步骤中的菜单栏项目更换在您电脑实际显示的项目路径及名称。

【已知问题】本动作需模拟点击鼠标，若正好点到 PDF 中的链接——常见于有带链接图片的 PDF——则动作将取消运行。

原文：[《Keyboard Maestro 的蠢操作：给 PDF 添加页码》](https://utgd.net/article/20515/)，了解具体设计思路请订阅 UNTAG Premium。

![title](img.gif)

v1.1 增加了起始页码和间隔选项，默认从第一页编起，间隔为一页，但是也可以自由设置，例如想从第一百零一页开始编的话，请输入 `101`。

v1.2 取消了等待，但性能较低的电脑可能仍需手动启用等待模块。

![img](img.png)