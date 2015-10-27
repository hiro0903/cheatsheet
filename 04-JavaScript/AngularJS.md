AngularJS 筆記
==============


雖然百般靠北Angular, 可適度到了還是只好K....

筆記only, 沒整理.


---
### Service, Factory, Provider 差異

 - Service:
    - Syntax: module.service('name', function)
    - 調用: 得到instance of myService
 - Factory
    - Syntax: module.factory('name', function)
    - 調用: 得到執行factoryFun的return value - 通常是個function
 - Provider
    - Syntax: module.provider('name', function)
    - 調用: 得到providerFunc.$get()
    