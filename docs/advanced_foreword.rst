.. Foreword for Experienced Programmers

给资深程序员的序言
====================================

.. Thread-Locals in Flask

Flask 的线程局部存储
----------------------

.. One of the design decisions in Flask was that simple tasks should be simple;
.. they should not take a lot of code and yet they should not limit you. Because
.. of that, Flask has a few design choices that some people might find
.. surprising or unorthodox. For example, Flask uses thread-local objects
.. internally so that you don’t have to pass objects around from
.. function to function within a request in order to stay threadsafe.
.. This approach is convenient, but requires a valid
.. request context for dependency injection or when attempting to reuse code which
.. uses a value pegged to the request.  The Flask project is honest about
.. thread-locals, does not hide them, and calls out in the code and documentation
.. where they are used.

Flask 设计决策中的重要一环便是让简单的任务保持简单。
这些任务不应该编写大量的代码，也不应当限制你。因此，
Flask 中的一些设计决策会让人感到惊讶或不合常规。例如，
Flask 使用了线程局部对象（Thread-local Objects），
所以不需要为了保持线程安全而将对象在各个函数中传递。
这种方法很简单，但进行依赖注入或者尝试重用与请求相关的值
的代码时，需要一个有效的请求上下文。Flask 项目坦诚地公开
线程局部存储这个设计，而不会隐藏它们，
并在使用它们的代码和文档中进行了标注。


.. Develop for the Web with Caution

谨慎地进行 Web 应用开发
--------------------------------

.. Always keep security in mind when building web applications.

在进行 Web 应用开发的时候，时刻牢记安全的重要性。

.. If you write a web application, you are probably allowing users to register
.. and leave their data on your server.  The users are entrusting you with data.
.. And even if you are the only user that might leave data in your application,
.. you still want that data to be stored securely.

在编写一个 Web 应用的时候，很可能会让用户在服务器上注册并将其数据保留在服务器上。
用户将数据托付给你。即便这个应用只有自己唯一一个用户，数据的安全仍然是值得留意的一点。

.. Unfortunately, there are many ways the security of a web application can be
.. compromised.  Flask protects you against one of the most common security
.. problems of modern web applications: cross-site scripting (XSS).  Unless you
.. deliberately mark insecure HTML as secure, Flask and the underlying Jinja2
.. template engine have you covered.  But there are many more ways to cause
.. security problems.

不巧的是，有很多方法能让 Web 应用置于危险之地。
Flask 可以保护应用免受常见的跨站脚本（XSS）攻击。
这是现代 Web 应用程序最常见的安全问题之一。
Flask 和底层的 Jinja2 模板引擎将抵御一些跨站脚本攻击。
除非有意将不安全的HTML标记为安全。
尽管如此，许多种情况下，也会带来安全问题。

.. The documentation will warn you about aspects of web development that require
.. attention to security.  Some of these security concerns are far more complex
.. than one might think, and we all sometimes underestimate the likelihood that a
.. vulnerability will be exploited - until a clever attacker figures out a way to
.. exploit our applications.  And don't think that your application is not
.. important enough to attract an attacker.  Depending on the kind of attack,
.. chances are that automated bots are probing for ways to fill your database with
.. spam, links to malicious software, and the like.

该文档将警告您有关 Web 开发方面需要注意安全性的方面。
其中一些安全隐患比想象的要复杂得多，而且有时都低估了利用漏洞的可能性
——直到聪明的攻击者找到了一种利用应用程序的漏洞。
并且不要以为您的应用程序不够重要，不足以吸引攻击者。
根据攻击类型的不同，自动化的机器人很可能会以各种方法将垃圾请求，
与指向恶意软件的链接之类的东西灌满数据库。

.. Flask is no different from any other framework in that you the developer must
.. build with caution, watching for exploits when building to your requirements.

Flask与任何其他框架一样，需要开发人员谨慎构建，并在实现需求的同时留意意外的漏洞。
