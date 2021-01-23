---
title: Style Guide
slug: style-guide
---

## Fonts

I use system fonts so no extra fonts have to be downloaded because of my website. I got these system font stacks from [systemfontstack.com](https://systemfontstack.com).

Serif: `-apple-system, BlinkMacSystemFont, "Avenir Next", Avenir, "Helvetica Neue", Helvetica, Ubuntu, Roboto, Noto, "Segoe UI", Arial, sans-serif;`

Monospace: `Menlo, Consolas, Monaco, "Liberation Mono", "Lucida Console", monospace;`.

## Colours

The teal is my favourite colour. The rest are just to achieve enough contrast whilst trying not to be _too_ contrasty, which I also find hard on the eyes. The excessive in-between levels of black and grey are only there to make the code blocks look decent.

<div style="padding: 0.5rem 1rem; color: var(--white); background: var(--literally-black);">Literally black - #000000</div>
<div style="padding: 0.5rem 1rem; color: var(--white); background: var(--darker-black);">Darker black - #242424</div>
<div style="padding: 0.5rem 1rem; color: var(--white); background: var(--black);">Black - #313131</div>
<div style="padding: 0.5rem 1rem; color: var(--white); background: var(--grey);">Grey - #8a8a8a</div>
<div style="padding: 0.5rem 1rem; color: var(--black); background: var(--medium-grey);">Medium grey - #bbbbbb</div>
<div style="padding: 0.5rem 1rem; color: var(--black); background: var(--light-grey);">Light grey - #e1e1e1</div>
<div style="padding: 0.5rem 1rem; color: var(--black); background: var(--white);">White - #fbfbfb</div>
<div style="padding: 0.5rem 1rem; color: var(--white);  background: var(--teal);">Colour - #0091ab</div>
<div style="padding: 0.5rem 1rem; color: var(--black);  background: var(--lighter-teal);">Colour dark mode - #64d1dd</div>

## Images

A smallish plain image

![Montreal from Mount Royal](/assets/images/montreal.jpg)

A figure with caption, intentionally wider than my width

<figure>
  <img src="/assets/images/me.jpg" alt="Kira McLean">
  <figcaption>That's me! A very old picture, but it's my face everywhere on the internet and I still look the same.</figcaption>
</figure>

## Email signup form

<form>
  <span>
    <input type="email" name="email" placeholder="Your Email Address">
  </span>
  <button type="submit">Send me updates!</button>
</form>

## Headers

# XL Heading (h1)

## Large heading (h2)

### Medium heading (h3)

#### Small heading (h4)

## Everything else

[a visited link](/style-guide) and [an unvisited link -- don't click this!](https://example.com/dont-click-this-kira)

- list
- one
- two

1. there are
2. also sometimes
3. ordered lists

some `code` in the middle of a line

```
;; some code
;; in a block that's really really long and needs to scroll horizontally because one line won't fit within my max width
```

<small>small text, like the dates on the home page or in the footer</small>

> blockquote text but long enough to wrap onto two lines so I can see what it looks like and make sure the styles work well

<time datetime="2020-01-01">January 1, 2021</time>

Just a paragraph with _emphasized text_ and **strong text** to see what normal text looks like. Followed by a page break, to see what those look like.

---

<dl>
  <dt>Description list</dt>
  <dd>Use these to mark up lists of definitions</dd>

  <dt>dt</dt>
  <dd>A description list item title</dd>

  <dt>dd</dt>
  <dd>A description list item definition</dd>
</dl>
