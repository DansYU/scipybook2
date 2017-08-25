
# Python科学计算 演示程序使用说明


```python
import subprocess
import os
from os import path
import re
#from IPython.nbformat import read
from nbformat import read
```

本文件夹保存本书所有章节对应的IPython Notebook文件。为了正确显示其中的SVG图表，需要运行下面的程序“Trust”所有的Notebook：


```python
for folder, subfolders, filenames in os.walk("."):
    for filename in filenames:
        fullpath = path.join(folder, filename)
        if fullpath.lower().endswith(".ipynb"):
            #subprocess.call(["jupyter", "trust", fullpath, "--profile=scipybook2"])
            subprocess.call(["jupyter", "trust", fullpath])
```

* 通过[examples.ipynb](examples.ipynb)可以运行本书提供的所有实例程序。

* 通过[nbextensions](../../nbextensions/)可以开关Notebook的所有Javascript插件。

* 本书采用Notebook编写，请打开[IPython Notebook操作练习](01-intro/notebook-train.ipynb)学习Notebook的基本操作。

* 请打开[本书提供的魔法命令](01-intro/scpy2-magics.ipynb)查看本书新增的所有魔法命令。

* 运行下面的程序可以得到所有章节对应的Notebook文件链接：


```python
links = []
for folder, _, filenames in os.walk("."):
    for filename in filenames:
        #if re.match(r"\w+-[0-9a-zA-Z]\d\d-.+?\.ipynb$", filename):
        if re.match(r"\w+-[0-9]\d\d-+\w+\.ipynb$", filename):
            fullpath = path.join(folder, filename)
            book = read(fullpath, 4)
            for cell in book.cells:
                if cell.cell_type == "markdown" and cell.source.startswith("#"):
                    title = cell.source.strip("# ")
                    name = path.splitext(filename)[0]
                    folder = path.basename(folder)
                    link = "[{title} - {name}]({folder}/{name}.ipynb)".format(
                        title=title, name=name, folder=folder)
                    links.append(link)
                    break

from IPython.display import display_markdown, Markdown
display_markdown(Markdown("\n\n".join(links)))
```


[Python科学计算环境的安装与简介 - intro-100-whypython](01-intro/intro-100-whypython.ipynb)

[IPython Notebook入门 - intro-200-ipython](01-intro/intro-200-ipython.ipynb)

[扩展库介绍 - intro-300-library](01-intro/intro-300-library.ipynb)

[NumPy-快速处理数据 - numpy-100-ndarray](02-numpy/numpy-100-ndarray.ipynb)

[ufunc函数 - numpy-200-ufunc](02-numpy/numpy-200-ufunc.ipynb)

[多维数组的下标存取 - numpy-300-mulitindex](02-numpy/numpy-300-mulitindex.ipynb)

[庞大的函数库 - numpy-400-functions](02-numpy/numpy-400-functions.ipynb)

[广义ufunc函数 - numpy-470-gufuncs](02-numpy/numpy-470-gufuncs.ipynb)

[实用技巧 - numpy-900-tips](02-numpy/numpy-900-tips.ipynb)

[SciPy-数值计算库 - scipy-100-intro](03-scipy/scipy-100-intro.ipynb)

[拟合与优化-optimize - scipy-210-optimize](03-scipy/scipy-210-optimize.ipynb)

[线性代数-linalg - scipy-310-linalg](03-scipy/scipy-310-linalg.ipynb)

[统计-stats - scipy-400-stats](03-scipy/scipy-400-stats.ipynb)

[数值积分-integrate - scipy-500-integrate](03-scipy/scipy-500-integrate.ipynb)

[信号处理-signal - scipy-600-signal](03-scipy/scipy-600-signal.ipynb)

[插值-interpolate - scipy-700-interpolate](03-scipy/scipy-700-interpolate.ipynb)

[稀疏矩阵-sparse - scipy-810-sparse](03-scipy/scipy-810-sparse.ipynb)

[图像处理-ndimage - scipy-900-ndimage](03-scipy/scipy-900-ndimage.ipynb)

[matplotlib-绘制精美的图表 - matplotlib-100-fastdraw](04-matplotlib/matplotlib-100-fastdraw.ipynb)

[Artist对象 - matplotlib-200-artists](04-matplotlib/matplotlib-200-artists.ipynb)

[坐标变换和注释 - matplotlib-300-transform](04-matplotlib/matplotlib-300-transform.ipynb)

[matplotlib技巧集 - matplotlib-600-tips](04-matplotlib/matplotlib-600-tips.ipynb)

[Pandas-方便的数据分析库 - pandas-100-dataobjects](05-pandas/pandas-100-dataobjects.ipynb)

[下标存取 - pandas-200-getset](05-pandas/pandas-200-getset.ipynb)

[文件的输入输出 - pandas-300-io](05-pandas/pandas-300-io.ipynb)

[数值运算函数 - pandas-400-calculation](05-pandas/pandas-400-calculation.ipynb)

[字符串处理 - pandas-500-string](05-pandas/pandas-500-string.ipynb)

[时间序列 - pandas-600-datetime](05-pandas/pandas-600-datetime.ipynb)

[与`NaN`相关的函数 - pandas-700-nan](05-pandas/pandas-700-nan.ipynb)

[改变DataFrame的形状 - pandas-800-changeshape](05-pandas/pandas-800-changeshape.ipynb)

[分组运算 - pandas-900-groupby](05-pandas/pandas-900-groupby.ipynb)

[SymPy-符号运算好帮手 - sympy-100-intro](06-sympy/sympy-100-intro.ipynb)

[数学表达式 - sympy-200-expression](06-sympy/sympy-200-expression.ipynb)

[符号运算 - sympy-300-calculations](06-sympy/sympy-300-calculations.ipynb)

[输出符号表达式 - sympy-400-output](06-sympy/sympy-400-output.ipynb)

[机械运动模拟 - sympy-500-mechanics](06-sympy/sympy-500-mechanics.ipynb)

[Traits & TraitsUI-轻松制作图形界面 - traits-100-intro](07-traits/traits-100-intro.ipynb)

[Trait类型 - traits-200-types](07-traits/traits-200-types.ipynb)

[TraitsUI入门 - traits-300-uiintro](07-traits/traits-300-uiintro.ipynb)

[用Handler控制界面和模型 - traits-400-handler](07-traits/traits-400-handler.ipynb)

[属性编辑器 - traits-500-editors](07-traits/traits-500-editors.ipynb)

[函数曲线绘制工具 - traits-600-example](07-traits/traits-600-example.ipynb)

[TVTK与Mayavi-数据的三维可视化 - tvtk_mayavi-100-intro](08-tvtk_mayavi/tvtk_mayavi-100-intro.ipynb)

[VTK的流水线(Pipeline) - tvtk_mayavi-200-pipeline](08-tvtk_mayavi/tvtk_mayavi-200-pipeline.ipynb)

[数据集 - tvtk_mayavi-300-dataset](08-tvtk_mayavi/tvtk_mayavi-300-dataset.ipynb)

[TVTK的改进 - tvtk_mayavi-400-tvtk_and_vtk](08-tvtk_mayavi/tvtk_mayavi-400-tvtk_and_vtk.ipynb)

[用mlab快速绘图 - tvtk_mayavi-600-mlab](08-tvtk_mayavi/tvtk_mayavi-600-mlab.ipynb)

[图像处理 - opencv-200-imgprocess](09-opencv/opencv-200-imgprocess.ipynb)

[图像变换 - opencv-300-transforms](09-opencv/opencv-300-transforms.ipynb)

[图像识别 - opencv-400-identify](09-opencv/opencv-400-identify.ipynb)

[形状与结构分析 - opencv-500-shapes](09-opencv/opencv-500-shapes.ipynb)

[Cython-编译Python程序 - cython-100-compiler](10-cython/cython-100-compiler.ipynb)

[Cython入门 - cython-200-intro](10-cython/cython-200-intro.ipynb)

[高效处理数组 - cython-300-memoryview](10-cython/cython-300-memoryview.ipynb)

[Cython技巧集 - cython-600-tips](10-cython/cython-600-tips.ipynb)

[实例 - examples-000-intro](11-examples/examples-000-intro.ipynb)

[使用泊松混合合成图像 - examples-100-possion](11-examples/examples-100-possion.ipynb)

[推荐算法 - examples-300-movielens](11-examples/examples-300-movielens.ipynb)

[频域信号处理 - examples-400-fft](11-examples/examples-400-fft.ipynb)

[布尔可满足性问题求解器 - examples-500-picosat](11-examples/examples-500-picosat.ipynb)

[分形 - examples-600-fractal](11-examples/examples-600-fractal.ipynb)



```python

```
