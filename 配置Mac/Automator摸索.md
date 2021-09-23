# 记录自己倒腾Automator

这玩意儿确实厉害，不得不佩服苹果自家的软件配合。这软件属于自带软件，长这样：
<div align=center>
    <img src="https://i.loli.net/2020/02/27/BuC9xFNnziAoEkw.png" width="20%">
</div>
点击新建能看到不同的文件类型。
<div align=center>
	<img src="https://i.loli.net/2020/02/27/gp49cuHdJoFTB7W.png" alt="20200227220533.png" width = "70%">
</div>
简单复述一下不同文件类型的功能：  

- **workflow**：在`Automator`内使用的工作流，有点像测试文档的意思。
- **Application**：保存成这种文件是一个可以直接运行的应用程序。可以双击打开，然后运行你指定的流程，如果涉及文件输入的话，直接把文件拖拽到这个应用程序，就可以当作工作流的输入。
- **Quick Action**：类似系统服务功能，可以生成在`Finder`,`Touch Bar`,`Services menu`。比较适合想按快捷键运行的工作流，看具体例子就知道如何运用了。
- **Print Plugin**：不常用不晓得。
- **Folder Action**：文件夹发生特定行为时候运行的工作流，类似通过文件管理来触发的脚本。
- **Calendar Alarm**：用日历中特定时间来触发的自动化脚本。
- **Image Capture Plugin**：不常用。
- **Dictation Command**：通过语音触发的自动化脚本，适合有中二的控制。便于制造贾维斯。

# 基本操作
## 下回再说

# 例子

---

## 1. 打开一套工作的工具
之前写过一个打开`Git`资料的`AppleScript`，本来的打算做的效果是用"Spotlight"控制启动这个脚本。`Spotlight`搜索到文件后，希望运行文件就是运行脚本。所以说这个Workflow应该选择 **Application** ，创建 **Application** 后，在`Automator`左边搜索栏搜索`AppleScript`就可以添加它的流块。
<div align=center>
	<img src="https://i.loli.net/2020/02/27/9cGMyvQzg4lekIL.png" alt="20200227232626.png" width = "100%">
</div>

双击`Run AppleScript`或者拖到右边就可以。然后把写好的脚本放进去，保存文件就ok了。
<div align=center>
	<img src="https://i.loli.net/2020/02/27/jZ8Ro5utLwrV9kx.png" alt="20200227233021.png" width = "100%">
</div>

保存的时候去个合适的文件名。配合上`Spotlight`，确保能用`Spotlight`搜索到这个文件。
<div align=center>
	<img src="https://i.loli.net/2020/02/27/zLaTE3O9blQW2iN.png" alt="20200227233430.png" width = "100%">
</div>

直接选中回车就能愉快的运行脚本了！

---

