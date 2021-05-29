# Flask 中文文档

这里是 Flask 文档中文翻译项目，欢迎参与！

1. 在开始翻译之前，请务必阅读下面的 Contributing Guide 了解翻译流程，然后阅读[这个 issue](https://github.com/greyli/flask-docs-zh/issues/11) 了解翻译要求，并在[这些 discussions](https://github.com/greyli/flask-docs-zh/discussions/categories/vote) 中分别投票选出最佳翻译词汇、中文 logo 字体和中文标语。
2. 需要强调的是，完成一章的翻译要提交两个 PR：第一个 PR 在对应的章节条目后添加自己的用户名以认领章节；第二个 PR 翻译对应的 `.po` 文件并勾选完成的章节条目。先认领，再翻译，一次只认领一章。
3. 不要改动任何 ReStructuredText 标记、变量/类/函数/方法名称、URL 等。

如果有其他问题和相关想法，请[创建 discussion](https://github.com/greyli/flask-docs-zh/discussions/new) 发起讨论；如果对翻译流程和项目设置有改进建议，或是发现了翻译错误和笔误，请[创建 issue](https://github.com/greyli/flask-docs-zh/issues/new) 反馈。

这个项目在后期会转移到 [FlaskCWG](https://github.com/flaskcwg) 组织，并在翻译完成后链接到 Flask 官方文档。


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
- [ ] example @your_username Your Name
```

You can link the username to your GitHub profile:

```
- [ ] example [@your_username](https://github.com/your_username) Your Name
```

- Leave a commit message (e.g., "Assign example to @your_username"), then select
"Create a new branch for this commit and start a pull request" and click the
"Commit changes" button to create a PR.


### Translation

- When the self-assignment PR is merged, create a new branch locally
(be sure to update the example branch name, for example, `translate-cli`):

```
$ git fetch upstream
$ git checkout -b your-branch-name upstream/main
```

- Translate the `.po` file in the `docs/locales/zh_CN/LC_MESSAGES` directory.

An example of one such file, from docs/.../index.po, is given below.

```po
#: ../../index.rst:4
msgid "Welcome to Flask"
msgstr "欢迎来到 Flask 的世界"
```

Another case, msgid is multi-line text and contains reStructuredText syntax:

```po
#: ../../index.rst:11
msgid ""
"Welcome to Flask's documentation. Get started with :doc:`installation` "
"and then get an overview with the :doc:`quickstart`."
msgstr ""
"欢迎来到 Flask 的文档。你可以从 :doc:`installation` 入手"
"然后阅读 :doc:`quickstart` 来了解基本概念。"
```

Please be careful not to break reST notation. Most
[po-editors](https://www.gnu.org/software/trans-coord/manual/web-trans/html_node/PO-Editors.html) will help you with that.

- Mark the chapter as finished (fill the checkbox with "x"):

```
- [x] example @your_username Your Name
```

- Update the `Last-Translator` field at the top of the `.po` file.
- Commit the changes:

```
$ git add docs/locales/zh_CN/LC_MESSAGES/example.po README.md
$ git commit -m "Translate docs/example"
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

Be sure only mark one chapter at a time, mark another one when the former
PR is created. Unless it's a long chapter, we may reset the assignment
if you doesn't finish the translation in ten days.


### docs/

- [ ] advanced_foreword (reserved)
- [ ] appcontext [@rosekc](https://github.com/rosekc) rosekc
- [ ] async-await
- [ ] becomingbig
- [x] blueprints [@frostming](https://github.com/frostming) Frost Ming
- [ ] changes
- [ ] cli
- [ ] config
- [ ] contributing
- [ ] debugging
- [ ] design
- [ ] errorhandling [@qiufengyu](https://github.com/qiufengyu) Fengyu
- [ ] extensiondev
- [ ] extensions
- [ ] foreword (reserved)
- [ ] htmlfaq
- [x] index [@greyli](https://github.com/greyli) Grey Li
- [x] installation [@greyli](https://github.com/greyli) Grey Li
- [ ] logging
- [ ] quickstart (reserved)
- [ ] reqcontext [@rosekc](https://github.com/rosekc) rosekc
- [ ] security
- [ ] server
- [ ] shell [@LTakamori](https://github.com/LTakamori) LTakamori
- [ ] signals
- [ ] templating
- [ ] testing
- [ ] views


### docs/tutorial/ (reserved)

- [ ] blog
- [ ] database
- [ ] deploy
- [ ] factory
- [x] index [@greyli](https://github.com/greyli) Grey Li
- [ ] install
- [ ] layout
- [ ] next
- [ ] static
- [ ] templates
- [ ] tests
- [ ] views


### docs/deploying/

- [ ] asgi
- [ ] cgi
- [ ] fastcgi
- [ ] index [@180909](https://github.com/180909) 180909
- [ ] mod_wsgi
- [ ] uwsgi
- [ ] wsgi-standalone


### docs/patterns/

- [ ] appdispatch
- [ ] appfactories
- [ ] caching
- [ ] celery
- [ ] deferredcallbacks
- [ ] distribute
- [ ] fabric
- [ ] favicon
- [ ] fileuploads
- [ ] flashing
- [ ] index
- [ ] jquery
- [ ] lazyloading
- [ ] methodoverrides
- [ ] mongoengine
- [ ] packages
- [ ] requestchecksum
- [ ] singlepageapplications
- [ ] sqlalchemy
- [ ] sqlite3
- [ ] streaming
- [ ] subclassing
- [ ] templateinheritance
- [ ] urlprocessors
- [ ] viewdecorators
- [ ] wtforms


## docs/api

- [ ] L0~L1000
- [ ] L1000~L1500
- [ ] L1500~L2000
- [ ] L2000~L2500
- [ ] L2500~L3000
- [ ] L3000~L3500
- [ ] L3500~L4000
- [ ] L4000~L4500
- [ ] L4500~L5000
- [ ] L5000~L5500
- [ ] L5500~L6000
- [ ] L6000~L6500
