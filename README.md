# RichTextEX支持阴影和描边的版本(基于Cocos2d-x v3.10)

原版本github地址：https://github.com/ArcherPeng/RichTextEXWithUnderLineAndOutLine

原版本基于的cocos2dx版本未知，当前版本是基于cocos2dx v3.10

去除: \n
1.去除了原版本的下划线功能
增加: \n
1.字体描边
2.字体阴影
修正: \n
1.v3.10版本下\n换行不正确问题，换行需设置ContentSize

下面演示代码的效果图：
![Aaron Swartz](https://github.com/huangzhentao/Cocos2dx_RichTextEx/raw/master/example.png)

一个简单的富文本 Label，用法
	
	local txt = RichTextEx:create() -- 或 RichTextEx:create(26, cc.c3b(10, 10, 10))
	
	-- 多行模式要同时设置 ignoreContentAdaptWithSize(false) 和 contentSize
	txt:setMultiLineMode(true)	-- 这行其实就是 ignoreContentAdaptWithSize(false)
	txt:setContentSize(200, 400)
	addChild(txt)
	
	txt:setText("<font fonts/fzlbjt.ttf><64><#FFF><effect shadow><@F00>A ABB<img temp.png>哦<img_50*50 temp.png>B<#00F>&lt;C\tC&gt;<@0F0><64>D\nD<18>EE<")

	如果字符串是由用户输入的话，建议调用RichTextEx.htmlEncode("<ABC>")将用户输入内容编码一下，以避免用户输入关键字符导致无法预知的错误
	在生成字符串之前会自动调用RichTextEx.htmlDecode,如果你自定义了字符串创建，请记得调用这个，以解码
	
基本选项：

	<#F00> = <#FF0000> 	= 文字颜色
	<32>				= 字体大小
	<font Arial>		= 文字字体 支持TTF
	<img filename>		= 图片（filename 可以是已经在 SpriteFrameCache 里的 key，或磁盘文件）
	<img_32*32 fname> 	= 指定大小的图片
	<+2> <-2> <*2> </2> = 当前字体大小 +-*/
	<!>					= 颜色、字体和字体大小恢复默认
	\n \t 				= 换行 ， tab可能暂时实现得不是很好
	
	新增：
	<effect name>		= 设置字体效果 outline : 描边   shadow ：阴影
	<outline 2>			= 描边大小
	<@FFF>				= 字体效果的颜色
	
