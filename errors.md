错误有两种类型,一种是不能处理的错误，一种是可以处理的错误。
//不能处理的错误必须panic,可以处理的错误应当重试或报告错误。

现在梳理一遍流程
首先只考虑标准流程中可能出现的错误,
1. 从命令行读取输入参数 (可能出现参数错误)是可以处理的错误,要求重新输入参数  暂不处理
2. 解析输入参数,检查是否有错误 (可能出现参数错误)是可以处理的错误           暂不处理
3. 初始化程序,写入nft指令    可以处理的错误,可能是表重名了,错误处理方式,换一个表名重新创建,如果成功则继续,失败则退出程序        
4. 初始化queue              一旦失败,执行清除nft指令
5. 循环中处理queue中的数据包    
6. 循环结束,清除nft指令
现在统计共有多少种错误可能出现
//首先