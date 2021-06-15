# UIComp_Base : DEvent_AutoRelease
### 描述：
- UI的数据组件类，保存界面必要的组件和临时数据，除子界面以外，所有UI界面的组件类都必须显式继承于UIComp_Base。如果本界面有子界面，则需要拥有UIComp_Sub_Base的引用


```
public class UIComp_Guild : UIComp_Base
{
    public GuildCreateSubCtrl subCreate; // 创建公会
    public GuildInfoSubCtrl subInfo;         // 公会详情  

}
```

---
### 公开属性
属性名|功能
--- | ---
**Canvas ctrlCanvas** | 对应的Canvas
**ESceenPriority sceenPriority** | UI的SortingLayer

---
