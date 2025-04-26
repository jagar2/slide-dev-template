---
# You can also start simply with 'default'
theme: ./theme
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: ./assets/title_image.png
# some information about your slides (markdown enabled)
title: Add Title Here
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: fade-out
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true

# open graph
# seoMeta:
#  ogImage: https://cover.sli.dev
---

# Add Title Here

## Joshua C. Agar

### Drexel University

#### Department of Mechanical Engineering and Mechanics

#### {{ new Date().toLocaleDateString() }}

<!-- <div @click="$slidev.nav.next" class="mt-12 py-1" hover:bg="white op-10">
  Press Space for next page <carbon:arrow-right />
</div> -->

<div class="abs-br m-6 text-xl">
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
layout: mainer
title-text: "What is Slidedsfsdfsdfdsfdsfv?"
---

## Test Azo Sans Font
## Test Malonet Font
### Test Papernotes Font dfssdf
#### Test Anthonio Font
##### Test Papernotes Sketch Font
###### Test Random Wednesday Font

- 📝 **Text-based** - focus on the content with Markdown, and then style them later
- 🎨 **Themable** - themes can be shared and re-used as npm packages
- 🧑‍💻 **Developer Friendly** - code highlighting, live coding with autocompletion
- 🤹 **Interactive** - embed Vue components to enhance your expressions
- 🎥 **Recording** - built-in recording and camera view
- 📤 **Portable** - export to PDF, PPTX, PNGs, or even a hostable SPA
- 🛠 **Hackable** - virtually anything that's possible on a webpage is possible in Slidev

<p style="text-align: center;">
  Read more about [Why Slidev?](https://sli.dev/guide/why)
</p>

---
layout: layout-body-w-text-subtitle
titleText: "My Title"
subtitleText: "My Subtitle"
image: "https://user-images.githubusercontent.com/13499566/138951075-018e65d5-b5fe-4200-9ea7-34315b1764da.jpg"
---

::text::

- athkjkasda
- skdla;sd
- akdlskd
  
---
layout: layout-body-w-text-subtitle
titleText: "My Title"
subtitleText: "My Subtitle"
image: "https://user-images.githubusercontent.com/13499566/138951075-018e65d5-b5fe-4200-9ea7-34315b1764da.jpg"
lineSpacing: 1.2
titleHeight: 25   # Increase title section height
mainHeight: 70     # Increase main content height
footerHeight: 5   # Decrease footer height
---

::text::

- First item
- Second item
- Third item

---
layout: ncolumns
titleText: "My Multi-Column Layout"
columns: 3
images: 
  - "https://github.com/slidevjs/themes/blob/main/screenshots/theme-default/01.png?raw=true"
  - "https://github.com/slidevjs/themes/blob/main/screenshots/theme-default/01.png?raw=true"
  - "https://github.com/slidevjs/themes/blob/main/screenshots/theme-default/01.png?raw=true"
titles:
  - "First Image"
  - "Second Image"
  - "Third Image"
---

::text::

Footer content goes here.
