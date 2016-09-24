# Decentralized Data Workshops

This git repository contains Workshop material on distributed version control and distributed data systems. The workshops were created as part of the [Dat Jawn](http://datjawn.com) project at [Code for Philly](http://codeforphilly.org) in autumn 2016. 

For more info about the workshops, and to see the rendered content of this repository, go to https://codeforphilly.github.io/decentralized-data/ or read [index.md](./index.md)

## Information for Contributors and Maintainers of these Tutorials

Our tutorials use only one branch, `gh-pages`, for both development and hosting.  This includes all our own custom content as well as the [pool/hyde](https://github.com/poole/hyde) jekyll template.  **Submit all pull requests, etc. against the `gh-pages` branch.**  We do not use a `master` branch.

## How to structure tutorials in the curriculum

Read the [Template Curriculum](http://flyingzumwalt.github.io/jekyll-curriculum-template/curriculum-template/) for info about how to structure your courses, modules, and activities.

### Hosting your curriculum on Github Pages

It's easy to host your curriculum on Github pages. Github's help pages about [Using Jekyll as a static site generator with GitHub Pages](https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/) should provide the info you need to get going.

### Applying Styles and templates

There are lots of Jekyll Themes out there that you can apply to your curriculum.  This template is set up to work with the [pool/hyde](https://github.com/poole/hyde) theme, but using it with another theme is relatively easy.

If you already have your curriculum in a git repository, you can apply your content on top of a template like this (assuming your curriculum content is in the master branch). _Note: you will probably have to resolve some merge conflicts when you run `git merge master`_

```
git remote add hyde git@github.com:poole/hyde.git
git fetch hyde
git checkout -b gh-pages hyde/master
git merge master  
git commit -m"apply curriculum content on top of hyde"
```

### Serve your Curriculum anywhere with Jekyll

In the root of your curriculum content, run

```
bundle install
bundle exec jekyll serve
```

See the [Setting up your GitHub Pages site locally with Jekyll](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/) for more info and troubleshooting.

## Authors

**Matt Zumwalt**
- <https://github.com/flyingzumwalt>
- <https://twitter.com/flyingzumwalt>

**Jadrian Miles**
- <https://github.com/jadrian>


## License

Open sourced under the [MIT license](LICENSE.md).
