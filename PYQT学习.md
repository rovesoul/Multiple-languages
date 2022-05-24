- [QT-designer如何安装问题，实际不用anaconda的，直接系统也有](https://blog.csdn.net/weixin_41929524/article/details/81456308)，系统文件位置：C:\Users\39770\AppData\Local\Programs\Python\Python37\Lib\site-packages\qt5_applications\Qt\bin
- [pyqt-designer的ui转为python文件](https://blog.csdn.net/Angelasan/article/details/44917283)
## 虚拟环境
###  创建虚拟环境
`virtualenv ven `

###  打开虚拟环境
`ven\scripts\activate `

###  关闭虚拟环境
`deactivate.bat`

###  查看piplist 
`pip list`

###  此环境装载了pyqt6
`pip install PyQt6`


###  新建用户环境变量
```
名称：QT_QPA_PLATFORM_PLUGIN_PATH
位置：E:\D-drive-61125\PyQtApps\biliUdemy课程\ven\Lib\site-packages\PyQt6\Qt6\plugins\platforms
```

##  Qtdesigner
需要安装`pyqt6-tools`的库文件
`pip install pyqt6-tools`

文件路径：\ven\Lib\site-packages\qt6_applications\Qt\bin 找到designer.exe

01. UI 转Py文件
`pyuic6 -x exampleUI.ui -o WinUI.py`

02. 直接加载UI文件

``` python
from PyQt6.QtWidgets import QApplication,QWidget
import sys


from PyQt6 import uic

class UI(QWidget):
    def __init__(self):
        super().__init__()

        uic.loadUi("exampleUI.ui",self)


app = QApplication(sys.argv)
window = UI()
window.show()
app.exec()
```



[https://www.bilibili.com/video/BV1US4y1P7ae?p=22](https://www.bilibili.com/video/BV1US4y1P7ae?p=22)

第一部分 安装

第二部分，各个组件的介绍

  Qlabel

  QPushButton

  QLineEdit

  QHBoxLayout

  QVBoxLayout

  QGridLayout

  QRadioButton

  QCheckBox

  QSpinBox

  QDoubleSpinBox

  QLCDNumber

  QComboBox

  Q.......



第三部分 案例 文本编辑程序



第四部分 案例 数据库操作



第五部分 2D图像和绘画



第六部分 QtQuick and QML



第七部分 QT6 图表



第八部分 图书馆管理系统



第九部分 Qt多媒体和网络浏览器以及打包exe