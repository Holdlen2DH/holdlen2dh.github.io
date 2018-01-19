# Markdown Tips and Tricks I Used

Markdown is a lightweight markup language with plain text formating syntax <sup>[1]</sup>. I prefer using Markdown to write simple blogs. In this blog, I will introduce some useful trips and tricks I learned.

#### Editor

[Visual studio code](https://code.visualstudio.com/) is my main editor to write Markdown. And the suggested extensions includes markdownlint, markdown+math, and markdown preview enhanced. Mardown + math help to render Latex math. Markdown preview enhanced provides one useful functionality of HTML export I appreciate most. The following images show how to export the HTML file  in visual studio code.

<p align = "center">
    <img src="./learn_markdown/mpe_openpreview.jpg" width="400" title="Open preview">
</p>
<p align = "center">
    <img src="./learn_markdown/mpe_exporthtml.jpg" width="400" title="HTML export">
</p>

#### Embedding images

There are two ways to add an image <sup>[3]</sup>. 
**Markdown** 
Use markdown syntax to add an image.

``` markdown
![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)
```

Also you can add an local image by setting the link with the image's relative path.

``` markdown
![Image of Github Markdown](./learn_markdown/github_markdown.jpg)
```

![Image of Github Markdown](./learn_markdown/github_markdown.jpg)

**HTML**

``` html
<p align="center">
    <img src="./learn_markdown/github_markdown.jpg" width="256" title="The First Lady of the Internet">
</p>
```

<p align = "center">
    <img src="./learn_markdown/lena.jpg" width="256" title="The First Lady of the Internet">
</p>

$$ c^2 $$

#### References

1. [Wikipedia: Markdown](https://en.wikipedia.org/wiki/Markdown)

2. [认识与入门Markdown](https://sspai.com/post/25137)

3. [Tips and tricks that you probably don't know with the Github Markdown in readme.md files](https://ourcodeworld.com/articles/read/162/tips-and-tricks-that-you-probably-don-t-know-with-the-github-markdown-in-readme-md-files)
