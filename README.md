# Blog
A repository for DeepLearnPhysics group [Blog](https://deeplearnphysics.org/Blog) webpage.
The `master` branch holds static HTML files generated by [Pelican](http://docs.getpelican.com/en/stable/) with [flex theme](https://github.com/alexandrevicenzi/Flex). We use [pelican-ipynb](https://github.com/danielfrg/pelican-ipynb) plugin to easily turn a juypyter notebook into a blog.
The `develop` branch holds source code to generate the website.

## Requirement
You need python packages:
* `pelican >= 3.5.0`
* `markdown >= 2.6.9`

Also for `pelican-ipynb` plug-ins you need:
* `jupyter >= 1.0`
* `ipython >= 4.0`
* `nbconvert >= 4.0`

If you find the above requirement for [pelican-ipynb](https://github.com/danielfrg/pelican-ipynb#Requirements) changed, please let us know or update it above!

## How to contribute (develop)
For aweome you to help development, follow the following steps. I split into three steps: **installation**, **compilation**, **development**, and **publish**.

### Installation
1. Join [web-blog](https://github.com/orgs/DeepLearnPhysics/teams/web-blog) github team
2. Install [Pelican](http://docs.getpelican.com/en/stable/) ... here's [quick start](http://docs.getpelican.com/en/stable/quickstart.html#).
3. Clone the repo: `git clone git@github.com:DeepLearnPhysics/Blog`.
4. Make sure you are on the `develop` branch by `git branch`
5. Enable plican-ipynb plugin:
```
cd plugins/ipynb
git submodule init
git submodule update
cd -
```
### Compilation
By compilation we mean to generate static HTMLs. This is fairly simple:
1.  `make html`

### Development
Our development work is a process of modify-compile-check. The **first to-do** is:
1. Open `pelicanconf.py` and **uncomment** the line `#SITEURL = ''`. This generates HTMLs to be viewed locally.
2. `make devserver` then access `localhost:8000` on your browser. This runs a virtual pelican web server on your machine and allows you to browse the updated website contents all on your laptop.
3. Make modifications you wish to make. `contents` directory is where you make a _blog post_.
4. `make html` will update your local static website.

### Publish
After you finish your development work, if you want to publish your change on our website, you have to push your changes.
1. Open `pelicanconf.py` and **comment out** the line `SITEURL = ''`. This generates HTMLs to be viewed on the shared remote server.
2. `make html` and if you are running a local virtual server, `make stopserver`.
3. Commit your changes to the develop branch.
4. `git checkout master` ... the master branch holds static website contents.
5. `cp -r output/* ./`
6. `git add .`
7. `git commit -m "your message"`
8. `git push`

Done!

---

### Jupyter notebook
The following is an instruction copied from [pelican-ipynb](https://github.com/danielfrg/pelican-ipynb) plugin repository.

Write the post using the Jupyter Notebook interface, using markdown, equations, etc.

Place the `.ipynb` file in the content folder and create a new file with the
same name as the ipython notebook with extension `.ipynb-meta`.
For example if you have `my_post.ipynb` create a `my_post.ipynb-meta`.

The `.ipynb-meta` should have the markdown metadata (note the empty line at the end, you need that)
of a regular pelican article:

```
Title:
Slug:
Date:
Category:
Tags:
Author:
Summary:

```

---

### Copyright and license

It is under [the MIT license](/LICENSE).
