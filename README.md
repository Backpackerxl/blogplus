# Blog项目使用手册

> blog项目是基于B/S架构的一款个人博客app，目前推出blog-0.0.1-SNAPSHOT.jar内测版，希望大家踊跃参与，在此backpackerxl衷心的感谢所有测试的人员。下面我将介绍项目的结构，及运行方式。

##### 1.整个项目分为，前台，和后台。

> 前台，是用来给游客展示的，后台用来控制前台显示内容，例如，我写了一篇博客，但我不想马上发表，我们可以通过保存，暂时存于数据库不发表，前台页面就不会展示。关于更多后台的控制下面再细说。

##### 2.数据库配置。

> 一个完整的B/S软件，必不可少的就是数据库服务。所以我们需要配置数据库，在我发给你们的测试软件中你们不会发现sql文件，因为这一切在程序运行时就做好了，只要启动测试程序，它会自动，生成相应的表，以及表与表之间的关系，以及创建相应索引，这点大家不必担心。下面才是重点。首先你得找到项目目录下的src/resource下面的application-pro.yml配置文件你只需要更改一个地方，就是你自己的数据库密码（password部分），然后再到数据库中新建一个名为blog的数据库就可以了，为什么要这么配置，因为配置由于约定，没错我就是约定你们的那个人。数据库就讲到这里。还有补充说明一点，本套系统分为2个环境，分别是，一个是测试环境（application-pro.yml），一个是正式环境（application-dev.yml），正式环境的数据库名叫blogplus，切换两种环境要到application.yml文件中将pro改为dev就行。配置由于约定嘛。注意更改配置后要重新打包。原jar包不会跟着配置文件的改变而改变。

##### 3.登陆前的配置

> 如果你来到这里，说明前面的数据库工作你已完成。接下来初始化登录信息，原谅我这一步没有做图形化操作界面，这一步需要我们到blog数据库中为t_user插入一条用户基本信息，用于登录，需要些什么数据大家可以看表结构，尽量填完整，显示页面，才会显得好看。还用户头像，是url地址，大家不要忘了，就是avater字段，其它没有啥可以注意的了

##### 4.个性化配置方法

>  由于打包把配置信息一起打进去了所以要改配置请重新打包，建议使用idea打包，方便快捷。首先还是的找到src/resource目录下的messages.properties这里面是所有的个性化配置选项，因为都是长期固定不变的东西，故而写成了配置文件。下面解释一下配置项的意思。（默认是我提供的配置信息），一共有24个配置选项。

| 配置名         | 描述                                                         |
| -------------- | ------------------------------------------------------------ |
| index.email    | 个人邮箱地址                                                 |
| index.QQ       | 个人QQ号。                                                   |
| index.Chat     | 个人微信二维码，注意这个是图片比较特殊，需要把你的图片放在这个路径下（src/resource/static/images）名字可以自定义，路径格式如下（/images/xxx.jpg）。 |
| index.pay      | 打赏的付费二维码，配置方式跟index.Chat相同。                 |
| index.name     | 这是博客底部的昵称。                                         |
| index.recode   | 这是备案信息，如果项目上线可以填上，不上线请自便。           |
| about.des      | 这是个人介绍或描述，在关于我的页面展示，段落1。              |
| about.tag      | 这是个人介绍或描述，在关于我的页面展示，段落2。              |
| about.m        | 这是关于我页面的个人爱好的标签类容1。                        |
| about.a        | 这是关于我页面的个人爱好的标签类容2。                        |
| about.b        | 这是关于我页面的个人爱好的标签类容3。                        |
| about.c        | 这是关于我页面的个人爱好的标签类容4。                        |
| blog.url       | 这是配置以后上线的一级域名地址，这是生成网页二维码，扫描能够访问的关键不上线的话暂时可配置为如下形式 http://192.168.43.63:8888/ 其中192.168.43.63 为你这台计算机的ipV4地址，8888代表端口号，这里要申明一点，本套系统有两个环境，一个是测试环境（application-pro.yml），一个是正式环境（application-dev.yml），可用两套数据库，一套测试一套正式运行需要创建一个名为blogplus的数据库，因为你电脑不允许同时出现两个相同的数据库，而且端口号也不同，测试环境的端口号为：8888，正式环境端口号为：9999。 |
| about.like1    | 这是博客底部的个人兴趣爱好配置1，只在关于我的页面显示        |
| about.like2    | 这是博客底部的个人兴趣爱好配置2，只在关于我的页面显示        |
| about.like3    | 这是博客底部的个人兴趣爱好配置3，只在关于我的页面显示        |
| index.conten   | 这是博客底部的描述信息                                       |
| comment.avater | 这是游客评论头像的统一设置，因为没有做游客登录注册功能，只能统一设置，注意这个设置是在application.yml配置文件中哦。 |
|index.project1 | 推荐项目一|
|index.project2 | 推荐项目二|
|index.project3 | 推荐项目三|
|index.projecturl1 | 推荐项目在线地址一|
|index.projecturl2 | 推荐项目在线地址二 |
|index.projecturl3 | 推荐项目在线地址三 |



##### 5.后台控制详情页

> 如果你来到这里，说明前面工作你已完成。你以进入后台管理，后台管理主要是CRUD这个不必多说必须具备。后台除了可以控制博客的发布和保存之外还可以对博客进行设置分类、标签、描述信息。最主要的是它能控制，博客详情页面的，转载声明，是否推荐，是否允许评论，是否开启打赏，这些后台都可以控制。

> 以上就是Blog项目使用手册，的所有类容。此次更新修复了社区分页问题最新稳定版本为[blog-0.0.3-SNAPSHOT.jar](https://github.com/Backpackerxl/blogplus/blob/master/target/blog-0.0.3-SNAPSHOT.jar)，添加了几个超链接。