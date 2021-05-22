部署方式
==================

虽然 Flask 轻便且易与使用，但是 Flask 的内置服务器不适合用于生产环境中，同时也不能很好的
扩展。本章主要说明在生产环境下正确使用 Flask 的一些方式。

如果你想要把 Flask 应用部署到这里没有列出的 WSGI 服务器，请查询文档中关于 如何使用 WSGI 的部分，
只需要记住： Flask  :class:`Flask` 应用本质上是一个 WSGI 应用。

托管选项
--------------

- `Deploying Flask on Heroku <https://devcenter.heroku.com/articles/getting-started-with-python>`_
- `Deploying Flask on Google App Engine <https://cloud.google.com/appengine/docs/standard/python3/runtime>`_
- `Deploying Flask on Google Cloud Run <https://cloud.google.com/run/docs/quickstarts/build-and-deploy/python>`_
- `Deploying Flask on AWS Elastic Beanstalk <https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create-deploy-python-flask.html>`_
- `Deploying on Azure (IIS) <https://docs.microsoft.com/en-us/azure/app-service/containers/how-to-configure-python>`_
- `Deploying on PythonAnywhere <https://help.pythonanywhere.com/pages/Flask/>`_

自主部署选项
-------------------

.. toctree::
   :maxdepth: 2

   wsgi-standalone
   uwsgi
   mod_wsgi
   fastcgi
   cgi
   asgi
