**用户登录**：(后端以头部形式返回cookie)

方式：GET

接口：/login/:code/

返回参数：

{

​	userid:VCG256,

​	truename:黎明,

​	nickname：liming

}

**用户信息上传**

方式:POST，

接口:/setuserinfo/:userid

参数：

{

​	trueName:'姓名',

​	nickName:'昵称',

​	avater:'http://baidu.com'

}



**首页信息获取**

方式：GET

接口：/gethomepage/:userid

返回参数：

{

​	"attention":[

​		{

​			imgUrl:'https://www.baodu.com',

​			projectid:1,

​			projectName:'项目一',

​		}

​	],

​	"create":[

​		{

​			imgUrl:'https://www.baodu.com',

​			projectid:1,

​			projectName:'项目一',

​		}

​	],

​	"follow":[

​		{

​			imgUrl:'https://www.baodu.com',

​			projectid:1,

​			projectName:'项目一',

​		}

​	]

}

**添加关注**：

方式：GET，

接口:/addAttention/:userid/:projectid

参数：

{

​	msg:'请求成功/请求失败'

}

**创建项目**:

方式:POST,

接口:/createProject/:userid

发送body：

{

​	projectnName:'项目一',

​	imgUrl:'https://baidu.com',

​	states:[

​		{

​			stateName:'阶段一'

​		},

​		{

​			stateName:'阶段一'

​		},

​		{

​			stateName:'阶段一'

​		},

​	]

}

**添加到回收站**:

方式:GET

接口：/addrecycle/:userid/:projectid

返回参数：

{

​	msg:''

}

**获取回收站信息**：

方式：GET，

接口：/getrecycle/:userid/:page/:limit

返回参数:

{

​	{

​			imgUrl:'https://www.baodu.com',

​			projectid:1,

​			projectName:'项目一',

​	}

}

**彻底删除某些项目**:

方式:DELETE

接口：/deleteproject

参数：

{

​	data:[

​		{

​			projectid:2

​		}，

​		{

​			projectid:3

​		}

​	]

}

**项目进展**:

方式：GET，

接口：/getprojectstate/:userid/:projectid

参数:

{

​	data:[

​		{

​			stateid:1,

​			stateName:'阶段一',

​			work:[

​				{

​					workid:1

​					workName:'任务一',

​					condition:0

​				},

​				{

​					workid:1

​					workName:'任务一',

​					condition:0

​				}

​			]

​		}

​	]

}

**任务详情**：

方式：GET，

接口：/getworkdetail/:userid/:workid

参数：

{

​	stateName:'阶段一',

​	executor:[

​		'执行一',

​		'执行二'

​	]

​	endtime:2013,

​	remark:'备注'

​	publisher:'发布人'

}

**任务领取**

方式：GET，

接口:/recievework/:userid/:workid

参数：

{

​	msg:''

}

**任务删除**：

方式：DELETE

接口:/deletework/:userid/:workid

参数：{

​	msg:''

}

**任务完成**:

方式：GET，

接口:/finishwork/:userid/:workid

参数：

{

​	msg:''

}

**修改时间**:

方式：POST，

接口：/changeworktime/:userid/:workid

参数：

{

​	endtime:2019.03.02

}

**创建任务**：

方式：POST，

接口：/creatework/:userid

参数：

{

​	stateid:1,

​	workname:'任务一',

​	endtime:2019.03.06,

​	remark:'备注',

​	participant:[

​		1，2，3(userid)

​	]

}

**获取项目参与者**：

方式：GET,

接口:/getparticipant/:projectid

参数：

{

​	data:[

​		{

​			userid:1,

​			userName:'limign',

​			avater:'https://baidu.com'

​		},

​		{

​			userid:1,

​			userName:'limign',

​			avater:'https://baidu.com'

​		}

​	]

}

**添加新成员**：

(待定)

**获取通知**：

方式：GET,

接口：/getnotice/:projectid

参数：

{

​	data:[

​	{

​		noticeId:1,

​		date:2019.03.03  01:01:01

​		projectid:1,

​		content:'内容',

​		publisherName:'liming'

​	}

​	]

}

**发布通知**：

方式：POST,

接口：/addnotice/:projectid/:userid

参数：

{

​		content:'内容',

}

**项目设置**

方式：POST,

接口：/setproject/:projectid/:userid

参数：

{

​	imgUrl:'',(待定)

​	projectName:'项目名',

}

