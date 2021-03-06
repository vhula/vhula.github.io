---
layout: post
title:  "Myself getting started with Jekyll"
date:   2020-03-31
categories: jekyll
tags: jekyll getting-started
---

# Installation

Installation steps are available at [Jekyll's quickstart page][jekyll-docs].

The Jekyll can be installed on most operating systems.

## Installing via Bash on Windows 10

### Install Linux Subsystem

More details are available at [Windows Subsystem for Linux Installation Guide for Windows 10][wsl-install-win10]

1. Open PowerShell as Administrator and run:
    ```
    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
    ```
1. Restart your computer when prompted.

### Install Ubuntu Linux

More details are available at [Windows Subsystem for Linux Installation Guide for Windows 10][wsl-install-win10]

1. Open the Microsoft Store and search for *Ubuntu 18.04 LTS*.
1. Click **Install**.
1. Launch Ubuntu and [set up a user account][ubuntu-initialize-win10].

### Set up Jekyll environment

1. Open PowerShell as Administrator and run:

    ```bash```
1. Update repo lists and packages:

    ```sudo apt-get update -y && sudo apt-get upgrade -y```
1. Install Ruby from the [BrightBox repo][bright-box-ubuntu]:
   ```
   sudo apt-add-repository ppa:brightbox/ruby-ng
   sudo apt-get update
   sudo apt-get install ruby2.5 ruby2.5-dev build-essential dh-autoreconf
   ```
1. Update Ruby gems:

    ```sudo gem update```
1. Install [Jekyll][jekyll-docs] and [Bundler][bundler-home]:

    ```sudo gem install jekyll bundler```
1. Check if Jekyll is installed properly:

    ```jekyll -v```

**Warning**. If you see a warning message similar to "*operating_system.rb:10: warning: constant gem::configmap is deprecated*",
you may try to [downgrade the RubyGems][rubygems-downgrade] by running:
    ```gem update --system 3.0.6```

# Generating a site

Navigate to the directory that will contain a site and run this command

```jekyll new .```

It generates the default site.

# Running a site on your local machine

The site may be served by running the jekyll command

```jekyll serve```

However, it's best to use the [bundler][bundler-home] to avoid dependencies' versioning nightmare

```bundle exec jekyll serve```

# Jekyll site structure explained

A [directory structure of Jekyll site][jekyll-dir-structure]:

File/Directory  |  Description
--|--
```_config.yml```  |  Contains [configuration][jekyll-configuration] data
```_drafts```  |  This directory contains files that are unpublished posts (drafts). The files name format: ```title.MARKUP```, e.g. ```draft-post.md```. To preview the site with drafts, run ```jekyll serve --drafts```
```_posts```  |  This directory contains files that are published posts. The file name format: ```YEAR-MONTH-DAY-title.MARKUP```, e.g. ```2020-03-14-getting-started-with-jekyll.markdown```. A markdown file may contain permalinks that provide the output path for pages. The date and format of the post is determined by the file's name only
```_layouts```  |  This directory contains files that are templates for the posts.  The layout of the post should be defined in the [front matter][front-matter-link], which is a simple YAML block at the beginning of the post file. The front matter must be placed at the beginning of the file and wrapped by triple-dashed lines
```_includes```  |  These are the files that can be included in layouts and posts. The inclusion is possible by using a [liquid][liquid-home] tag ```{% raw %}{%include file.ext %}{% endraw %}```
```_data```  |  This directory contains data that is supposed to be placed in well-formatted files, e.g. ```.yml```, ```.json```, ```.csv```. The Jekyll can autoload these formats. The data from ```filename.yml``` is accessible via ```site.data.filename``` reference
```_sass```  |  Jekyll generates ```main.css``` based on ```main.scss```. The generated file is used by a site to configure styles. This directory contains [sass][sass-home] partials that may be imported into the ```main.scss```
```_site```  |  This directory contains the generated site
```.jekyll-metadata```  |  This file is used by Jekyll to track modifications since the site was last built.
```index.html```, ```index.md``` and other HTML, Markdown files |  These files will be transformed by Jekyll if they contain the [front matter][front-matter-link] section
Other files and directories  |  All other files that may be used by the site, e.g. images, styles, scripts

# Configuring Jekyll site

The [configuration][jekyll-configuration] is placed in the ```_config.yml``` file. There are properties that are generated by Jekyll by default.

[jekyll-docs]: https://jekyllrb.com/docs/
[wsl-install-win10]: https://docs.microsoft.com/en-us/windows/wsl/install-win10?redirectedfrom=MSDN
[ubuntu-install-win10]: https://docs.microsoft.com/en-us/windows/wsl/install-win10?redirectedfrom=MSDN
[ubuntu-initialize-win10]: https://docs.microsoft.com/en-us/windows/wsl/initialize-distro
[bright-box-ubuntu]: https://www.brightbox.com/docs/ruby/ubuntu/
[bundler-home]: https://bundler.io/
[rubygems-downgrade]: https://github.com/rubygems/rubygems/issues/3068#issuecomment-574775885
[bundler-home]: https://bundler.io/
[jekyll-dir-structure]: https://jekyllrb.com/docs/structure/
[jekyll-configuration]: https://jekyllrb.com/docs/configuration/
[liquid-home]: https://shopify.github.io/liquid/
[sass-home]: https://sass-lang.com/
[front-matter-link]: https://jekyllrb.com/docs/front-matter/
