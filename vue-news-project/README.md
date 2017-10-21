# vue-news-project
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

			如果在vuex中要使用axios的http请求操作，由于此时的this指向发生了改变(指向store)，所以需要用Vue.axios.post()请求

		—— 获取vuex的状态值时，为了不做重复的请求数据，通常在入口文件做一次状态更改。但无法防止恶意用户在地址栏直接访问，

			所以需要在main.js里做一个路由判断，无论如何必须跳转到首页，进行一次初始化状态即可

	2)  路由嵌套关系
		—— 在使用vue-router路由操作时，children的使用必须在父路由的router-view中才能生效


	3)  密码加密
		—— 使用crypto.js进行MD5加密，可直接在前台进行加密匹配

	4)	在对评论进行评分组件显示时，绑定的值不正确

		——  通过v-model以及表格的scope.row能拿到当前行的信息，进而匹配数据

	5)  显示每条新闻评论数

		——	在后台由于for循环中的数据库查找是异步的，而for循环比DB操作快，进而拿不到数据。
			这里需要用到async 异步加载模块。

			通过async.map 实施串行有关联操作，来获取评论数

	6)  elementUi 树组件中获取所有子节点

		——  需要在后台进行处理，通过mongoose-materialized的getChildren方法能将嵌套关系变成平行关系，所以可以直接进行for循环

		然后将循环后的数据返回，这里要注意getChildren方法是不包括自己的，所以在循环之前需要先加上本身。


	7)  表单重置问题

		——  elementUI的表单重置方法 this.$refs.formName.resetFileds() 是重置到上一次数据储存的时候，有问题






