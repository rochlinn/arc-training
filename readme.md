## Using this template...

To see a working example, visit [https://csc-ubc-okanagan.github.io/R-Fundamentals/](https://csc-ubc-okanagan.github.io/R-Fundamentals/)

### Prerequisites

This template requires the `rmarkdown` package:

```
install.packages("rmarkdown")
```

You should probably also have some sort of `Tex` option available. The simplest is just to install the `tinytex` package:

```
install.packages("tinytex")

tinytex::install_tinytex()
```

### Template files & folders

| File           | Description                                                  |
| -------------- | ------------------------------------------------------------ |
| _site.yml      | Contains front matter content, such as output format, site title, and menu structure. Update this file with your workshop title and preferred menu structure. There is an existing link to the 'resources' page. |
| footer.html    | Custom footer content.                                       |
| header.html    | Custom header content.                                       |
| index.Rmd      | The landing page of the site. Intended to house a description, schedule, and links to any files needed. The `Files` section is auto-populated when files are deposited in the directory `files` by way of a script in the `scripts` directory. |
| readme.md      | This file.                                                   |
| resources.Rmd  | The resources page, intended to house a list of additional resources for attendees. Update as needed. |
| styles.css     | Custom styling.                                              |
| Template.Rproj | The R Project file. You can ignore this.                     |



| Directory | Description                                                  |
| --------- | ------------------------------------------------------------ |
| files/    | Houses any files you would like attendees to be able to download during the workshop. |
| images/   | Houses the CSC logo. If using additional images, best to place them here too. |
| scripts/  | Custom scripts. Currently one script that looks for any files in the directory `files`, pulls their location, name, and file size and then populates a list under the header `Files` in `index.Rmd` |

### Instructions

#### First things first

Open the file `Template.Rproj` This will provide you with a workding directory in RStudio with all of the above files.

In `RStudio` open `_site.yml` and under `navbar` > `title` update the text with your workshop title. This is the text that will appear in the header of the website. `yml` is very specific about spacing, so be careful when updating this file.

```
navbar:
  title: "YOUR TITLE HERE"
```

Open `index.Rmd` and populate it with the basic information required for your workshop. Don't worry about the section under the header `Files`.

If you wish to include any files (slides, datasets etc), place these in the `files` directory. A list with links will be auto-generated when the site is built and placed under the header `Files` in `index.Rmd`

#### Write your content

Go to town building out your content. Each page should be it's own `.Rmd` file. You can either do this yourself by navigating to your `Terminal` in `RStudio`:

```
touch youNewFile.Rmd
```

or by going to `file` > `New File` > `R Markdown...`

#### Page titles

The `title` will be the first `H1` header on your page. The `pagetitle` is what will show in the browser's tab.

If going the former route, the first thing you want to do is provide your page with a `title` and `pagetitle` with a bit of `yaml`, like so

```
---
title: yourTitleHere
pagetitle: yourPageTitleHere
---

## Add a subheader if desired

Start writing your content here.
```

If going the latter route, don't worry too much about the prompting, this is just there to get some auto generated `yaml` up and going for you. Once your new `.Rmd` doc is created with some `yaml` and placeholder content, delete everything, and use the code snippet above, replacing `yourTitleHere` and `yourPageTitleHere` with whatever you want to call your page!

#### Headers

Start with a second level header - first level headers are used elsewhere by the conversion process from `markdown` to `html` - as seen above with the `title` in the `yaml`.

#### File names

When `knit` from `markdown` to `html` the files are processed alphabetically. So, files should be numbered in the order in which you wish to  have them compiled. `index.Rmd` will be compiled first by default and does not require numbering, but subsequent files should look like:

- index.Rmd
- 01_FirstFile.Rmd
- 02_SecondFile.Rmd

The `resources` file should be rendered last, and so will need to be renamed accordingly once all other content is complete.

#### Menu structure

Site navigation is controlled within the `_site.yml` file. You'll see content pre-populated for the `resources` page like so:

```
navbar:
  title: "YOUR TITLE HERE"
  left:
    - text: "Resources"
      href: resources.html
```

Additional menu items can be added before the resources page, where `text` is what will appear in the menu in the header and `href` will link to the appropriate file. So, when your `resources` page is updated to include a number in it's name, the `href` content here will need to be updated. Adding more pages would look something like this:

```
navbar:
  title: "YOUR TITLE HERE"
  left:
    - text: "First Page"
      href: 01_FirstFile.html
    - text: "Second Page"
      href: 02_SecondFile.html
    - text: "Resources"
      href: 03_resources.html
```

Remember, `yaml` cares about spacing  - indent two spaces after `left:` before adding your `-` and ensure that `text` and `href` are vertically left aligned.

Also, note that while right now our files end in `.Rmd` once rendered they will be `html` files, hence the `href` pointing to an `html` extension.

##### Sub menus

If you would like sub menus, use the following convention, with an additional two spaces

```
navbar:
  title: "YOUR TITLE HERE"
  left:
    - text: "Menu title"
      - text: "First Page"
        href: 01_FirstFile.html
    	- text: "Second Page"
        href: 02_SecondFile.html
    - text: "Resources"
      href: 03_resources.html
```

This will provide you with a dropdown menu titled `Menu title`, with two links in the dropdown. The `resources` link will sit at the same level as the `Menu title`.

### Building your site

Once everything is ready, or you want to review what your content is looking like when rendered to html, simply head to the `Build` panel in `RStudio` (upper right), and select `Build Website`. This will create a folder in your working directory called `docs` containing your website. When you're happy with it, you can upload it to GitHub and publish it!

