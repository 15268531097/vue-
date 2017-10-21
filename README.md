# vue后台管理项目
基于vue的新闻管理系统

1. 项目名称
	vue搭建的后台新闻管理系统
2. 	使用到的技术有
	vue , vue-cli , elementUI , webpack , nodeJS , express ,  mongoDB , cookie , axios , sass , vue-router等
3.  主要功能有
	用户管理模块（登录 等），分类管理模块，新闻管理模块 -> 评论管理模块
	使用了mixins混合，减少重复代码的书写，以及SPA单页面技术
4.  遇到的问题及解决方法
	1)	vuex的使用方法不正确
		—— 在使用vuex的过程中，要明确四种方式的工作。
			state	->	声明状态
			getters	->	获取状态数据
			mutations ->	修改状态数据，但只支持同步
			actions	  ->	负责分发任务，修改数据仍然给mutations，但支持异步