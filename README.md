# Notes on metabolic modelling analysis

This repo hosts the Jupyter book of mine for the analysis of (community) metabolic models. 

## Build a Jupyter book

### Overview

> For Enterprise version:
> GitHub Pages now gives you the option to limit access, making the [site visible only to users with access to the repository that published the Page](https://github.blog/changelog/2021-01-21-access-control-for-github-pages/). 
> With access control, you can use GitHub Pages to publish and share internal documentation and knowledge across your enterprise.
> For the free plan, it seems you need to have your repo public. 



Examples of [Jbooks](https://executablebooks.org/en/latest/gallery/).

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

> **REMEMBER**
> 
> Make sure you always run the `jupyter-book build` command before deploying! 
> It's also a good practice to first remove the `_build` folder built locally and then run it. 



- Publish your book online. Once your book is built, you can share it with others. Most common is to build HTML, and host it as a public website. See [Publish your book online](https://jupyterbook.org/en/stable/start/publish.html).

> **Never** edit the `gh-pages` directly! 


### Build **this** JBook

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


Then, once your notebooks are ready to go, just execute the `deplosy.sh` script. 

```bash
bash deploy.sh
```

### References


To add a reference, you need to first add the `.bit` item to the `references.bib` file within the `notebooks` folder and to mention it in a notebook 
you need to follow the following syntax. 
Assuming your `.bib` item is 

```bib
@article{dwork2014,
  title={The algorithmic foundations of differential privacy},
  author={Dwork, Cynthia and Roth, Aaron and others},
  journal={Foundations and Trends{\textregistered} in Theoretical Computer Science},
  volume={9},
  number={3--4},
  pages={211--407},
  year={2014},
  publisher={Now Publishers, Inc.}
}
```

You would need to have on your notebook:

```python
{cite}`dwork2014`
```

### Equations

You may have a markdown cell directly with a latex block like:

```
\begin{align}
N \times  v = 0 = N \times v^+  - N \times v^- = 
\left[ N \ {-N} \right] 
\begin{bmatrix}
    v^+  \\
    v^-
\end{bmatrix} \qquad
\end{align}
```

that will be numbered. 

### Documentation 

We use definitions, observations etc. from [sphinx-proof](https://sphinx-proof.readthedocs.io/en/latest/syntax.html#observations).

Also, the [dollarmath] and [amsmath] Myst extensions. 

> Example for how to make a note:
```
:::{note}
Here is a note
:::
```

> Example for important messages:
```
::::{important}
:::{note}
This text is **standard** _Markdown_
:::
::::
```

:::{admonition} **Quote**!
:class: tip

My quote
:::


