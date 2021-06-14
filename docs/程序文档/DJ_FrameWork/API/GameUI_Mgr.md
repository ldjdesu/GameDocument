# GameUI_Mgr
### 描述：
- UI框架总管理器，负责UI系统的生命周期以及资源管理


```
/// <summary>
/// 打开主城UI
/// </summary>
public class DemoStart : MonoBehaviour
{
    void Start()
    {
        GameUI_Mgr.GetInstance().OpenUI(typeof(MainCityScreen));
    }

}
```

---
### 公开属性
属性名|功能
--- | ---
**poolRoot** | 缓存池节点

---

### 公开函数
函数名|功能
--- | ---
**GetUIRootTransform** |获取UIRoot节点
**GetUICamera** | 获取UI相机
**OpenUI** | 打开界面
**GetUI** | 获取界面
**CloseUI** | 关闭界面
**CloseAllUI** | 关闭所有界面
**Reset** | 重置所有Ui界面

---
### 静态函数
函数名|功能
--- | ---
**GetInstance** | 获取单例实例

---
