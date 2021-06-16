## Contributing Guide


### Installation

- Click the [Fork](https://github.com/greyli/flask-docs-zh/fork) button to fork this repository on GitHub.
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

- Open [this README.md file](https://github.com/greyli/flask-docs-zh/edit/main/README.md).
- Find the "Translation To-do List" section, mark the chapter you want to
translate in following format:

```
- [ ] example @your_username Your Name
```

You can link the username to your GitHub profile:

```
- [ ] example [@your_username](https://github.com/your_username) Your Name
```

- Leave a commit message (e.g., "Assign example to @your_username"), then click the
"Propose changes" button to create a PR.


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
