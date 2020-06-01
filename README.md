[![Build Status](https://travis-ci.org/Sage-Bionetworks/synapseDocs.svg?branch=master)](https://travis-ci.org/Sage-Bionetworks/synapseDocs)

# Synapse Documentation

This is a documentation site for [Synapse](https://www.synapse.org). Synapse is an open source software platform that data
scientists use to carry out, track, and communicate their research in real time.

## Contributing Guide

- Assign GitHub issue to yourself to track work in progress and prevent duplicate efforts. If you don't know what you should work on, look for things tagged with `help-wanted` or `good-first-issue`.
- Create a [feature branch](https://guides.github.com/introduction/flow/) from the `gh-pages` branch to make your changes or new contribution.
- Using a Markdown editor lke Typora, VS Code, or Sublime Text will allow you to visualize how your Markdown looks locally. You can also make your changes directly in the GitHub website or any other text editor.
- Open a [pull request](https://help.github.com/en/articles/about-pull-requests) against the `gh-pages` branch and [request a review](https://help.github.com/en/articles/requesting-a-pull-request-review).
- Merge requires approving review by a repository administrator.

Synapse Docs is generated using [Github Pages](https://pages.github.com/). Follow the standard [Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) guide.

To build locally, follow the instructions found [here](https://help.github.com/en/articles/testing-your-github-pages-site-locally-with-jekyll). You will need Jekyll, Ruby, and the Ruby package manager, Bundler.

Internal development can be performed by branching from `gh-pages` to your own feature branch, making changes, pushing the branch to this repository, and opening a pull request. Pull requests against the `gh-pages` branch require a review before merging.

### Categories

Pages are described by categories. These are stored in a Jekyll collection at [_categories](_categories/). The architecture of this repo is described in the [Jekyll collection documentation](https://jekyllrb.com/docs/collections/).  The content that describes each category is defined in a YAML header in a file in that directory. The categories avaiable for reference elsewhere are named as the file or as present in the 'name' field of the YAML header.

For example, if you want to create a page with a governance category, you would look in [_categories/governance.md](_categories/governance.md) in the 'name' field and use that value.

### Creating a page

To create a page using the article layout, start by specifying at the very beginning the title, layout, excerpt, and category in the YAML front matter. The title and excerpt will show up in the article's user guide thumbnail and the category tag will be used to sort the article into its corresponding user guide tab. If no category is specified, it will default into the "How-To" tab. 

Note that the front matter needs to be enclosed between three dashed lines to work properly.

```
---
title: Name of page here
layout: article
excerpt: A blurb about this page that will show up as a description in the user guide.
category: intro 
---
```

### Style Guide 

- The title in the [YAML front matter block](https://jekyllrb.com/docs/front-matter/) will populate as a level 1 header. Therefore, please do not supply a H1 header in the markdown! 
```
---
title: "Wikis"
layout: article
excerpt: Create wikis to provide narrative content for your research.
category: how-to
---

Start of short summary about wikis.
```
- Article content should begin with a short summary describing what the page is about.
- Synapse entity types or features are only emphasized in the top-most Overview section on each page. e.g. `File` , `Project` 
  - In all subsequent sections, these entity types or features are referred to as proper nouns and capitalized. e.g. File, Project
- Synapse buttons are emphasized as **bold**. e.g Click **File Tools**.

### Using alert tags

There are four types of alert highlighting to inform users: note, tip, warning, and important. You can insert an alert by using any of the following code in a markdown file.
```
{% include note.html content="This is a note." %}

{% include tip.html content="This is a tip." %}
```
To include new paragraphs, just add the `<br/>` tag within the content, like this:
```
{% include warning.html content="This is a warning. `<br/>` This is the second line of the warning." %}

{% include important.html content="This is for an important message." %}
```

### Adding a table

To add a table, use Liquid to call on the markdown-table css class. Then use the standard markdown table format.
```
{:.markdown-table}
| Header 1 | Header 2 |
| --- | --- |
| content | content |
| content | content |
```

### Inserting an image

Images can be inserted using either Markdown or HTML, it all depends on your preference. The examples below will display the same thing:
```
![alt text](/assets/images/image1.jpg)
<img src="/assets/images/image1.jpg" alt="alt text">
```

### Inserting code 

The docs may contain a high level overview of a feature, but should link to the [Python docs](https://python-docs.synapse.org/build/html/index.html) and [synapser](https://r-docs.synapse.org/articles/synapser.html) docs, pointing to the relevant anchor, for code examples. This is to ensure code is validated with the client release cycles. 

### Inserting relative links

A page may link to other pages within the documentation site. To do this, use a `link` Liquid tag to properly render the URL:

```
[link text]({{ site.baseurl }}{% link _articles/getting_started.md %})
```

If the link uses an anchor to jump to a specific part of the page, it must go outside the `link` tag:

```
[Annotations]({{ site.baseurl }}{% link _articles/annotation_and_query.md %}#adding-annotations)
```

### Linking to Synapse client documentation 

Code examples in the documentation should be minimal. Preferably, links are provided to the Python, R, commandline and REST documentation. 
- [r-docs.synapse.org](https://r-docs.synapse.org/)
- [python-docs.synapse.org](https://python-docs.synapse.org/)
    - [command line client documented in Python docs](https://python-docs.synapse.org/build/html/CommandLineClient.html?highlight=command%20line) 
- [rest-docs.synapse.org/rest](http://rest-docs.synapse.org/rest/)

## License

Distributed under the Eclipse Public License, the same as Clojure.
