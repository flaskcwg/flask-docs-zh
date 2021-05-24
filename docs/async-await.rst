.. _async_await:

使用 ``async`` 和 ``await``
===========================

.. versionadded:: 2.0

.. Routes, error handlers, before request, after request, and teardown
.. functions can all be coroutine functions if Flask is installed with the
.. ``async`` extra (``pip install flask[async]``). This allows views to be
.. defined with ``async def`` and use ``await``.

在安装 Flask 时使用 ``async`` 额外后缀（``pip install flask[async]``）之后，包括
路由、错误处理、请求前、请求后、清理（teardown）的函数都可以使用协程函数。这允许视图
函数使用 ``async def`` 定义，以及使用 ``await``。

.. code-block:: python

    @app.route("/get-data")
    async def get_data():
        data = await async_db_query(...)
        return jsonify(data)

.. .. admonition:: Using ``async`` on Windows on Python 3.8

..     Python 3.8 has a bug related to asyncio on Windows. If you encounter
..     something like ``ValueError: set_wakeup_fd only works in main thread``,
..     please upgrade to Python 3.9.

.. admonition:: 在 Windows，Python 3.8 环境下使用 ``async``

    在 Windows，Python 3.8 环境下存在一个与 asyncio 相关的 bug。如果遇到
    类似 ``ValueError: set_wakeup_fd only works in main thread`` 的信息，
    请更新到 Python 3.9。

.. Performance

性能
----

.. Async functions require an event loop to run. Flask, as a WSGI
.. application, uses one worker to handle one request/response cycle.
.. When a request comes in to an async view, Flask will start an event loop
.. in a thread, run the view function there, then return the result.


异步函数需要一个事件循环来执行。作为一个 WSGI 应用，Flask 使用一个线程去处理
请求/响应循环。当请求进入一个异步视图函数时，Flask 将在一个线程中启动一个事件
循环，在这个事件循环中执行视图函数，然后返回结果。

.. 译注：根据语义，uses one worker似乎是单线程的意思。

.. Each request still ties up one worker, even for async views. The upside
.. is that you can run async code within a view, for example to make
.. multiple concurrent database queries, HTTP requests to an external API,
.. etc. However, the number of requests your application can handle at one
.. time will remain the same.

即使使用异步视图函数，每一个请求依然与一个线程绑定在一起。这样设计的好处时
在视图函数中可以执行异步代码，例如多个并行的数据库查询，HTTP请求外部API等等。
然而，同一时间应用本身能接受的请求数量不会改变。

.. **Async is not inherently faster than sync code.** Async is beneficial
.. when performing concurrent IO-bound tasks, but will probably not improve
.. CPU-bound tasks. Traditional Flask views will still be appropriate for
.. most use cases, but Flask's async support enables writing and using
.. code that wasn't possible natively before.

**异步并不一定比同步代码快。** 异步的优势是在IO密集任务上，但是在CPU密集任务上
则不然。传统的 Flask 视图函数在大多数情况下是合适的选择，而 Flask 对异步的支持让
运行和使用协程代码成为可能，这是以前原生环境无法做到的。

.. Background tasks

后台任务
--------

.. Async functions will run in an event loop until they complete, at
.. which stage the event loop will stop. This means any additional
.. spawned tasks that haven't completed when the async function completes
.. will be cancelled. Therefore you cannot spawn background tasks, for
.. example via ``asyncio.create_task``.

异步函数在其执行完成前，都一个事件循环中运行。当异步函数完成时，事件循环也将停止。
这意味着异步函数完成的时候，所有尚未完成的其他衍生任务都将被取消。因此，不能使用
类似 ``asyncio.create_task`` 的方法来创建后台任务。

.. If you wish to use background tasks it is best to use a task queue to
.. trigger background work, rather than spawn tasks in a view
.. function. With that in mind you can spawn asyncio tasks by serving
.. Flask with an ASGI server and utilising the asgiref WsgiToAsgi adapter
.. as described in :ref:`asgi`. This works as the adapter creates an
.. event loop that runs continually.

要使用后台任务，最好的方法就是使用任务队列去激活后台任务，而不是在视图函数中
创建。考虑到这点，使用 ASGI 服务器来为 Flask 提供服务来创建后台任务，然后如
:ref:`asgi` 提到的使用 asgiref 中的 WsgiToAsgi 适配器。这种做法与适配器
创建了一个持续运行的事件循环类似。

.. When to use Quart instead

何时使用 Quart 作为替代品
-------------------------

.. Flask's async support is less performant than async-first frameworks due
.. to the way it is implemented. If you have a mainly async codebase it
.. would make sense to consider `Quart`_. Quart is a reimplementation of
.. Flask based on the `ASGI`_ standard instead of WSGI. This allows it to
.. handle many concurrent requests, long running requests, and websockets
.. without requiring multiple worker processes or threads.

基于实现上的不同，Flask 的异步支持的性能比异步优先的框架会稍低。如果已经拥有
一个以异步为主的代码库，考虑使用 `Quart`_ 是明智的选择。Quart 是一个基于 `ASGI`_
的 Flask 重新实现版本（而 Flask 是基于 WSGI 的）。这让多并行请求，长时间运行
的请求，以及 websockets 编程不再需要多个工作进程或线程。

.. It has also already been possible to run Flask with Gevent or Eventlet
.. to get many of the benefits of async request handling. These libraries
.. patch low-level Python functions to accomplish this, whereas ``async``/
.. ``await`` and ASGI use standard, modern Python capabilities. Deciding
.. whether you should use Flask, Quart, or something else is ultimately up
.. to understanding the specific needs of your project.

当前已经可以使用 Gevent 或 Eventlet 运行 Flask 来得到使用异步请求处理的好处。
这些库通过为底层 Python 库打补丁的方式实现，而 ``async``/``await`` 与 ASGI
使用了现代标准 Python 的特性。决定是否应使用 Flask，Quart 或其他工具最终取决于
了解项目的特定需求。

.. _Quart: https://gitlab.com/pgjones/quart
.. _ASGI: https://asgi.readthedocs.io/en/latest/


扩展
----

.. Flask extensions predating Flask's async support do not expect async views.
.. If they provide decorators to add functionality to views, those will probably
.. not work with async views because they will not await the function or be
.. awaitable. Other functions they provide will not be awaitable either and
.. will probably be blocking if called within an async view.

Flask 扩展系统先于 Flask 异步支持，所以并不会假设视图函数是异步的。如果扩展提供了对
视图函数的有附加功能的装饰器，这些装饰器因为不会异步等待（await）函数运行或者不是
异步可等待（awaitable）的，可能在异步视图函数上不能正常运行。扩展提供的其他函数或许
同样不是异步可等待的，在异步视图函数调用的时候大概会阻塞。

.. Extension authors can support async functions by utilising the
.. :meth:`flask.Flask.ensure_sync` method. For example, if the extension
.. provides a view function decorator add ``ensure_sync`` before calling
.. the decorated function,

扩展作者可以通过使用 :meth:`flask.Flask.ensure_sync` 方法来支持异步番薯。
例如，如果扩展提供了一个视图函数装饰器，使用 ``ensure_sync`` 调用被包裹的函数。

.. code-block:: python

    def extension(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            ...  # Extension logic
            return current_app.ensure_sync(func)(*args, **kwargs)

        return wrapper

.. Check the changelog of the extension you want to use to see if they've
.. implemented async support, or make a feature request or PR to them.

检查扩展的更新记录，查看是否实现了异步支持。如果没有可以向他们提交 PR。


.. Other event loops

其他事件循环
------------

.. At the moment Flask only supports :mod:`asyncio`. It's possible to
.. override :meth:`flask.Flask.ensure_sync` to change how async functions
.. are wrapped to use a different library.

当前 Flask 只支持 :mod:`asyncio`。覆盖 :meth:`flask.Flask.ensure_sync`
可以修改包裹异步函数的实现，以使用其他库。
