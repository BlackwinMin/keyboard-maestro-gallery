# Group Desktop Files 一键整理桌面文件

以第一个选中的文件为准，将所选文件从上到下整理排好。设计来自 Scapple 中画布元素的整理方式。

纯 AppleScript，方便移植。

座标参数基于我的电脑分辨率和桌面设置，请自行调整。

出处：《一键将选中的桌面文件整理成组》，发布时间未定。

![img](img.gif)

```
tell application "Finder"
	set selectedItems to selection
	
	if selectedItems is not {} then
		try
			-- 以第一个文件当前位置为基准
			set firstItem to item 1 of selectedItems
			set basePos to desktop position of firstItem
			set xPos to item 1 of basePos
			set yPos to item 2 of basePos
			
			-- 第一个文件不动，从第二个开始依次下移
			repeat with i from 2 to count of selectedItems
				set theItem to item i of selectedItems
				set newPos to {xPos, yPos + ((i - 1) * 38)}
				set desktop position of theItem to newPos
			end repeat
			
		on error errMsg
			display dialog errMsg & "（请检查文件是否位于桌面，且未启用 Stack）"
		end try
	else
		display dialog "没有选中任何文件。"
	end if
end tell
```