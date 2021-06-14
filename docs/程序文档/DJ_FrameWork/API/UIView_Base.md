# UIView_Base
### 描述：
- UI界面的基类，除了子界面外，所有UI界面都必须显式继承于UIView_Base


```
public class UIView_Guild : UIView_Base
{
    UIComp_Guild mComp;

    GuildCreateSubScreen mSubCreate;// 创建公会界面逻辑
    GuildInfoSubScreen mSubInfo;        // 公会详情界面逻辑

    public UIView_Guild(UI_OpenView_Parameter_Base param = null) : base(UIConst.UIGuild){ }

    protected override void OnLoadSuccess()
    {
        base.OnLoadSuccess();
        mComp = mComp_Base as UIComp_Guild;

        // 监听公会创建成功事件
        EventManager.RegistDEvent(DEventCmd.OnGuildCreated_Event, mComp, OnGuildCreated);
        // 有公会就打开公会详情 没有就打开创建界面
        bool bHaveGuild = PlayerData.GetInstance().HaveGuild();
        // 处理子界面的显示隐藏
        mComp.subInfo.gameObject.SetActive(bHaveGuild); 
        mComp.subCreate.gameObject.SetActive(!bHaveGuild);

        // 处理子界面逻辑初始化
        if (bHaveGuild) 
        {
            mSubInfo = new GuildInfoSubScreen(mComp.subInfo);
        }
        else
        {
            mSubCreate = new GuildCreateSubScreen(mComp.subCreate);
        }
    }

    void OnGuildCreated(bool bCreated)
    {
        // 这里可以直接从PlayerData拿数据，也可以通过参数传递进来，就看你定义的时候是否给事件定义参数了
        //bCreated = PlayerData.GetInstance().HaveGuild();
        // 处理子界面的显示隐藏
        mComp.subInfo.gameObject.SetActive(bCreated);
        mComp.subCreate.gameObject.SetActive(!bCreated);

        // 处理子界面逻辑初始化
        if (bCreated)
        {
            mSubInfo = new GuildInfoSubScreen(mComp.subInfo);
        }
        else
        {
            mSubCreate = new GuildCreateSubScreen(mComp.subCreate);
        }
    }
}
```

---
### 公开属性
属性名|功能
--- | ---
**mComp_Base** | 页面所绑定的物件类
**mPanelRoot** | 对应的UIRoot
**mStrUIName** | 页面名称
**mOpenOrder** | 页面的打开顺序

---
### 公开函数
函数名|功能
--- | ---
**void SetOpenOrder(int openOrder)** | 手动设置ui的sortOrder

---

### 可继承的回调函数
函数名|功能
--- | ---
**OnLoadSuccess()** | UI加载完后触发
**void OnClose()** | UI销毁前调用

---