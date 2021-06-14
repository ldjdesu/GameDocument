# 如何基于UIFrameWork进行UI开发
## 代码示例：
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
        if (bHaveGuild)
        {
            mSubCreate.Open();
            mSubInfo.Open();
        }
        else
        {
            mSubCreate.Close();
            mSubInfo.Close();
        }
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
        // 处理子界面逻辑初始化和显隐
        if (bCreated)
        {
            mSubCreate.Close();
            mSubInfo.Open();
            mSubInfo = new GuildInfoSubScreen(mComp.subInfo);
        }
        else
        {
            mSubCreate.Open();
            mSubInfo.Close();
            mSubCreate = new GuildCreateSubScreen(mComp.subCreate);
        }
    }


}

```
---
## 工作流程：
1. 拼好ui
2. 在根节点上添加UIComp_Base的脚本并往其中添加需要的页面临时数据。
3. 拖拽ui组件到UIComp_Base类绑定
4. 如果有子界面：在子界面的根节点添加UIComp_Sub_Base脚本，具体操作和UIComp_Base一样。并且在对应的UIComp_Base中声明UIComp_Sub_Base脚本并在编辑器拖入组件。
5. 在UIConst中添加预制名字符串
6. 新建UIView_Base和UIView_Sub_Base脚本书写页面逻辑，需要遵守UIFrameWork的生命周期。
7. 
---
### UIFrameWork的生命周期
### UIView_Base：
##### OnLoadSuccess() -> OnClose()

### UIView_Sub_Base
##### Init()->OnOpen->Onclose -> UIView_Base.OnClose()