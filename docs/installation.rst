安装
====


Python 版本
-----------

我们建议使用最新版本的 Python。Flask 支持 Python 3.6 及其以上版本。


依赖
----

这些包会在安装 Flask 的时候自动安装：

* `Werkzeug`_ 实现了 WSGI——程序和服务器之间交互的 Python 标准。
* `Jinja`_ 是一个模板语言，它可以渲染你的程序提供的页面。
* `MarkupSafe`_ 随 Jinja 附带。当渲染模板时，它会转义不受信任的输入以避免注入攻击。
* `ItsDangerous`_ 可以安全地签名数据以确保数据的完整性。这被用来保护 Flask 的 ``session`` cookie。
* `Click`_ 是一个用来写命令行程序的框架。它提供了 ``flask`` 命令并允许添加自定义管理命令。

.. _Werkzeug: https://palletsprojects.com/p/werkzeug/
.. _Jinja: https://palletsprojects.com/p/jinja/
.. _MarkupSafe: https://palletsprojects.com/p/markupsafe/
.. _ItsDangerous: https://palletsprojects.com/p/itsdangerous/
.. _Click: https://palletsprojects.com/p/click/


可选依赖
~~~~~~~~

这些包不会被自动安装。如果你安装了的话，Flask 会检测到并使用它们。

* `Blinker`_ 提供 :doc:`signals` 支持。
* `python-dotenv`_ 在执行 ``flask`` 命令时开启对 :ref:`dotenv` 的支持。
* `Watchdog`_ 为开发服务器提供更快和更高效的重载器（reloader）。

.. _Blinker: https://pythonhosted.org/blinker/
.. _python-dotenv: https://github.com/theskumar/python-dotenv#readme
.. _watchdog: https://pythonhosted.org/watchdog/


虚拟环境
--------

使用虚拟环境可以在开发和生产环境下管理项目依赖。

虚拟环境解决了什么问题？你的 Python 项目越多，就越有可能需要使用不同版本的 Python 包
，甚至 Python 本身。某个项目使用的新版本的库可能会破坏其他项目的兼容性。

虚拟环境是 Python 库的独立集合，每一个项目对应一个虚拟环境。安装到某个项目的包不会
影响其他项目或是操作系统层级的包。

Python 自带的 :mod:`venv` 模块可以用来创建虚拟环境。


.. _install-create-env:

创建虚拟环境
~~~~~~~~~~~~

创建一个项目文件夹，并在其中创建虚拟环境文件夹 :file:`venv`：

.. tabs::

   .. group-tab:: macOS/Linux

      .. code-block:: text

         $ mkdir myproject
         $ cd myproject
         $ python3 -m venv venv

   .. group-tab:: Windows

      .. code-block:: text

         > mkdir myproject
         > cd myproject
         > py -3 -m venv venv


.. _install-activate-env:

激活虚拟环境
~~~~~~~~~~~~

在开始动手做你的项目之前，先激活对应的虚拟环境：

.. tabs::

   .. group-tab:: macOS/Linux

      .. code-block:: text

         $ . venv/bin/activate

   .. group-tab:: Windows

      .. code-block:: text

         > venv\Scripts\activate

你的 shell 提示符现在会显示激活的虚拟环境名称。


安装 Flask
----------

在激活的虚拟环境内，使用下面的命令安装 Flask：

.. code-block:: sh

    $ pip install Flask

Flask 现在已经安装好了。阅读 :doc:`/quickstart` 或是前往 :doc:`文档概览 </index>`
进一步了解 Flask。
