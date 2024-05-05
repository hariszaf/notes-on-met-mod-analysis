# Notes on metabolic modelling analysis

This repo hosts the Jupyter book of mine for the analysis of (community) metabolic models. 

## Build a Jupyter book

> GitHub Pages now gives you the option to limit access, making the [site visible only to users with access to the repository that published the Page](https://github.blog/changelog/2021-01-21-access-control-for-github-pages/). 
> With access control, you can use GitHub Pages to publish and share internal documentation and knowledge across your enterprise.


Examples of [Jbooks](https://executablebooks.org/en/latest/gallery/).

As mentioned in the `requirements.txt` file, we need to make sure `jupyter-book` is available locally.
If not, to get it:

```bash
pip install -U jupyter-book
```

Then, for our book, we need the `sphinx` libraries:

```bash
pip install sphinx 
pip install sphinx-proof
pip install pydata-sphinx-theme
```

Also, the `ghp-import` library will be needed. 

```bash
pip install ghp-import
```


Building a Jupyter Book broadly consists of these steps:

- Create your book’s content. You structure your book with a collection of folders, files, and configuration. See [Anatomy of a Jupyter Book](https://jupyterbook.org/en/stable/start/create.html#anatomy-of-a-book).
    There are three things that you need in order to build a Jupyter Book, each of which was just created by running jupyter-book create:

    - A configuration file (`_config.yml`)

    Here’s an example of a simple _config.yml file:

    ```yaml
    # In _config.yml
    title: My sample book
    author: The Jupyter Book Community
    logo: logo.png
    # Execute can be important: https://jupyterbook.org/en/stable/content/execute.html
    execute:
    execute_notebooks: force

    # Add a bibtex file so that we can create citations
    bibtex_bibfiles:
    - references.bib
    ```

    - A table of contents file (`_toc.yml`)

    Example:
    ```yaml
    # In _toc.yml
    format: jb-book
    root: intro
    chapters:
    - file: markdown
    - file: notebooks
    - file: markdown-notebooks
    ```

    - Your book’s content


- Build your book. Using Jupyter Book’s command-line interface you can convert your pages into either an HTML or a PDF book. See [Build your book](https://jupyterbook.org/en/stable/start/build.html).
In our case, the `mybookname` will be the root of the repo, thus we run:

```bash
jupyter-book build .
```

- Publish your book online. Once your book is built, you can share it with others. Most common is to build HTML, and host it as a public website. See [Publish your book online](https://jupyterbook.org/en/stable/start/publish.html).






