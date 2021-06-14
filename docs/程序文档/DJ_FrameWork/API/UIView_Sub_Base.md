# UIView_Sub_Base
### 描述：
- UI子界面的基类，所有UI子界面都必须显式继承于UIView_Sub_Base

```
public class GuildCreateSubScreen : UIView_Sub_Base
{
    GuildCreateSubCtrl mCtrl;// 创建公会子控件

    public GuildCreateSubScreen(GuildCreateSubCtrl subCtrl) :base(subCtrl)
    {
    }

    protected override void Init()
    {
        mCtrl = mComp_Sub_Base as GuildCreateSubCtrl;

        mCtrl.btnCreate.onClick.AddListener(OnCreateClick);
        mCtrl.btnClose.onClick.AddListener(OnCloseClick);
    }

    void OnCreateClick()
    {
        PlayerData.GetInstance().SetHaveGuild(true);
    }

    void OnCloseClick()
    {
        GameUI_Mgr.GetInstance().CloseUI(typeof(UIView_Guild));
    }
}
```

---
### 公开属性
属性名|功能
--- | ---
**UIComp_Sub_Base Comp_Sub_Base** | 页面所绑定的物件类

---
### 公开函数
函数名|功能
--- | ---
**UIView_Sub_Base(UIComp_Sub_Base ctrComp)** | 构造函数
**void Open()** | 打开本页面
**void Close()** | 关闭该页面

---

### 可继承的回调函数
函数名|功能
--- | ---
**void Init()** | UI加载完后触发
**void OnOpen() ** | UI打开时触发
**OnClose()** | UI加载完后触发

---