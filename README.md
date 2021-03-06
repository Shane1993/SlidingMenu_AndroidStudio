# SlidingMenu_AndroidStudio
Using SlidingMenu in AndroidStudio with jfeinstein10-SlidingMenu

在极客学院上看SlidingMenu这一节的时候，发现用AndroidStudio跟着视频导入第三方库的时候遇到了很大的问题，以下是个人按照视频在AndroidStudio上搭建工程的步骤：

1. 创建新项目

2. 下载并解压jfeinstein10和ActionBarSherlock库，网址分别是https://github.com/jfeinstein10/SlidingMenu 和http://actionbarsherlock.com/ 

3. 在项目的目录下创建一个文件夹名为libraries的文件夹

4. 将SlidingMenu和ActionBarSherlock的库复制到libraries中

5. 打开AndroidStudio就能看到该文件夹libraries了，接下来便是在AndroidStudio中修改gradle文件了

6. 打开ActionBarSherlock中的build.gradle，将其中的buildToolsVersion和compileSdkVersion改成与app中的build.gradle的buildToolsVersion和compileSdkVersion一样

7. 打开SlidingMenu中的build.gradle, 将其中的buildToolsVersion和compileSdkVersion改成与app中的build.gradle的buildToolsVersion和compileSdkVersion一样，此时可能会发现该gradle中的classpath那行出现错误，将其改成和app同一个目录下的build.gradle文件中classpath一样

8. 再次打开SlidingMenu中的build.gradle文件，此时AndroidStudio会检测到新增加进来的文件夹没有属于Gradle project所以会提示你将其添加进Gradle project，按Add Now便可以了（同样再次打开ActionBarSherlock中的build.gradle文件执行相同的操作）

9. 在app下的build.gradle的dependencies中添加工程：
comple project(‘:libraries:SlidingMenu’)
comple project(‘:libraries:ActionBarSherlock’)

10. 修改和app文件夹同个目录中的settings.gradle文件
include ‘:app’,’:libraries:SlidingMenu’,’:libraries:ActionBarSherlock’

11. 最后点击AndroidStudio菜单栏的Build->Make Project就大功告成可以使用SlidingMenu了

12. 注：如果工程用的是v7包，运行工程的时候会发现属性重复定义的问题，那是因为和slidingmenu那两个库中的v4包重复了，目前还没有完美的解决方法，以下是我的解决方法，虽然不是很完美，但至少可以运行在虚拟机上看效果啦~

解决方法：
*1 打开app下面的gradle文件，将dependencies下面的含有v7包的那行去掉
*2 再次运行程序，把出错的地方（跟v7包有关的）删掉或者改掉就行了
