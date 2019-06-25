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
  
  
