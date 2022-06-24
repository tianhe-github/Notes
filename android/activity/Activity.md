# Activity

### Activity生命周期

- ![Activity生命周期](../../img/activity生命周期.png)

- 在A跳转B会执行：
    **A onPause ->  B onCreate -> B onStart -> B onResume->A onStop**

- 在A跳转B会执行：
    **A onPause ->  B onCreate -> B onStart -> B onResume->A onStop**

- 在B按下返回键会执行：
    **B onPause -> A onRestart -> A onStart -> A onResume-> B onStop -> B onDestroy**

- 在A跳转B会执行：
    **A onPause ->  B onCreate -> B onStart -> B onResume->A onStop**
- 当 B Activity 的 launchMode 为 singleInstance，singleTask 且对应的 B Activity 有可复用的实例时，生命周期回调是这样的: 
**A.onPause -> B.onNewIntent -> B.onRestart -> B.onStart -> B.onResume -> A.onStop -> ( 如果 A 被移出栈的话还有一个 A.onDestory)** 

- 在A跳转B会执行：
    **A onPause ->  B onCreate -> B onStart -> B onResume->A onStop**
- 当 B Activity 的 launchMode 为 singleTop且 B Activity 已经在栈顶时（一些特殊情况如通知栏点击、连点），此时只有 B 页面自己有生命周期变化:
    **B.onPause -> B.onNewIntent -> B.onResume**




