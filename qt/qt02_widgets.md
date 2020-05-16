# 4.2 QT基本控件

## 4.2.1 QT窗体

### 4.2.1.1 菜单栏

菜单栏在窗体中有且只有一个，`include<QMenuBar>`。

1. 定义：`QMenuBar * bar = menuBar();`
2. 设置菜单到窗口中：`setMenuBar(bar);`
3. 利用菜单栏添加菜单：`QMenu * fileMenu = bar->addMenu("文件")`
4. 添加菜单项：`QAction * newAction = fileMenu->addAction("新建")；`
5. 添加分割线：`fileMenu->addSeparator();`

### 4.21..2 工具栏

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

   

### 4.2.1.3 状态栏

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

### 4.2.1.4 铆接部件（浮动窗口）

铆接部件（浮动窗口）在窗体中可以有多个，一般停靠在核心部件周围。头文件：`#include <QDockWidget>`

1. 定义：`QDockWidget * dock = new QDockWidget("铆接部件",this);`
2. 添加铆接部件到窗口中：`addDockWidget(Qt::BottomDockWidgetArea, dock);`
3. 设置铆接部件可停靠的位置：`dock->setAllowedAreas(Qt::TopDockWidgetArea|Qt::BottomDockWidgetArea);`

### 4.2.1.5 核心部件

核心部件在窗口中有且只有一个。

1. 设置核心部件：`setCentralWidget(widget*);`

   ```c++
   QTextEdit * textEdit = new QTextEdit(this);
   setCentralWidget(textEdit);
   ```

   

## 4.2.2 资源文件

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

## 4.2.3 对话框

### 4.2.3.1 QDialog对话框

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

   

### 4.2.3.2 QMessageBox消息对话框

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

   

### 4.2.3.3 QFileDialog文件对话框

打开文件对话框

```c++
connect(actNew, &QAction::triggered, [=](){
        //文件对话框
        //参数1：父窗口 参数2：标题 参数3：打开默认路径 参数4：过滤后缀名
        //返回值：打开文件的完整路径
        QString filename = QFileDialog::getOpenFileName(this,"openMe","/","*.doc");
        qDebug()<<"点击"<<filename;
    });
```

### 4.2.3.4 QColorDialog颜色对话框

```c++
#include<QColorDialog>
//QColor参数
//      r:红 g:绿 b:蓝 a:透明度(默认255，不透明)
//QColor color = QColorDialog::getColor(QColor(int r, int g, int b, int a));
QColor color = QColorDialog::getColor(QColor(255,0,0));
qDebug() << color.red() << " " << color.green() << " " << color.blue();
```

### 4.2.3.5 QFontDialog字体对话框

```c++
#include<QFontDialog>

bool ok;//是否有找到对应字体
//QFont参数
//     family:字体， pointSize:字号
//QFont font = QFontDialog::getFont(&ok, QFont(QString &family, int pointSize));
QFont font = QFontDialog::getFont(&ok, QFont("宋体", 33));
qDebug() << font.family()<< " " << font.pointSize()<< " " << font.italic() << " " << font.bold();
```

## 4.2.4 界面布局

1. 利用widget做控件容器，在容器中可以进行水平布局、垂直布局、grid布局等
2. 使用弹簧控件，支撑布局中各控件直接的间隙
3. widget如果需要修改垂直大小，垂直策略改为fixed
4. 可以修改widget 和控件之间的间隙，默认9 pixel，在layout -> margin

## 4.2.5 常用控件

### 4.2.5.1 按钮

1. Push Button：普通按钮，默认显示文字，在icon属性中可以设置图标

2. Tool Button：工具按钮，默认只显示图片，在toolButtonStyle属性中可以修改文字的显示方式

3. Radio Button：单选按钮，分组需配合GroupBox一起使用

   ```c++
   //radio button: set the default value设置默认值
   ui->btn_man->setChecked(true);
   ```

4. Check Box：复选按钮

   ```c++
   //check box:get the check box's value
   // 0：未选中
   // 1：半选中
   // 2：选中
   connect(ui->checkBox, &QCheckBox::stateChanged, [=](int state){
       qDebug()<< "state=" << state;
   });
   ```

### 4.2.5.2 QListWidget插件

​    `QListWidget`每一行的项目都称为`QListWidgetItem`。

1. 单项添加

   ```c++
   //list widget
   //使用 QString::fromLocal8Bit 来将本地字符编码转换为 Unicode 形式的 QString
   QListWidgetItem * item = new QListWidgetItem(QString::fromLocal8Bit("春眠不觉晓"));
   // add the list item to list widget
   ui->listWidget->addItem(item);
   // set list alignment，只有单项添加的时候才可以设置每个项目的对齐方式
   item->setTextAlignment(Qt::AlignHCenter);
   ```


2. 多项添加

   ```c++
   QStringList list; //List<QString>
   // 初始化list
   list << QString::fromLocal8Bit("春眠不觉晓") << QString::fromLocal8Bit("处处闻啼鸟") \
        << QString::fromLocal8Bit("夜来风雨声") << QString::fromLocal8Bit("花落知多少");
   //将list添加到QListWidget
   ui->listWidget->addItems(list);
   ```

### 4.2.5.3 QTreeWidget插件

`QTreeWidget`每一行的项目都称为`QTreeWidgetItem`。

1. 设置树控件标签头`setHeaderLabels`

2. 设置树根节点，可以有多个根节点 `addTopLevelItem`

3. 在根节点下，添加子节点 `addChild`

   ```c++
   // TreeWidget 树控件使用
   // 1.设置树标签（fromLocal8Bit防止乱码）
   ui->treeWidget->setHeaderLabels(QStringList()<<QString::fromLocal8Bit("英雄")<<QString::fromLocal8Bit("描述"));
   
   // 2.添加树项目
   // 2.1 添加根节点
   QTreeWidgetItem *itemL = new QTreeWidgetItem(QStringList()<<QString::fromLocal8Bit("力量"));
   QTreeWidgetItem *itemM = new QTreeWidgetItem(QStringList()<<QString::fromLocal8Bit("敏捷"));
   QTreeWidgetItem *itemZ = new QTreeWidgetItem(QStringList()<<QString::fromLocal8Bit("智力"));
   ui->treeWidget->addTopLevelItem(itemL);
   ui->treeWidget->addTopLevelItem(itemM);
   ui->treeWidget->addTopLevelItem(itemZ);
   
   // 2.2 添加子节点
   QStringList heroL1;
   heroL1 << QString::fromLocal8Bit("八戒") << QString::fromLocal8Bit("吃啊吃啊");
   
   QTreeWidgetItem * itemL1 = new QTreeWidgetItem(heroL1);
   itemL->addChild(itemL1);
   ```


### 4.2.5.4 QTableWidget插件

`QTableWidget`每一行的项目都称为`QTableWidgetItem`。

1. 设置列数`setColumnCount`

   ```c++
   // TableWidget 表控件使用
   // 1. 设置列数
   ui->tableWidget->setColumnCount(3);
   ```

2. 设置水平表头（列名）`setHorizontalHeaderLabels`

   ```c++
   // 2. 设置列名
   QStringList columnName;
   columnName << QString::fromLocal8Bit("姓名") << QString::fromLocal8Bit("性别") << QString::fromLocal8Bit("年纪");
   ui->tableWidget->setHorizontalHeaderLabels(columnName);
   ```

3. 设置行数`setRowCount`

   ```c++
   // 3. 设置行数
   ui->tableWidget->setRowCount(5);
   ```

4. 设置表格内容`setItem`

   ```c++
   // 4. 添加表项目
   QStringList nameList;
   QStringList sexList;
   
   nameList << QString::fromLocal8Bit("刘备") << QString::fromLocal8Bit("关羽") \
                << QString::fromLocal8Bit("张飞") << QString::fromLocal8Bit("孙尚香");
   sexList << QString::fromLocal8Bit("男") << QString::fromLocal8Bit("男") \
               << QString::fromLocal8Bit("男") << QString::fromLocal8Bit("女");
   
   for (int i = 0; i<4; i++) {
       int col = 0;
       ui->tableWidget->setItem(i, col++, new QTableWidgetItem(nameList[i]));//直接使用[]程序可能挂掉
       ui->tableWidget->setItem(i, col++, new QTableWidgetItem(sexList.at(i)));//使用at会抛出异常
       // 使用QString::number可以将数字转成QString
       ui->tableWidget->setItem(i, col++, new QTableWidgetItem(QString::number(18+i)));
   ```

   

### 4.2.5.5 其他常用控件

1. 栈控件（stacked widget）：设置显示的活动栈 `ui->stackedWidget->setCurrentIndex(1);`

2. 下拉框（combo box）

   - 添加下拉项：`  ui->combo_box->addItem(QString::fromLocal8Bit("英雄"));`

   - 设置当前的显示内容：`ui->combo_box->setCurrentIndex(1);`

3. 标签控件（Label）

   - 利用Label显示图片

     ```c++
     //利用label显示图片
     ui->label_img->setPixmap(QPixmap(":/img/test.png"));
     ```

   - 利用Label显示动图

     ```c++
     //利用label显示动图
     QMovie *qMovie = new QMovie(":/img/test.gif");
     ui->label_gif->setMovie(qMovie);
     //动图需要使用start方法来播放
     qMovie->start();
     ```

     

## 4.2.6 自定义控件

1. 添加qt类：Qt->设计师界面类，将自动生成：cpp、h、ui文件，如SmallWidget

2. 提升widget：在使用该类的界面中提升widget为新建的类（SmallWidget）

3. 修改自定义控件：定义自定义控件中的相关功能

   ```c++
   //spinbox 值修改的时候 进度条也跟着修改
   //原信号存在重载，需要定义函数指针明确使用哪一个信号函数
   void (QSpinBox:: * smallSignal)(int) = &QSpinBox::valueChanged;
   connect(ui->spinBox,smallSignal, ui->hSlider, &QSlider::setValue);
   
   //进度条修改的时候 spinbox的值跟着修改
   connect(ui->hSlider,&QSlider::valueChanged, ui->spinBox, &QSpinBox::setValue);
   ```

   