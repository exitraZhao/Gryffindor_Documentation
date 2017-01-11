# MovieBox_API

## 用户相关API
+ 用户注册 <font color=red>（供网页端用户使用）</font>
	+ 获取页面:
		+ url: /users
		+ type: GET
		+ **（返回页面）**
	+ 进行注册:
		+ url: /users
		+ type: POST
		+ body: 
			+ password **String**
			+ username **String**
			+ myid **String**
			+ file **Files**
+ 用户登陆
	+ <font color=red>（供网页端用户使用）</font> 
		+ 获取页面:
			+ url: /users/user 
			+ type: GET
			+ **（返回页面）**
		+ 进行登陆
			+ url: /users/user 
			+ type: POST
			+ body:
				+ account **String**
				+ password **String** 
	+ <font color=red>（供微信端用户使用）</font> 
		+ 微信登陆跳转
			+ url: /users/wechat
			+ type: GET
		+ 从定向到微信授权页面
			+ url: /users/wechat/check
			+ type: GET
+ 朋友圈
	+ 进入朋友搜索页面
		+ url: /friends
		+ type: GET
		+ **（返回页面）**
	+ 模糊搜索朋友
		+ url: /friends/friend/\<string:name>
		+ type: GET
		+ params: 
			+ 搜索关键字 **String**
	+ 进入朋友圈页面
		+ url: /timeline
		+ type: GET
		+ **（返回页面）**
	+ 获得更多的朋友圈信息
 		+ url: /timeline/more/\<int:num>
 		+ type: GET
 		+ params:
 			+ 分页页数 **Int**
	+ 修改朋友关系
		+ url: /friends/one/\<int:myid>
		+ type: GET
		+ params:
			+ 朋友的myid **Int** 
 		
## 日历相关API
+ 日历页面
	+ 获取页面：
		+ url: /calendar 	
		+ type: GET
	+ 获取日历一页的所有活动
		+ url: /calendar 
		+ type: POST
		+ body:
			+ firstDay **String (%Y-%m-%d)**    
			+ lastDay **String (%Y-%m-%d)**


## 电影相关API
+ 电影信息
	+ 获取搜索页面：
		+ url: /movies 	
		+ type: GET
	+ 进入具体电影信息页面  
		+ url: /movies/\<int:id>
		+ type: GET
		+ params: 电影的id **(int: id)**
	+ 电影名字模糊匹配所有可能的电影
		+ url: /movies/\<string:name>/\<string:num> 
		+ type: GET
		+ params: 
			+ 搜索关键词 **(string:name)**
			+ 跳过前多少个 **(string:num)** 
	+ 记录观影记录／观看计划
		+ url: /movies 
		+ type: POST
		+ body: 
			+ userId **String**
			+ movieId **String**
			+ createTime **Date**
			+ updateTime **Date**
			+ date **String**
+ 电影观想
	+ 获取用户对于一个电影的感想
		+ url: /movies/impressions/\<string:movieId>
		+ type: GET
		+ params: 电影的id **(string:id)**
		+ **（返回页面）**
	+ 获取好友对于一个电影的感想
		+ url: /movies/friends/\<string:userId>/impressions/\<string:movieId>
		+ type: GET
		+ params: 
			+ 用户的id **(string)**
			+ 电影的id **(string)**
		+ **（返回页面）**
	+ 获取一个电影感想的所有留言
		+ url: /movies/message/\<string:eventId> 
		+ type: GET
		+ params: 
			+ 感想事件的id **(string)** 	
		+ **（返回页面）**
	+ 提交一个电影感想的留言
		+ url: /movies/message/\<string:eventId>
		+ type: POST
		+ params:
			+ 感想事件的id **(string)** 	
		+ body:
			+ message **String**
			
# 定时任务_API
## 用户相关API
+ 管理员状态
	+ 获取登入页面
		+ url: /admin/login
		+ type: GET
		+ **（返回页面）**
	+ 管理员登录
		+ url: /admin/login
		+ type: POST
		+ body:
			+ account **(String)**
			+ password **(String)**
	+ 管理员登出
		+ url: /admin/logout
		+ type: GET
	+ 管理员修改密码
		+ url: /admin/changePassword
		+ type: PUST
		+ body:
			+ password **(String)**
			+ oldPwd **(String)** 

## 系统相关API
+ 系统状态
	+ 开启定时任务系统 
		+ url: /taskManage/startSystem
		+ type: GET
	+ 关闭定时任务系统
		+ url: /taskManage/stopSystem
		+ type: GET 
## 任务相关API
+ 任务状态
	+ 展示任务界面
		+ url: /taskManage/taskShow
		+ type: GET
		+ **（返回页面）** 
	+ 创建任务
		+ url: /taskManage/create
		+ type: POST
		+ body: 
			+ pushTime **String**
			+ beginDate **String**
			+ endDate **String**
			+ jobId **String**
			+ command **String**
			+ description **String**
	+ 更新任务
		+ url: /taskManage/update/\<string:id>
		+ type: PUT
		+ params: 
			+ 任务的id **String**
		+ body:
			+ pushTime **String**
			+ beginDate **String**
			+ endDate **String**
			+ jobId **String**
			+ command **String**
			+ description **String**
	+ 获取具体任务的信息
		+ url: /taskManage/getInfo/\<string:id>
		+ type: GET
		+ params: 
			+ 任务的id **String**
	+ 删除任务
		+ url: /taskManage/delete/\<string:id>
		+ type: DELETE
		+ params: 
			+ 任务的id **String**
	+ 任务搜索
		+ url: /taskManage/taskShow/search
		+ type: GET
		+ args:
			+ jobId **String**
			+ page **Int**
	+ 开始任务
		+ url: /taskManage/startTask/\<string:id>
		+ type: GET
		+ params: 
			+ 任务id **String**
	+ 暂停任务
		+ url: /taskManage/stopTask/\<string:id>
		+ type: GET
		+ params: 
			+ 任务id **String**  
	
## 日志相关API
+ 日志状态
	+ 分页获取日志
		+ url: /log/logShow
		+ type: GET
		+ args: 
			+ page **Int** 
		+ **（返回页面）**
	+ 日志搜索
		+ url: /log/logShow/search
		+ type: GET
		+ args: 
			+ page **Int** 
			+ task **String**
		+ **（返回页面）**
	+ 日志删除
		+ url: /log/delete/\<string:id>
		+ type: DELETE
		+ params: 
			+ 日志id **String**
	+ 获取具体日志内容
		+ url: /log/getInfo/\<string:id>
		+ type: GET
		+ params:
			+ 日志id **String**
			
# 微信通信_API
## 自动回复
+ 验证服务器的有效性
	+ url: /reply
	+ type: GET
+ 为用户发送的消息 
	+ url: /reply
	+ type: POST
	+ body: 
		+ 用户消息通过微信服务器发送过来的xml文件 
