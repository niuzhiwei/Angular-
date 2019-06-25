Angular学习笔记
=========
#### ng serve启动Angular应用。
#### ng generate component hello-world(ng g c hello-world)命令创建新组件
#### *ngFor语法是说我们想在这个属性上使用NgFor指令，可以理解为一个for循环，其目的是为集合中的每个条目都新建一个DOM元素
#### names:string[] 这种语法表示names的类型是string构成的数组，它的另一种写法是Array<string>
#### @input可以接受从父模板传进来的值 @Input() name:string;
#### 为了把一个值传入组件，就要在模板中使用方括号[]语法,[name]="name",在Angular中，添加一个带方括号的属性意味着把一个值传给该组件上同名的输入属性。
#### NgModule注解有三个属性：declarations,imports和bootstrap
  declarations指定了在该模块中定义的组件。使用ng generate时，会自动把生成的组件添加到这个列表里。
  Angular中的一个重要思想：想要在模板中使用一个组件，必须在NgModule中声明它。
  imports描述了该模块有哪些依赖。我们正在创建一个浏览器应用，因此要导入BrowserModlue。
  bootstrap告诉Angular,当使用该模块引导应用时，我们要把AppComponent加载为顶层组件。
#### 在input标签上使用了#(hash)来要求Angular把该元素赋值给一个局部变量。  
#### 在@Component中传入了一个选项：host:{class:'row'}.它告诉Angular：我们要在宿主元素上设置class属性，使其具有row类。
#### TypeScript相对于ES5有五大改善：
  
  - 类型
  - 类
  - 注解  
  - 模块导入
  - 语言工具包（比如解构）
  
  #### TS的新语法可以为变量名提供可选的变量类型：
  ```
  var name:string
  ```
  声明函数时，也可以为函数参数和返回值制定类型：           
    ```                                          
    function greetText(name:string):string{
    return 'Hello'+name;
    }
    ```
 #### 数组用Array类型表示。然而，因为数组是一组相同数据类型的集合，所以我们还需要为数组中的条目制定一个类型。我们可以用Array<type>或者type[]语法来为数组条目指定元素类型：
  ```
  var jobs:Array<string>=['IBM','Microsoft','Google'];
  var jobs:string[]=['Apple','Dell','HP']
  ```
  #### 枚举是一组可命名数值的集合。比如，如果我们想拿到某人的一系列角色，可以这么写：
  ```
  enum Role {Employee,Manager,Admin};
  var role:Role=Role.Employee;
  ```
  默认情况下，枚举类型的初始值是0.我们也可以调整初始化值的范围：
  ```
  enum Role {Employee=3,Manager,Admin};
  var role:Role = Role.Employee;
  ```
  在上面的代码中，Employee的初始值被设置为3而不是0.枚举中其他项的值是依次递增的，意味着Manager的值为4，Admin的值为5.同样，我们也可以单独为枚举中的每一项指定值：
  ```
  enum Role {Employee=3,Manageer=5,Admin=7};
  var role:Role = Role.Employee;
  ```
  还可以从枚举的值来反查它的名称：
  ```
  enum Role {Employee,Manager,Admin};
  console.log('Roles:',Role[0],Role[1])
  ```
    
    
    
      
  
