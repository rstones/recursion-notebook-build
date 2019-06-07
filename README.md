## How to create and build a Jupyter Book

1. Install jupyter-book from the github repo (the version on pypi doesn't seem to work properly)
```bash
pip install git+https://github.com/jupyter/jupyter-book.git
```
2. Create a folder notebooks/ containing the jupyter notebook you wish to convert
3. Create the book
```bash
jupyter-book create <book-title> --content-folder notebooks/
```
4. Build the book
```bash
jupyter-book build <book-title>
```
5. View a local version of the book using a Jekyll server inside a Docker container
```bash
docker pull emdupre/jupyter-book
docker run docker run --rm --security-opt label:disable -v <path-to-book-folder-inside-repo>:/srv/jekyll -p 4000:4000 -it -u 1000:1000 emdupre/jupyter-book bundle exec jekyll serve --host 0.0.0.0
``` 
