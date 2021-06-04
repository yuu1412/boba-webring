# Too Many Webrings!

## Visit the live page here: [tfering-jekyll](https://nanufucker.github.io/tfering-jekyll/)

Original readme from [TooManyBees/ring](https://github.com/TooManyBees/ring):

This is a webring, built using Jekyll, hosted by GitHub Pages, that adds sites via pull requests.

The choice to make it a static site generated by GitHub Pages was based on the following:

* Contributing content is pretty well solved by GitHub pull requests.
* Merge conflicts are avoided by making each site represented by a separate file, rather than a list where multiple PRs might be appending to the same spot at the top or bottom.
* GitHub Pages hosts the webring content.
* GitHub Pages rebuilds on merge.

It wasn't intended, but a pleasant side effect of making unique embed pages for each member site is that the next/previous links are computed at build time, and neither server rendering nor JavaScript are needed for it to function. JavaScript is only need for:

* picking a destination for the `random` link
* resizing the iframe (through help of a `parent.js` file), thought that is not needed if the host site styles the iframe correctly
* overriding the interior styles of the embed iframe with the optional `?stylesheet=<some url>` query param

## jess, why do you hate javascript?

I don't, but neither do I let random scripts from unknown origins run in my browser until I specifically whitelist them. They're dangerous as all heck, so it's important to me that 95% of this works without needing it.

# Using it

Full instructions are available on [the prototype's about page](https://toomanybees.github.io/ring/about), but the gist is:

```html
<iframe src="https://toomanybees.github.io/ring/sites/toomanybees">
</iframe>
<script src="https://toomanybees.github.io/ring/assets/parent.js"></script>
```

where `toomanybees` is the name of the member site that's hosting this embed (it corresponds to the file in `_websites`), and the host is the GitHub Pages host location.

# Forking

When basing a new webring on this codebase, these are the most notable files to update:

* [`_config.yml`](_config.yml): the Jekyll configuration
* [`_layouts/site_html.html`](_layouts/site_html.html): the markup template for the embeds
* [`assets/embed.css`](assets/embed.css): the stylesheet for the embeds
* [`_websites`](_websites): the folder where site descriptor files reside
