##**用户登录**：(后端以头部形式返回cookie)

方式：POST

接口：/login

参数 :code (str)

返回参数：

若用户曾经注册过：

{

​	status:"OK",

​	cookie:自定义登录态

}

若用户未注册过：

{

​	status:"need reg",

​	cookie:自定义登录态

}

**用户信息上传**

方式:POST，

接口:/setuserinfo

传入参数：

{

​	truename:'姓名',

​	nickname:'昵称',

​	avater:'http://baidu.com'

}


**首页信息获取**

方式：GET

接口：/gethomepage

返回参数（不返回is_recycle为True的数据）

{

​	"attention":[

​		{

​			imgUrl:'https://www.baidu.com',

​			projectId:1,

​			projectName:'项目一',

​			isRecycle:'N'
      
      creater:
      
      total:
​		}

​	],

​	"create":[

​		{

​			imgUrl:'https://www.baodu.com',

​			projectId:1,

​			projectName:'项目一',

​			isRecycle:'Y',

      isAttention:
      
      creater:
      
      total:

​		}

​	],

​	"follow":[

​		{

​			imgUrl:'https://www.baodu.com',

​			projectId:1,

​			projectName:'项目一',

​			isRecycle:'Y'

      isAttention:
      
      total:

​		}

​	]

}

**添加关注**：

方式：GET，

接口:/addAttention/:projectid

i参数：

{

​	msg:'请求成功/请求失败'

}

**创建项目**:   发送数据时，将content-type改为application/json

方式:POST,

接口:/createProject

发送body：

{

​	projectName:'项目一',

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

接口：/addrecycle/:projectid

返回参数：

{

​	msg:''

}

**获取回收站信息**：  (还没做)

方式：GET，

接口：/getrecycle/:page/:limit

返回参数:

{

​	{

​			imgUrl:'https://www.baidu.com',

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

接口：/getprojectstate/:projectid

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

​					isFinished:N  

​				},

​				{

​					workid:1

​					workName:'任务一',

​					isFinished:Y

​				}

​			]

​		}

​	]

}

**任务详情**：work   content-type:application/json

方式：GET，

接口：/getworkdetail:workid   

参数：

{

​	stateName:'阶段一',

​	executor:[

​		'执行者一',

​		'执行者二'

​	]

​	endtime:2013,

​	remark:'备注'

​	publisher:'发布人'

}

**任务领取**

方式：GET，

接口:/receivework

发送参数：
{
  workid:work1,
  formid:formid
}

返回参数：

{

​	msg:''

}

**任务删除**：

方式：DELETE

接口:/deletework/:workid

参数：{

​	msg:''

}

**任务完成**:

方式：GET，

接口:/finishwork/:workid

参数：

{

​	msg:''

}

**修改时间**:

方式：POST，

接口：/changeworktime/:workid

参数：

{

​	endtime:2019.03.02

}

**创建任务**：

方式：POST，

接口：/creatework    content-type:application/jsopn

参数：

{

​	stateid:1,

​	workname:'任务一',

​	endtime:2019-03-06 11:00:00,

​	remark:'备注',

​	participant:[

​		1，2，3(openid)

​	]

}

**获取项目参与者**：

方式：GET,

接口:/getparticipant/:projectid

参数：

{

​	data:[

​		{

​			openid:1,

​			userName:'limign',

​			avater:'https://baidu.com'

​		},

​		{

​			openid:1,

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

​		time:2019.03.03  01:01:01

​		projectid:1,

​		content:'内容',

​		publisherName:'liming'

​	}

​	]

}

**发布通知**：

方式：POST, （后端自己生成noticeid和time）

接口：/addnotice/:projectid

参数：

{

​		content:'内容',

}

**项目设置**

方式：POST,

接口：/setproject/:projectid

参数：

{

​	imgUrl:'',(待定)

​	projectName:'项目名',

}

获取某个用户首个没有接收的任务：

方式：GET，

接口：/getFirstUnreceived,

参数：

如果有：

{

workid:1,

workName:'任务一',

openid:'openid1'

}

如果没有：

{

workid:null

}

获取某个用户的未领取任务表

方式：GET，

接口：/getUnreceived,

参数：

如果有：

{

data:[

{

workid:1,

workName:'任务一',

projectName:'项目一',

},

{

workid:1,

workName:'任务一',

projectName:'项目一',

},

]

}

如果没有：

{

data:[]

}

获取某个用户已领取但未完成的任务表

方式：GET，

接口：/getUnfinished,

参数：

如果有：

{

data:[

{

workid:1,

workName:'任务一',

projectName:'项目一',

},

{

workid:1,

workName:'任务一',

projectName:'项目一',

},

]

}

如果没有：

{

data:[]

}

