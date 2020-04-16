# Words-away  
## 这个东西是干什么的？
一个文本处理工具，用于防止对文本的敏感词检测。主要是因为酷安的折叠词太过蜜汁，**例如“申诉”也会被折叠（doge）**所以就有了这个软件。

设计目标为酷安，理论上所有完整支持Unicode的社区等 都能够使用，但效果不确定。实测对[网易易盾](https://dun.163.com/product/text-detection)的文本检测API有一定效果。

## 原理：
+ 普通模式：在相隔的两个字符之间插入Unicode零宽间隔符（[U+200B](https://unicode.org/cldr/utility/character.jsp?a=200B)）以规避检测。

+ （可选）增强的双重反转模式：将一行内所有文字顺序反转（物理）再加入Unicode反转控制符([U+202E](https://unicode.org/cldr/utility/character.jsp?a=202E))从而实现增强的规避检测。

+ （可选）（默认选中）规避中括号：遇到中括号时不进行反转，以避免表情符号出现Bug。

关于原理的详细说明，可以参考[这篇文章](https://blog.texice.xyz/2020/Anti-Text-Detect/)。


## 隐私：
基于JavaScript的网页实现，仅运行在浏览器端，不会将数据传到服务器~可以放心使用
## 已实现/将实现的功能：
+ [x] 增强模式
+ [x] 自动判断链接并绕行
+ [ ] ~~多♂插♂几个空白符（逃）~~
## 已知的问题：
+ 用双重反转模式处理之后，当一行文本（即不含换行符）以多行的形式显示时，那几行的顺序会反转，[详见这里](https://blog.texice.xyz/2020/Anti-Text-Detect/#%E4%B8%80%E4%B8%AA%E9%97%AE%E9%A2%98)。暂时无法解决
## 使用：
+ 可以使用 [在线网页](https://wordsaway.texice.xyz/)
+ 可以在[Release页面](https://github.com/NitroRCr/Words-away/releases)下载最新的离线版本
>1. 打开网页  
>2. 输入或粘贴需要处理的文本  
>3. 根据需要选中相应的功能，“避开中括号”或者“双重反转”  
>4. 处理，复制  
>5. 粘贴到酷安，能够正常发出（大多数情况）  
>>另有一个[被历史抛弃的旧版](https://blog.texice.xyz/demo/textmix)，已停止维护，随时移除。
## 免责声明：
**过于敏感的词语即使反转也会被检测到**，因此这个工具并不是万能的  
另外虽然Unicode控制符不会被机器检测，**但是酷安小编本人说过用Unicode控制符发送严重违规消息直接永封不解。**  
因此虽然这是个好东西但是切勿滥用，*不然到时候某一天酷安算法可以识别控制符了对谁都不好*  
## 关于：
>这个项目本来就是无聊开发的  
>可以查阅[作者的酷安主页](http://www.coolapk.com/u/1362352)  
>以及[作者的Github主页](https://github.com/NitroRCr)  
>
>欢迎 Star, Fork, PR
