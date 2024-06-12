# MCDE

***

## :memo:MCDE 1.0

MCDE是一款基于PyQt5构建的分割主动脉夹层并建模的医学图像处理软件，目前处于测试阶段。

:apple:**功能:**

1. 支持直接读取NIfTI file，支持间接读取Dicom file(内置Dicom to NIfTI 的转换器)

2. 支持读取单一文件和文件夹下所有文件，三个视角可视化，可视化控件基于QtWidgets.QGraphicsView进行重绘

3. 提供NIfTI file的直方图，并且可以调控NIfTI file的HU的窗位和窗宽

4. 支持通过MCDE算法预测主动脉区域，主动脉血流域，以及夹层的血栓和内膜区域，支持一键计算和分步计算，支持分割算法选择和后续优化，支持每步结果可视化，（将在论文发表后公开）

5. 提供预测结果(Label)后处理功能

   > 后处理功能支持对MCDE算法预测的区域更改，也可以当作一个正常的医学图像标注软件，我们提供六种颜色的label(对应主动脉夹层分割这显示是足够的)。
   >
   > 提供画笔和毛笔，可以对特定编辑区域做操作，提供多种交互方式。
   >
   > 提供插值方法，对连续相似的编辑区域，可以间隔标注，通过第一帧的轮廓点插值拟合函数，至少需要三帧以上的截面完成标注才能进行插值，对间隔截面数原则上没有要求，但过大间隔可能会导致插值效果较差。

 6. 支持将Label转化为stl进行显示，stl显示控件基于QVTKRenderWindowInteractor进行重绘

    >提供包含复位，重建，创建截面，360°全景视角等功能
    >
    >默认样式为VTK自带的vtkInteractorStyleTrackballCamera：下面提供该样式的操作说明
    >
    >```python
    >vtkInteractorStyleTrackballCamera - interactive manipulation of the
    >camera
    >
    >Superclass: vtkInteractorStyle
    >
    >vtkInteractorStyleTrackballCamera allows the user to interactively
    >manipulate (rotate, pan, etc.) the camera, the viewpoint of the
    >scene.  In trackball interaction, the magnitude of the mouse motion
    >is proportional to the camera motion associated with a particular
    >mouse binding. For example, small left-button motions cause small
    >changes in the rotation of the camera around its focal point. For a
    >3-button mouse, the left button is for rotation, the right button for
    >zooming, the middle button for panning, ctrl + left button for
    >spinning, and shift + right button for environment rotation. (With
    >fewer mouse buttons, ctrl + shift + left button is for zooming, and
    >shift + left button is for panning.)#vtkInteractorStyleTrackballCamera样式 操作的官方说明								
    >```
    >
    >创建截面：我们设计了CutPlaneInteractorStyle样式。操作说明：激活创建截面按钮：鼠标左键按下拖动创建平面，鼠标右键单击stl模型确定平面位置，鼠标中键单击分割，单击点必须捕捉到stl模型，否则分割无效。
    >
    >360°全景视角：我们设计了CutPlaneInteractorStyle演示，为方便实现位于主动脉模型内观察模型各个部分。激活全景视角按钮：鼠标右键单击出现菜单1.选择焦点 2.选择相机位置（单击点必须捕捉到stl模型，否则单击无效）,鼠标左键按下拖动即可调节相机焦点，相机本身位置不变。 

:baby_chick:**语言:** MCDE所有算法都是基于Python语言实现，利用PyQT5构建平台，深度学习网络是基于Pytorch库构建和训练的，最后利用PyInstaller打包

```py
pyinstaller -F -w MCDE.py
```

​		-F打包成单文件 -w 免控制台

:phone:**联系我们:** 邮箱: w3022978104@gmail.com

​					   github: https://github.com/wangsongchen/MCDE



***

## :memo:MCDE 1.0 ➡ 2.0

* :nail_care:更新：更改PyInstaller的打包方式,加速软件打开速度

  ```python
  pyinstaller -D -w MCDE.py
  ```

  -D 打包成单文件夹 -w 免控制台

  **缺点:** 配置文件并没有被打包，存在暴露风险 

***

## :memo:MCDE 2.0 ➡ 2.1

* :nail_care:更新：添加Smoothing功能,平滑生成的主动脉夹层stl模型
* :nail_care:更新：添加了stl文件的导出功能
* :bug:Bug：解决了撤回（ctrl+z）不能正确撤回到上一步的问题

***

## :memo:MCDE 2.1 ➡ 2.2

* :nail_care:更新：插值方法从以开始截面为基准变更为以上一层截面为基准，改善了插值区域过大引起的插值形状畸变
* :bug:Bug：解决了部分bug

***

## :memo:MCDE 2.2 ➡ 2.3

* :nail_care:更新：添加了平面选取点，在三维坐标显示对应点处坐标系的功能，添加分割平面，并且正常显示
* :bug:Bug：解决了部分bug





