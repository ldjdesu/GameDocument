# enum ESceenPriority
### 描述：
- 保存UI层级的枚举
```
public enum ESceenPriority
{
    Default = 0,   //主界面以下 预留 目前没有使用到
    PriorityLobby = 10,   //主界面
    PriorityLobbyForSystem = 20,   //各种外围系统层级
    PriorityLobbyForLoading0 = 60, //各种loading页面层级
    PriorityUpLoadingCommonMessageBoxTips0 = 70, //游戏中各种通用弹框层级（高于loading页面）

    //PriorityCount = 100
};
```