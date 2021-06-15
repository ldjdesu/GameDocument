# UIComp_Sub_Base : DEvent_AutoRelease
### 描述：
- UI子界面的组件类，保存子界面必要的组件和临时数据，需要在父界面的UIComp_Base中保存本类的引用


```
public class GuildCreateSubCtrl : UIComp_Sub_Base
{
    public Button btnCreate;   // 创建公会
    public InputField ipGuildName;// 公会名字
    public InputField ipGuildDesc;// 公会简介
    public Dropdown dpGuildNeed;// 入会要求

    public Button btnClose; // 关闭按钮
}
```