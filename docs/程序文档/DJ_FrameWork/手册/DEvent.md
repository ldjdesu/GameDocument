# 自动化事件系统使用手册

### 使用方式
1. 导入系统代码。
2. 在DEventCmd.cs中添加对应的事件。
3. 将自身的数据类继承于DEvent_AutoRelease接口，即可实现销毁时自动化释放
3. 使用EventManager的RegistDEvent()来注册事件。
4. 使用EventManager的DispatchDEvent()来引发事件。
5. 使用EventManager的RemoveDEvent()来删除。
6. 事件默认支持最多5个参数，如需增加，在EventManager里增加对应的注册，引发，删除函数即可。
