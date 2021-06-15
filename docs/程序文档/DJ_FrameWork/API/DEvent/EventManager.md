# EventManager
### 描述：
- 事件管理器，用于注册，引发，删除事件

```
    /// <summary>
    /// 设置是否拥有公会
    /// </summary>
    /// <param name="bHaveGuild"></param>
    public void SetHaveGuild(bool bHaveGuild)
    {
        mBHasGuild = bHaveGuild;
        EventManager.DispatchDEvent(DEventCmd.OnGuildCreated_Event, mBHasGuild);
    }
```

---
### 静态函数
函数名|功能
--- | ---
**RegistDEvent** | 将函数注册进事件
**DispatchDEvent** | 引发事件
**RemoveDEvent** | 将函数从事件删除
