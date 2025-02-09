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
  #### 任意类型，如果我们没有为变量指定类型，那它的默认类型就是any.在TS中，any类型的变量能够接收任意类型的数据:
  ```
  var something:any='as string';
  something = 1;
  something = [1,2,3];
  ```
  #### "无"类型：void意味着我们不期望那里有类型。它通常用作函数的返回值，表示没有任何返回值:
  ```
  function someting(name:string):void{
  this.name = name
  }
  ```
  
  #### 示例代码：
  
 ```
  class Product {
  constructor(
  public sku:string,
  public name:string,
  public imageUrl:string,
  public department:string[],
  public price:number){
    }
  }
 ```
 
上面的代码创建了一个名叫Product的类，这个类的构造函数接收5个参数。public sku:string这行代码有两个意思：
- 这个类 实例有一个名为sku的公共属性；
- sku的类型是string

一般情况下，我们应该不会像一个函数传递超过5个参数。另一种做法是将Product类的构造函数修改为接收一个配置对象，这样就可以不必记住参数的顺序了。如果这样做，我们就可以像这样编写Product类的代码：
```
new Product({sku:'MYHAT',name:'A green hat'})
```
#### Angular组件的一个核心特性：输入/输出，方括号[]用来传递输入，圆括号()用来处理输出。
```
<products-list
  [productList]='products'
```
这就是在使用ProductsList组件的输入，这个元素属性分为两个部分：
- '[productList]'(=号左边)
- 'products'(=号右边)
左边的[productList]是指，我们希望在product-list组件中设置名为productList的输入。
右边的'products'是指，我们希望将输入设置为products表达式的值。


```
<products-list
  ...
  (onProductSelect)='productWasSelected($event)'>
```
意思是我们要监听ProductsList组件的onProductSelected输出。
也就是说：
- (onProductSelected),即=号左边是我们要监听的输出的名称；
- 'productWasSelected',即=号右边是当有新的输入时我们想要调用的方法；
- $event在这里是一个特殊的变量，用来表示输出的内容。

### 组件的输入
我们可以用inputs配置项来指定组件希望接收哪些参数。inputs接收一个字符串数组。用来指定输入的键（名称）。
当我们为组件指定了一个输入时，这个组件的定义类就一定要有一个实例属性来接收这个输入的值。例如，假设我们有以下代码：
```
@component({
selector:'my-component',
inputs:['name','age']
})
class MyComponent{
name:string;
age:number;
}
```
name和age输入分别对应于MyComponent类的实例中的name和age属性。
指定组件接收一个输入参数的另一种方式是使用@Input注解。你可以先导入Input，然后把@Input()添加到属性声明上，代码如下：
```
@Component({
selector:'my-component'
})
class MyComponent{
@Input() name:string;
@Input() age:number;
}
```

##### 你可以任意选择这两种方式之一来提供输入属性，它们的效果是一样的。

    
    
      
  
