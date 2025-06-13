# Move Desktop Items 全键盘调整桌面文件位置

以全键盘方式移动桌面上的文件，避免使用触控板或鼠标，可一次性移动整组文件。我经常在交通工具上办公，故设计此套动作。默认操作为：

- `⌥Option-⌘Command-下箭头`：向下移动
- `⌥Option-⌘Command-上箭头`：向上移动
- `⌥Option-⌘Command-左箭头`：向左移动
- `⌥Option-⌘Command-右箭头`：向右移动

不支持 Stack 布局。

使用前请根据您的实际情况修改座标增减量，可使用以下 AppleScript 脚本测量直面文件的位置，并算得纵横两个维度的插值。

```
tell application "Finder"
	set selectedItems to selection
	repeat with theItem in selectedItems
		get desktop position of theItem
	end repeat
end tell
```

出处：《吭哧吭哧，全键盘调整 Finder 桌面文件位置》，发布时间未定。 

![img](img.gif)