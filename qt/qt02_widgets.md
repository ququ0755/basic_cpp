# 4.2 QT基本控件

## 4.2.1 菜单栏

菜单栏在窗体中有且只有一个，`include<QMenuBar>`。

1. 定义：`QMenuBar * bar = menuBar();`
2. 设置菜单到窗口中：`setMenuBar(bar);`
3. 利用菜单栏添加菜单：`QMenu * fileMenu = bar->addMenu("文件")`
4. 添加菜单项：`QAction * newAction = fileMenu->addAction("新建")；`
5. 添加分割线：`fileMenu->addSeparator();`

## 4.2.2 工具栏

一个窗体中可以有多个工具栏，`include<QToolBar>`。

1. 定义：`QToolBar * toolBar = new QToolBar(this)`

2. 设置工具栏到窗口中：`addToolBar(位置， toolBar)`

   `位置：Qt::LetfToolBarArea、Qt::RightToolBarArea...`

3. 设置允许停靠位置：

   `toolBar->setAllowedArears(Qt::LetfToolBarArea | Qt::RightToolBarArea);`

4. 设置浮动：`toolBar->setFloatable(false);`

5. 设置移动，定义工具栏是否可移动的总开关

   `toolBar->setMovable(false);`

6. 工具栏中添加小控件：

   - 添加按钮

     ```c++
     QPushButton * btn = new QPushButton(this);
     toolBar->addWidget(btn);
     ```

   - 添加菜单

     ```c++
     toolBar->addAction(newAction);
     toolBar->addAction(openAction);
     ```

   

## 4.2.3 状态栏

状态栏在窗体中有且只有一个，头文件：`#include <QStatusBar>`

1. 定义：`QStatusBar *status = statusBar;`

2. 将状态栏设置到窗体中：`setStatusBar(status);`

3. 可以在状态栏中设置提示信息

   ```c++
   QLabel *label1 = new QLabel("左侧信息",this);
   status->addWidget(label1);   //在状态栏左侧放置提示信息
   
   QLabel *label2 = new QLabel(this);
   status->addPermanentWidget("右侧信息",this) //从右侧开始方提示信息
   ```

## 4.2.4 铆接部件（浮动窗口）

铆接部件（浮动窗口）在窗体中可以有多个，一般停靠在核心部件周围。头文件：`#include <QDockWidget>`

1. 定义：`QDockWidget * dock = new QDockWidget("铆接部件",this);`
2. 添加铆接部件到窗口中：`addDockWidget(Qt::BottomDockWidgetArea, dock);`
3. 设置铆接部件可停靠的位置：`dock->setAllowedArea(Qt::TopDockWidgetArea|Qt::BottomDockWidgetArea);`

## 4.2.5 核心部件

核心部件在窗口中有且只有一个。

1. 设置核心部件：`setCentralWidget(widget*);`

## 4.2.6 资源文件

创建项目时需要选择ui，并将资源文件导入项目。

1. 添加资源文件：新建文件-> Qt -> Qt Resource File

2. 自定义资源文件名称，生产资源文件，如：起名res，生成res.qrc文件

3. 右键点击资源文件，选择"open in editor"，用编辑的方式打开资源文件

4. 设置前缀：如："/"，资源文件的搜索根路径

5. 添加文件：将所有需要使用的文件（如图标），导入工程

6. 资源文件使用方式：" : + 前缀名 + 文件名"

   ```c++
   ui->actiongNew->SetIcon(QIcon(":/Image/Luffy.png"));
   ```

## 4.2.7 对话框

### 4.2.7.1 分类

1. 模态对话框：当对话框窗体被激活时，不能操作其他窗体

   ```c++
   connect（ui->actionNew, &QAction::triggered, [=](){
       QDialog dlg(this);   //定义对话框
   	dlg.resize(120,40);  //设置对话框大小，避免告警
       dlg.exec();          //阻塞，对话框始终显示
   })
   ```

   

2. 非模态对话框：当对话框长提被激活时，可以操作其他窗体

   ```c++
   connect（ui->actionNew, &QAction::triggered, [=](){
       QDialog * dlg = new QDialog(this);   //定义对话框
   	dlg->resize(120,40);                 //设置对话框大小，避免告警
       dlg->show();                         //阻塞，对话框始终显示
       // 设置对话框属性，当窗体被关闭时，同时回收资源，避免内存泄漏
       // 属性值：55号
       dlg->setAttribute(Qt::WA_DeleteOnClose); 
   })  
   ```

   

### 4.2.7.2 QMessageBox

所有弹出的对话框都是模态对话框，利用静态成员函数可以提示不同的对话框

1. 错误提示：`QMessageBox::critical(this, "error","错误");`

2. 警告提示：`QMessageBox::warning(this, "warning","告警");`

3. 信息提示：`QMessageBox::information(this, "info","信息");`

4. 提问提示：

   ```c++
   QMessageBox::question(this, "question","问题", QMessageBox::Save | QMessageBox::Cancel, QMessageBox::Cancel);
   ```

   > 参数1：父窗体
   >
   > 参数2：窗体标题
   >
   > 参数3：显示信息
   >
   > 参数4：按键类型
   >
   > 参数5：回车默认按键

   

