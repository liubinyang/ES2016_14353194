

# Lab2：DOL实例分析&编程

##### 修改后的dot图

- example1.dot

![dot1.PNG](http://upload-images.jianshu.io/upload_images/3326728-70855a082aa4f22a.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



- example2.dot

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/3326728-286d1cb2dff390f5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



##### 具体实验修改步骤

- example1

  根据实验文档的提示，example1主要是修改square.c中的代码，square.c的代码如下：

  ```
  #include <stdio.h>

  #include "square.h"

  void square_init(DOLProcess *p) {
      p->local->index = 0;
      p->local->len = LENGTH;
  }

  int square_fire(DOLProcess *p) {
      float i;

      if (p->local->index < p->local->len) {
          DOL_read((void*)PORT_IN, &i, sizeof(float), p);
          i = i*i;    //平方
          DOL_write((void*)PORT_OUT, &i, sizeof(float), p);
          p->local->index++;
      }

      if (p->local->index >= p->local->len) {
          DOL_detach(p);
          return -1;
      }

      return 0;
  }
  ```

  如上所示，我们只需要将注释处的代码改为 i = i * i * i，即可完成三次方的运算。



- example2

  根据实验文档的提示，example2主要是修改xml的iterator，所以example2.xml的部分代码如下所示：

  ```
    <variable value="3" name="N"/>

    <!-- instantiate resources -->
    <process name="generator">
      <port type="output" name="10"/>
      <source type="c" location="generator.c"/>
    </process>

    <iterator variable="i" range="N">
      <process name="square">
        <append function="i"/>
        <port type="input" name="0"/>
        <port type="output" name="1"/>
        <source type="c" location="square.c"/>
      </process>
    </iterator>
  ```

  我们可以看到这一部分的代码是通过迭代，定义了3个square模块，所以要变为2个模块只用将variable value的值改为2即可，即：  variable value="2" name="N"/



##### 实验感想

 	这一次实验是对dol中的example1和example2的具体内容进行研究，分析具体的实例，在熟悉过后进行小范围的修改，来完成实验。

​	通过这次实验，了解到了example中各个文件的含义，能够大概看懂每个文件对应实现的模块，定义模块间的连接等等，以及一些函数的作用和使用方法和进程的定义。加深了对于DOL的理解和对于DOL的使用更加熟悉。