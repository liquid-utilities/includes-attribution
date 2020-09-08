---
layout: post
title:  Frontmatter Example
date:   2020-09-06 14:57:30 -0800
categories: test attribution
attribution:
  links:
    - text: "GitHub -- Liquid Utilities -- Includes Attribution"
      url: https://github.com/liquid-utilities/includes-attribution
      title: Source code of this project

    - text: "GitHub -- Liquid Utilities -- Includes Translate"
      url: https://github.com/liquid-utilities/includes-translate
      title: Source code for Liquid configured Google translate
---



This is an example post for [`liquid-utilities/includes-attribution`](https://github.com/liquid-utilities/includes-attribution) and demonstrates how FrontMatter similar to...


```yaml
attribution:
  title: Attribution
  class_prefix: attribution
  auto_font_awesome: true

  links:
    - text: "GitHub -- Liquid Utilities -- Includes Attribution"
      url: https://github.com/liquid-utilities/includes-attribution
      title: Source code of this project

    - text: "GitHub -- Liquid Utilities -- Includes Translate"
      url: https://github.com/liquid-utilities/includes-translate
      title: Source code for Liquid configured Google translate
```

... is transpiled into HTML sorta like...


```html
<h2 class="attribution__heading"
    id="heading__attribution"
    >Attribution
</h2>

<ul class="attribution__list">
  <li class="attribution__item">
    <a href="https://github.com/liquid-utilities/includes-attribution"
       title="Source code of this project"
       class="fa-github attribution__link"
       rel="nofollow noreferrer"
       >GitHub -- Liquid Utilities -- Includes Attribution
    </a>
  </li>

  <li class="attribution__item">
    <a href="https://github.com/liquid-utilities/includes-translate"
       title="Source code for Liquid configured Google translate"
       class="fa-github attribution__link"
       rel="nofollow noreferrer"
       >GitHub -- Liquid Utilities -- Includes Translate
    </a>
  </li>
</ul>
```


... which browsers will display as...


