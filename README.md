# Flask 文档中文翻译

这里是 Flask 文档中文翻译项目，欢迎参与！在开始翻译之前，请务必阅读下面的 Contributing Guide 了解贡献流程，然后阅读[这个 Issue](https://github.com/greyli/flask-docs-zh/issues/11) 了解翻译基本要求和建议，并在[这个 Dicussion](https://github.com/greyli/flask-docs-zh/discussions/12) 投票选出你认为合适的翻译词汇。

如果有其他问题和相关想法，请[创建 Discussion](https://github.com/greyli/flask-docs-zh/discussions/new) 发起讨论；如果对翻译流程和项目设置有改进建议，或是发现了翻译错误和笔误，请[创建 Issue](https://github.com/greyli/flask-docs-zh/issues/new) 反馈。

这个项目在后期会转移到 [Flask Community Work Group](https://github.com/flaskcwg) 或单独的 Pallets 文档翻译组织，并链接到 Flask 官方文档作为官方中文翻译。


## Contributing Guide


### Installation

- Click the "Fork" button to fork this repository on GitHub.
- Clone your fork repository locally (replace `{username}` with your username):

```
$ git clone https://github.com/{username}/flask-docs-zh
$ cd flask-docs-zh
$ git remote add upstream https://github.com/greyli/flask-docs-zh
```

- Create a virtual environment and install requirements:

For Linux/macOS:

```
$ python3 -m venv env
$ source env/bin/activate
$ python -m pip install --upgrade pip setuptools
$ pip install -r requirements/dev.txt
$ pip install -e .
$ pre-commit install
```

For Windows:

```
> python -m venv env
> env\Scripts\activate
> python -m pip install --upgrade pip setuptools
> pip install -r .\requirements\dev.txt
> pip install -e .
> pre-commit install
```


### Self-Assignment

- Open your fork repository on GitHub.
- Click the "Fetch upstream" button to update your fork.
- Click the edit button (a pencil icon in the upper right corner of the README)
to edit the README.
- Find the "Translation To-do List" section, mark the chapter you want to
translate in following format:

```
- [ ] example.rst @your_username Your Name
```

You can link the username to your GitHub profile:

```
- [ ] example.rst [@your_username](https://github.com/your_username) Your Name
```

- Leave a commit message (e.g., "Assign docs/example.rst to @your_username"), then select
"Create a new branch for this commit and start a pull request" and click the
"Commit changes" button to create a PR.


### Translation

- When the self-assignment PR is merged, create a new branch locally
(be sure to update the example branch name, for example, `translate-cli`):

```
$ git fetch upstream
$ git checkout -b your-branch-name upstream/main
```

- Translate the file, then mark the chapter as finished (fill the checkbox
with "x"):

```
- [x] example.rst @your_username Your Name
```

Commit the changes:

```
$ git add docs/foo.rst README.md
$ git commit -m "Translate docs/foo.rst"
```

- Build the docs and preview the changes:

For Linux/macOS:

```
$ cd docs
$ make html
```

For Windows:

```
> cd docs
> .\make.bat html
```

Open `{project_location}/docs/_build/html/index.html` in your browser to view the docs.

- If everything is working as expected, push the changes to GitHub:

```
$ git push origin your-branch-name
```

- Open the home page of your forked repository, you will see a notice about
the new branch. Click the "Compare & pull request" button to create a PR.
- The translation coordinator will review your PR very soon. Thank you!


## Translation To-do List

Be sure only mark one chapter at a time, make another one when the former
PR is created. Unless it's a long chapter, we may reset the assignment
if you doesn't finish the translation in ten days.


### docs/

- [ ] advanced_foreword.rst
- [ ] appcontext.rst
- [x] async-await.rst  [@rosekc](https://github.com/rosekc) rosekc
- [ ] api.rst
- [ ] becomingbig.rst
- [ ] blueprints.rst
- [ ] changes.rst
- [ ] cli.rst
- [ ] config.rst
- [ ] contributing.rst
- [ ] debugging.rst
- [ ] design.rst
- [ ] errorhandling.rst
- [ ] extensiondev.rst
- [ ] extensions.rst
- [ ] foreword.rst [@greyli](https://github.com/greyli) Grey Li
- [ ] htmlfaq.rst
- [x] index.rst [@greyli](https://github.com/greyli) Grey Li
- [x] installation.rst [@greyli](https://github.com/greyli) Grey Li
- [ ] logging.rst
- [ ] quickstart.rst (reserved)
- [ ] reqcontext.rst
- [ ] security.rst
- [ ] server.rst
- [ ] shell.rst
- [ ] signals.rst
- [ ] templating.rst
- [ ] testing.rst
- [ ] views.rst


### docs/tutorial/ (reserved)

- [ ] blog.rst
- [ ] database.rst
- [ ] deploy.rst
- [ ] factory.rst
- [x] index.rst [@greyli](https://github.com/greyli) Grey Li
- [ ] install.rst
- [ ] layout.rst
- [ ] next.rst
- [ ] static.rst
- [ ] templates.rst
- [ ] tests.rst
- [ ] views.rst


### docs/deploying/

- [ ] asgi.rst
- [ ] cgi.rst
- [ ] fastcgi.rst
- [ ] index.rst [@180909](https://github.com/180909) 180909
- [ ] mod_wsgi.rst
- [ ] uwsgi.rst
- [ ] wsgi-standalone.rst [@180909](https://github.com/180909) 180909


### docs/patterns/

- [ ] appdispatch.rst
- [ ] appfactories.rst
- [ ] caching.rst
- [ ] celery.rst
- [ ] deferredcallbacks.rst
- [ ] distribute.rst
- [ ] fabric.rst
- [ ] favicon.rst
- [ ] fileuploads.rst
- [ ] flashing.rst
- [ ] index.rst
- [ ] jquery.rst
- [ ] lazyloading.rst
- [ ] methodoverrides.rst
- [ ] mongoengine.rst
- [ ] packages.rst
- [ ] requestchecksum.rst
- [ ] singlepageapplications.rst
- [ ] sqlalchemy.rst
- [ ] sqlite3.rst
- [ ] streaming.rst
- [ ] subclassing.rst
- [ ] templateinheritance.rst
- [ ] urlprocessors.rst
- [ ] viewdecorators.rst
- [ ] wtforms.rst


## src/flask/

Only the docstring and attribute comments in the source need to be translated.

- [ ] app.py
- [ ] blueprints.py
- [ ] cli.py
- [ ] config.py
- [ ] ctx.py
- [ ] debughelpers.py
- [ ] globals.py
- [ ] helpers.py
- [ ] logging.py
- [ ] scaffold.py
- [ ] sessions.py
- [ ] signals.py
- [ ] templating.py
- [ ] testing.py
- [ ] views.py
- [ ] wrappers.py
- [ ] json/
