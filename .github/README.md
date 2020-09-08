# Includes Translate
[heading__title]:
  #includes-translate
  "&#x2B06; Top of ReadMe File"


Liquid utility that includes Google Translate HTML and JS code


## [![Byte size of includes-translate][badge__master__includes_translate__source_code]][includes_translate__master__source_code] [![Open Issues][badge__issues__includes_translate]][issues__includes_translate] [![Open Pull Requests][badge__pull_requests__includes_translate]][pull_requests__includes_translate] [![Latest commits][badge__commits__includes_translate__master]][commits__includes_translate__master] [![Includes Translate Demos][badge__demo__includes_translate]][demo__includes_translate]


------


- [:arrow_up: Top of ReadMe File][heading__title]

- [:zap: Quick Start][heading__quick_start]

  - [:memo: Edit Your ReadMe File][heading__your_readme_file]
  - [:factory: Utilize Includes Translate][heading__utilize]
  - [:floppy_disk: Commit and Push][heading__commit_and_push]

- [&#x1F5D2; Notes][heading__notes]

- [:card_index: Attribution][heading__attribution]

- [&#x2696; License][heading__license]

------


## Quick Start
[heading__quick_start]:
  #quick-start
  "&#9889; Perhaps as easy as one, 2.0,..."


Change current working directory to the repository that will be utilizing this project, and checkout your `gh-pages` branch if available...


```Bash
cd ~/git/hub/__org_name__/__repository__


git checkout gh-pages
```


Add this project as a Git submodule...


```
mkdir -vp _includes/modules


git submodule add\
 -b master --name "includes-translate"\
 "https://github.com/liquid-utilities/includes-translate.git"\
 "_includes/modules/includes-translate"
```


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


### Utilize Includes Translate
[heading__utilize]:
  #utilize-includes-translate
  "&#x1F3ED; How to make use of this submodule within another project"


Include the Liquid script within a Layout file...


**`_layouts/default.html`**


```HTML
<!--
  Source: https://raw.githubusercontent.com/jekyll/minima/v2.5.0/_layouts/default.html
  License: MIT
  Modified_For: liquid-utilities/includes-translate
-->
<!DOCTYPE html>
<html lang="{{ page.lang | default: site.lang | default: "en" }}">
  {%- include head.html -%}

  <body>
    {%- include header.html -%}

    <main class="page-content" aria-label="Content">
      <div class="wrapper">
        {% include modules/includes-translate/includes-translate.html %}
        {{ content }}
      </div>
    </main>

    {%- include footer.html -%}

  </body>

</html>
```


> Note; depending upon theme choice it may be more organized to include code from this project within a `header.html` file, eg. _`_includes/header.html`_


Define site defaults...


**`_config.yaml`**


```YAML
page:
  translate_id: translate_selection
  language: en
  translate_callback: google_translate_callback
  auto_translate: false
```


Individual posts may overwrite site defaults...


**`_posts/2019-08-16-hello-lifeforms.md`**


```YAML
---
layout: post
title: "Hello Lifeforms"
date: 2019-08-16 13:58:05 -0700
categories: posts

language: es
auto_translate: true
---


Ejemplo de contenido de la página que se traducirá.
```


___


### Commit and Push
[heading__commit_and_push]:
  #commit-and-push
  "&#x1F4BE; It may be just this easy..."


```Bash
git add README.md
git add .gitmodules
git add _config.yaml
git add _includes/modules/includes-translate
git add _layouts/default.html


## Add any changed files too


git commit -F- <<'EOF'
:heavy_plus_sign: Adds `liquid-utilities/includes-translate#1` submodule



**Additions**


- `.gitmodules`, tracks submodules AKA Git within Git _fanciness_

- `README.md`, updates installation and updating guidance

- `_layouts/modules/includes-translate`, builds list of pages for a named collection
EOF


git push origin gh-pages
```


**:tada: Excellent :tada:** your site is now ready to begin unitizing code from this repository!


___


## Notes
[heading__notes]:
  #notes
  "&#x1F5D2; Additional things to keep in mind when developing"


`{% include %}` parameters, and `_config.yaml` or `_posts`/`_pages` Frontmatter, may accept the following customizations;


- `translate_id` string, HTML `id` that Google Translate script should inject `option` and `select` elements into; defaults to `"translate_selection"`

- `language` string, language two letter code that pages are written in; defaults to `"en"`

- `translate_callback` string, name of JavaScript function that Google Translate should call when a language `option` is chosen; defaults to `"google_translate_callback"`

- `auto_translate` boolean, if `true` will add JavaScript function and event listener that will automatically select preferred language if detectable; defaults to `false`

- `disable_translate` boolean, if `true` will disable **all** features of `includes-translate` within page/post or entire site; defaults to `false`


------


Because this project is a script that may be included, it is possible to translate select pages or posts instead of modifying site template files, eg...


**`_posts/2020-03-05-test-automatic-translation.md`**


```YAML
---
layout: post
title: "Test Automatic Translation"
date: 2020-03-05 12:58:05 -0700
categories: posts

translate_id: translate_selection
translate_callback: google_translate_callback
language: ja
auto_translate: true
---
{% include modules/includes-translate/includes-translate.html %}


翻訳するページコンテンツの例。
```


___


## Attribution
[heading__attribution]:
  #attribution
  "&#x1F4C7; Resources and individuals that where helpful in building this project so far."


- [W3 Schools -- HTML Language Code Reference](https://www.w3schools.com/tags/ref_language_codes.asp)

- [W3 Schools -- How to Google Translate](https://www.w3schools.com/howto/howto_google_translate.asp)

- [StackOverflow -- JavaScript for detecting browser language preference](https://stackoverflow.com/questions/1043339)

- [StackOverflow -- How do I change an HTML selected `option` using JavaScript?](https://stackoverflow.com/questions/10911526)

- [StackOverflow -- How do I change an HTML selected `option` using JavaScript?](https://stackoverflow.com/questions/10911526)

- [StackOverflow -- How can I trigger an `onchange` event manually?](https://stackoverflow.com/questions/2856513)

- [StackOverflow -- Adding Google Translate to a web site](https://stackoverflow.com/questions/12243818)


___


## License
[heading__license]:
  #license
  "&#x2696; Legal bits of Open Source software"


Legal bits of Open Source software


```
Includes Translate documentation on how things like this could be utilized
Copyright (C) 2020  S0AndS0

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published
by the Free Software Foundation; version 3 of the License.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
```



[badge__commits__includes_translate__master]:
  https://img.shields.io/github/last-commit/liquid-utilities/includes-translate/master.svg

[commits__includes_translate__master]:
  https://github.com/liquid-utilities/includes-translate/commits/master
  "&#x1F4DD; History of changes on this branch"


[includes_translate__community]:
  https://github.com/liquid-utilities/includes-translate/community
  "&#x1F331; Dedicated to functioning code"

[includes_translate__gh_pages]:
  https://github.com/liquid-utilities/includes-translate/tree/gh-pages
  "Source code examples hosted thanks to GitHub Pages!"


[badge__demo__includes_translate]:
  https://img.shields.io/website/https/liquid-utilities.github.io/includes-translate/index.html.svg?down_color=darkorange&down_message=Offline&label=Demo&logo=Demo%20Site&up_color=success&up_message=Online

[demo__includes_translate]:
  https://liquid-utilities.github.io/includes-translate/index.html
  "&#x1F52C; Check the example collection tests"


[badge__issues__includes_translate]:
  https://img.shields.io/github/issues/liquid-utilities/includes-translate.svg

[issues__includes_translate]:
  https://github.com/liquid-utilities/includes-translate/issues
  "&#x2622; Search for and _bump_ existing issues or open new issues for project maintainer to address."


[badge__pull_requests__includes_translate]:
  https://img.shields.io/github/issues-pr/liquid-utilities/includes-translate.svg

[pull_requests__includes_translate]:
  https://github.com/liquid-utilities/includes-translate/pulls
  "&#x1F3D7; Pull Request friendly, though please check the Community guidelines"


[badge__master__includes_translate__source_code]:
  https://img.shields.io/github/repo-size/liquid-utilities/includes-translate

[includes_translate__master__source_code]:
  https://github.com/liquid-utilities/includes-translate/
  "&#x2328; Project source!"
