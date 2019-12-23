# LLModuleRouter
模块化开发push、pop、present中间件

### 开发初衷
开发中很多使用Push、Pop、Present控制器的情况，同时需要import类声明，比较繁琐。故在此情况下为了偷懒封装了LLModuleRouter，适用于模块化开发项目。

### 原理
实现原理很简单：主要是使用‘类名字符串’反射为控制器类，然后初始化当前所需控制器，控制器持有公共参数和回调block，控制器所持有参数使用runtime动态绑定，具体可查看实现代码。

### 代码
```

/// 简化模态
/// @param viewControllerName 控制器类名
/// @param publicParamer 公共参数
/// @param isNeedNavigationController 是否需要导航控制器
/// @param animated 是否需要动画
/// @param handlerBlock 回调
void LLModuleRouterPersent(NSString * _Nullable viewControllerName ,id _Nullable publicParamer ,BOOL isNeedNavigationController ,BOOL animated ,HandlerBlock handlerBlock);

/// 简化dimiss
/// @param viewControllerName 控制器类名
/// @param anObject block回调传输对象
/// @param animated 是否需要动画
void LLModuleRouterDimiss(NSString * _Nullable viewControllerName , id _Nullable anObject ,BOOL animated);

/// 简化push
/// @param viewControllerName 控制器类名
/// @param publicParamer 公共参数
/// @param animated 是否需要动画
/// @param handlerBlock 回调
void LLModuleRouterPush(NSString * _Nullable viewControllerName ,id _Nullable publicParamer ,BOOL animated ,HandlerBlock handlerBlock);

/// 简化pop 默认响应HandlerBlock
/// @param viewControllerName 控制器类名
/// @param anObject block回调传输对象
/// @param animated 是否需要动画
void LLModuleRouterPop(NSString * _Nullable viewControllerName , id _Nullable anObject ,BOOL animated);

/// 根据类名删除指定的viewController（使用场景：A->B->C 在C中返回A跳过B 这时候可以调用此方法删除B 。。 当然也可以使用LLRouterPop跳转到指定的控制器）
/// @param viewControllerName 控制器类名
void dynamicRemoveViewController (NSString *viewControllerName);

```


