# Activity

### 1.Activity的生命周期



### 2.Activity的启动模式



### 3.Activity的启动流程 [https://www.jianshu.com/p/89fd44083c1c](https://www.jianshu.com/p/89fd44083c1c)

**Activity启动流程：**\
**1、应用通过startActivity或是startActivityForResult方法向ActivityManagerService发出启动请求。**\
**2、ActivityManagerService接收到启动请求后会进行必要的初始化以及状态的刷新，然后解析Activity的启动模式，为启动Activity做一系列的准备工作。**\
**3、做完上述准备工作后，会去判断栈顶是否为空，如果不为空即当前有Activity显示在前台，则会先进行栈顶Activity的onPause流程退出。**\
**4、栈顶Activity执行完onPause流程退出后开始启动Activity。如果Activity被启动过则直接执行onRestart->onStart->onResume过程直接启动Activity（热启动过程）。否则执行Activity所在应用的冷启动过程。**\
**5、冷启动过程首先会通过Zygote进程fork出一个新的进程，然后根据传递的”android.app.ActivityThread”字符串，反射出该对象并执行ActivityThread的main方法进行主线程的初始化。**\
**6、Activity所在应用的进程和主线程完成初始化之后开始启动Activity，首先对Activity的ComponentName、ContextImpl、Activity以及Application对象进行了初始化并相互关联，然后设置Activity主题，最后执行onCreate->onStart->onResume方法完成Activity的启动。**\
**7、上述流程都执行完毕后，会去执行栈顶Activity的onStop过程。**\








