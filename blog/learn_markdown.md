**[RETURN BACK](../blog.html)**|[Homepage](../index.html)|[Curriculum Vitae]()|[Publication](../publication.html)|[Fun Projects](../fun_proj.html)|**[Blog](../blog.html)**|


# Markdown Tips and Tricks I Used

Markdown is a lightweight markup language with plain text formating syntax <sup>[1]</sup>. I prefer using Markdown to write simple blogs. In this blog, I will introduce some useful tips and tricks I learned.

#### Editor

[Visual Studio Code](https://code.visualstudio.com/) is my main editor to write Markdown. And the suggested extensions includes markdownlint, markdown+math (mdmath), and markdown preview enhanced. mdmath helps to render Latex math. Markdown preview enhanced provides one useful functionality of HTML export I appreciate most. The following images show how to export the HTML file  in visual studio code.

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

#### Math typesetting

Katex inside the mdmath allows Visual Studio Code to reanding Tex math in a markdown file. 

**Inline math**
Einstein mass-energy equation: $E = mc^2$.

**Display math**

The Quadratic Formula: 

$$ x = \frac{-b \pm \sqrt{b^2 -4ac}}{2a} $$
The Cauchy's Integral Formula:

$$ f(a) = \frac{1}{2\pi i}\oint\frac{f(z)}{z - a}dz$$

However, the exported HTML file via Markdown Preview Enhanced extension uses the local .css file to render Tex math, as shown in the follow codes:

``` html
<link rel="stylesheet" href="file:///C:\Users\username\.vscode\extensions\shd101wyy.markdown-preview-enhanced-0.3.2\node_modules\@shd101wyy\mume\dependencies\katex\katex.min.css">
```

The local katex.min.css can not be found after uploaded to the web server. To solve this problem, I uploaded the katex folder along with the exported HTML file and used a relative path.

``` html
<link rel="stylesheet" href="./katex/katex.min.css">
```

**[RETURN BACK](../blog.html)**

#### References

1. [Wikipedia: Markdown](https://en.wikipedia.org/wiki/Markdown)

2. [认识与入门Markdown](https://sspai.com/post/25137)

3. [Tips and tricks that you probably don't know with the Github Markdown in readme.md files](https://ourcodeworld.com/articles/read/162/tips-and-tricks-that-you-probably-don-t-know-with-the-github-markdown-in-readme-md-files)
