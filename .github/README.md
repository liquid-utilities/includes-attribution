# Includes Attribution
[heading__top]:
  #includes-attribution
  "&#x2B06; Liquid includes that builds Attribution list of links"


Liquid includes that builds Attribution list of links


## [![Byte size of Includes Attribution][badge__main__includes_attribution__source_code]][includes_attribution__main__source_code] [![Open Issues][badge__issues__includes_attribution]][issues__includes_attribution] [![Open Pull Requests][badge__pull_requests__includes_attribution]][pull_requests__includes_attribution] [![Latest commits][badge__commits__includes_attribution__main]][commits__includes_attribution__main] [![includes-attribution Demos][badge__gh_pages__includes_attribution]][gh_pages__includes_attribution]


---


- [:arrow_up: Top of Document][heading__top]

- [:building_construction: Requirements][heading__requirements]

- [:zap: Quick Start][heading__quick_start]

  - [:memo: Edit Your ReadMe File][heading__your_readme_file]
  - [:fountain: Your Layout File][heading__your_layout_file]
  - [:floppy_disk: Commit and Push][heading__commit_and_push]
  - [&#x1F9F0; Usage][heading__usage]

- [&#x1F5D2; Notes][heading__notes]

  - [:symbols: FrontMatter API][heading__frontmatter_api]
  - [:paintbrush: CSS Styling][heading__css_styling]

- [:chart_with_upwards_trend: Contributing][heading__contributing]

  - [:trident: Forking][heading__forking]
  - [:currency_exchange: Sponsor][heading__sponsor]

- [:card_index: Attribution][heading__attribution]

- [:balance_scale: Licensing][heading__license]


---



## Requirements
[heading__requirements]:
  #requirements
  "&#x1F3D7; Prerequisites and/or dependencies that this project needs to function properly"


This repository depends upon [Jekyll][jekyll_rb__home] which is supported by [GitHub Pages][github_docs__github_pages__jekyll], further details about setup can be found from [documentation][jekyll_rb__github_pages] published by the Jekyll maintainers regarding GitHub Pages.


______


## Quick Start
[heading__quick_start]:
  #quick-start
  "&#9889; Perhaps as easy as one, 2.0,..."


This repository encourages the use of Git Submodules to track dependencies


**Bash Variables**


```Bash
_module_name='includes-attribution'
_module_https_url="https://github.com/liquid-utilities/includes-attribution.git"
_module_base_dir='_includes/modules'
_module_path="${_module_base_dir}/${_module_name}"
```


**Bash Submodule Commands**


```Bash
cd "<your-git-project-path>"


git checkout gh-pages

mkdir -vp "${_module_base_dir}"


git submodule add -b main\
              --name "${_module_name}"\
              "${_module_https_url}"\
              "${_module_path}"
```


---


### Your Layout File
[heading__your_layout_file]:
  #your-layout-file
  "&#x26F2; Example post layout modifications"


Example post layout modifications...


**`_layouts/post.html`**


```MarkDown
---
layout: default
license: MIT
source: https://raw.githubusercontent.com/jekyll/minima/v2.0.0/_layouts/post.html
---
<article class="post" itemscope itemtype="http://schema.org/BlogPosting">

  <header class="post-header">
    <h1 class="post-title" itemprop="name headline">{{ page.title | escape }}</h1>
    <p class="post-meta"><time datetime="{{ page.date | date_to_xmlschema }}" itemprop="datePublished">{{ page.date | date: "%b %-d, %Y" }}</time>{% if page.author %} • <span itemprop="author" itemscope itemtype="http://schema.org/Person"><span itemprop="name">{{ page.author }}</span></span>{% endif %}</p>
  </header>

  <div class="post-content" itemprop="articleBody">
    {{ content }}
    {%- if page.attribution -%}
      {%- include modules/includes-attribution/attribution.html -%}
    {%- endif -%}
  </div>

  {% if site.disqus.shortname %}
    {% include disqus_comments.html %}
  {% endif %}
</article>
```


---


### Your ReadMe File
[heading__your_readme_file]:
  #your-readme-file
  "&#x1F4DD; Suggested additions for your ReadMe.md file so everyone has a good time with submodules"


Suggested additions for your _`ReadMe.md`_ file so everyone has a good time with submodules


```MarkDown
Clone with the following to avoid incomplete downloads


    git clone --recurse-submodules <url-for-your-project>


Update/upgrade submodules via


    git submodule update --init --merge --recursive
```


---


### Commit and Push
[heading__commit_and_push]:
  #commit-and-push
  "&#x1F4BE; It may be just this easy..."


```Bash
git add .gitmodules
git add "${_module_path}"


## Add any changed files too


git commit -F- <<'EOF'
:heavy_plus_sign: Adds `liquid-utilities/includes-attribution#1` submodule



**Additions**


- `.gitmodules`, tracks submodules AKA Git within Git _fanciness_

- `README.md`, updates installation and updating guidance

- `_modules_/includes-attribution`, Liquid includes that builds Attribution list of links
EOF


git push origin gh-pages
```


**:tada: Excellent :tada:** your project is now ready to begin unitizing code from this repository!


---


### Usage
[heading__usage]:
  #usage
  "&#x1F9F0; How to utilize this repository"


**Site `_config.yml` configurations**


```YAML
attribution:
  title: Attribution
  class_prefix: attribution
  auto_font_awesome: true
```


**Post FrontMatter**


```yaml
attribution:
  links:
    - text: Google
      href: https://google.com
      title: Link to Google web search engine

    - text: GitHub
      url: https://github.com
      title: Link to GitHub
```


**HTML results**


```html
<h2 class="attribution__heading"
    id="heading__attribution"
    >Attribution
</h2>

<ul class="attribution__list">
  <li class="attribution__item">
    <a href="https://google.com"
       title="Link to Google web search engine"
       class="fa fa-google attribution__link"
       rel="nofollow noreferrer">Google</a>
  </li>

  <li class="attribution__item">
    <a href="https://github.com"
       title="Link to GitHub"
       class="fa fa-github attribution__link"
       rel="nofollow noreferrer">GitHub</a>
  </li>
</ul>
```


______


## Notes
[heading__notes]:
  #notes
  "&#x1F5D2; Additional things to keep in mind when developing"


This repository may not be feature complete and/or fully functional, Pull Requests that add features or fix bugs are certainly welcomed.


---


### FrontMatter API
[heading__frontmatter_api]:
  #frontmatter-api
  "&#x1F523; FrontMatter properties for this project"


- `attribution` object, site or page configuration namespace

  - `title` string, site or page configuration for list heading title
  - `class_prefix` string, site or page configuration for HTML classes
  - `auto_font_awesome` boolean, if `true` then attempt to derive Font Awesome class from link `href` or `url`

  - `links` object list, page configuration
    - `text` string, displayed within HTML `a` tag
    - `title` string, displayed on hover of HTML `a` tag
    - `href` or `url` string, asset that browser will navigate to upon click
    - `rel` string, default `nofollow noreferrer` 
    - `class` string, overwrites parsed Font Awesome by manually assign link class


---


### CSS Styling
[heading__css_styling]:
  #css-styling
  "&#x1f58c; Tips on how to style listed share links"


This project is compatible with Font Awesome, include a `link` to their style sheet for easy icons...


```HTML
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
```


This project utilizes BEM (Block Element Modifier) syntax for HTML/CSS class names, the `block` may be modified via `class_prefix` of page FrontMatter and/or site configuration file.


______


## Contributing
[heading__contributing]:
  #contributing
  "&#x1F4C8; Options for contributing to includes-attribution and liquid-utilities"


Options for contributing to includes-attribution and liquid-utilities


---


### Forking
[heading__forking]:
  #forking
  "&#x1F531; Tips for forking includes-attribution"


Start making a [Fork][includes_attribution__fork_it] of this repository to an account that you have write permissions for.


- Add remote for fork URL. The URL syntax is _`git@github.com:<NAME>/<REPO>.git`_...


```Bash
cd ~/git/hub/liquid-utilities/includes-attribution

git remote add fork git@github.com:<NAME>/includes-attribution.git
```


- Commit your changes and push to your fork, eg. to fix an issue...


```Bash
cd ~/git/hub/liquid-utilities/includes-attribution


git commit -F- <<'EOF'
:bug: Fixes #42 Issue


**Edits**


- `<SCRIPT-NAME>` script, fixes some bug reported in issue
EOF


git push fork main
```


> Note, the `-u` option may be used to set `fork` as the default remote, eg. _`git push fork main`_ however, this will also default the `fork` remote for pulling from too! Meaning that pulling updates from `origin` must be done explicitly, eg. _`git pull origin main`_


- Then on GitHub submit a Pull Request through the Web-UI, the URL syntax is _`https://github.com/<NAME>/<REPO>/pull/new/<BRANCH>`_


> Note; to decrease the chances of your Pull Request needing modifications before being accepted, please check the [dot-github](https://github.com/liquid-utilities/.github) repository for detailed contributing guidelines.


---


### Sponsor
  [heading__sponsor]:
  #sponsor
  "&#x1F4B1; Methods for financially supporting liquid-utilities that maintains includes-attribution"


Thanks for even considering it!


With [![sponsor__shields_io__liberapay]][sponsor__link__liberapay] you may sponsor liquid-utilities on a repeating basis.


Regardless of if you're able to financially support projects such as includes-attribution that liquid-utilities maintains, please consider sharing projects that are useful with others, because one of the goals of maintaining Open Source repositories is to provide value to the community.


______


## Attribution
[heading__attribution]:
  #attribution
  "&#x1F4C7; Resources that where helpful in building this project so far."


- [GitHub -- `github-utilities/make-readme`](https://github.com/github-utilities/make-readme)


______


## License
[heading__license]:
  #license
  "&#x2696; Legal side of Open Source"


```
Liquid includes that builds Attribution list of links
Copyright (C) 2020 S0AndS0

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published
by the Free Software Foundation, version 3 of the License.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
```


For further details review full length version of [AGPL-3.0][branch__current__license] License.



[branch__current__license]:
  /LICENSE
  "&#x2696; Full length version of AGPL-3.0 License"


[badge__commits__includes_attribution__main]:
  https://img.shields.io/github/last-commit/liquid-utilities/includes-attribution/main.svg

[commits__includes_attribution__main]:
  https://github.com/liquid-utilities/includes-attribution/commits/main
  "&#x1F4DD; History of changes on this branch"


[includes_attribution__community]:
  https://github.com/liquid-utilities/includes-attribution/community
  "&#x1F331; Dedicated to functioning code"

[includes_attribution__gh_pages]:
  https://github.com/liquid-utilities/includes-attribution/tree/
  "Source code examples hosted thanks to GitHub Pages!"

[badge__gh_pages__includes_attribution]:
  https://img.shields.io/website/https/liquid-utilities.github.io/includes-attribution/index.html.svg?down_color=darkorange&down_message=Offline&label=Demo&logo=Demo%20Site&up_color=success&up_message=Online

[gh_pages__includes_attribution]:
  https://liquid-utilities.github.io/includes-attribution/index.html
  "&#x1F52C; Check the example collection tests"

[issues__includes_attribution]:
  https://github.com/liquid-utilities/includes-attribution/issues
  "&#x2622; Search for and _bump_ existing issues or open new issues for project maintainer to address."

[includes_attribution__fork_it]:
  https://github.com/liquid-utilities/includes-attribution/
  "&#x1F531; Fork it!"

[pull_requests__includes_attribution]:
  https://github.com/liquid-utilities/includes-attribution/pulls
  "&#x1F3D7; Pull Request friendly, though please check the Community guidelines"

[includes_attribution__main__source_code]:
  https://github.com/liquid-utilities/includes-attribution/
  "&#x2328; Project source!"

[badge__issues__includes_attribution]:
  https://img.shields.io/github/issues/liquid-utilities/includes-attribution.svg

[badge__pull_requests__includes_attribution]:
  https://img.shields.io/github/issues-pr/liquid-utilities/includes-attribution.svg

[badge__main__includes_attribution__source_code]:
  https://img.shields.io/github/repo-size/liquid-utilities/includes-attribution


[jekyll_rb__home]:
  https://jekyllrb.com/
  "Jekyll home page"

[jekyll_rb__github_pages]:
  https://jekyllrb.com/docs/github-pages/
  "Jekyll documentation for GitHub Pages setup"

[github_docs__github_pages__jekyll]:
  https://docs.github.com/en/github/working-with-github-pages/setting-up-a-github-pages-site-with-jekyll
  "GitHub Pages documentation on Jekyll setup"

[sponsor__shields_io__liberapay]:
  https://img.shields.io/static/v1?logo=liberapay&label=Sponsor&message=liquid-utilities

[sponsor__link__liberapay]:
  https://liberapay.com/liquid-utilities
  "&#x1F4B1; Sponsor developments and projects that liquid-utilities maintains via Liberapay"

