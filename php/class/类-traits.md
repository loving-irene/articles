#### trait概述
trait可以看做是特殊的类，和普通的类区别在于两点，一点是关键字不一样，另外一点是traits不能实例化。
    
    class normal_class
    {
        属性区域
        方法区域
    }
    
    trait special_class
    {
        属性区域
        方法区域
    }
    
#### 借助traits，实现横向的多重继承
类-继承一节当中，已经说明，多重继承有两种方案，一种是纵向的（已使用范例说明），一种是横向的，就是借助本节的trait来实现。

    trait level1
    {
        public function plus(){}
    }
    
    trait level2
    {
        public function mul(){}
    }
    
    trait level3
    {
        public function division(){}
    }
    
    trait level4
    {
        public function sub(){}
    }
    
    class math
    {
        use level1;
        use level2;
        use level3;
        use level4;
    }
    
如范例，最终math类提供加减乘除功能，与类-继承一节不同的是，使用trait，可以随意组合，可以使用任意一个功能，也可以任意多个功能进行组合。需要注意的一点是，trait必须放到一个“容器”当中才能使用，如范例中的math，这也是概述中所描述的trait不能实例化。

这样来看，trait才真正让PHP实现了功能组件化，有趣的又是其本身并不具备功能。举个乐高积木的例子，乐高提供了很多基础的正方体，长方体，三棱柱等，这些零件可以单独使用，也可以组合起来使用，trait和这些零件类似，但其不能单独使用，必须先放到一个“容器”当中，然后才能使用，**这里有一个不能忽略的步骤，将trait放入“容器”之中，不然trait无法使用**，普通的类虽然不存在这样的问题，但组合上面又不够灵活。

#### 同时使用trait和extend
    trait fun1
    {
        public function add()
        {
            echo "trait add \r\n";
        }
    }
    
    trait fun2
    {
        public function add()
        {
            echo "fun2 add \r\n";
        }
    }
    
    class dad
    {
        public function add()
        {
            echo "dad add \r\n";
        }
    }
    
    class son extends dad
    {
        use fun1;
    }
    
    $obj = new son();
    $obj->add();#trait add. trait会覆盖dad
    
    class grandson
    {
        use fun1;
        use fun2;
    }
    $obj = new grandson();
    $obj->add();#error trait当中不能出现重名
    
和继承一样，trait同样存在同名覆盖的问题，这里要说明是如果extends和trait同时存在，谁覆盖谁的问题以及多个trait中存在同名时，覆盖关系如何。当前类成员大于trait中成员大于继承的基类中的成员。

根据grandson的测试结果，所有的trait都在同一个作用域中，虽然可以使用多个trait来分割出多个不同的功能，理解上可以看成一个作用域被切割成了多个分离的部分，在“容器”中，又将分离的部分组合到了一起。

#### trait中的同名处理，方法
    trait fun1
    {
        public function add(){}
        public function sub(){}
    }
    
    trait fun2
    {
        public function add(){}
        public function sub(){}
    }
    
    class son
    {
        use fun1,fun2{
            fun1::add insteadof fun2;
            fun2::sub insteadof fun1;
            fun2::sub as f;
        }
    }
    
如上范例，trait fun1和fun2中都定义了add()和sub()，在son“容器”中拼装了fun1,fun2，使用insteadof来指定由谁覆盖谁，上例中由fun1::add（fun1中的add）覆盖fun2中的同名方法。as仅仅只是用来起别名而已，别名的使用就是为了简化。

trait当中同样可以定义属性，需要自己避免重名问题，在实际的项目中，trait中尽量不使用属性，因为没有类似insteadof这样的处理方式。