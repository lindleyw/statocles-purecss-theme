# statocles-purecss-theme
A basic framework for building themes using the PureCSS framework on Statocles.

This is primarily a demonstration of how to create entirely new Statocles themes.

The quickest way to start a new theme is to say Yes when you make a new site
with the `statocles create` command:

    Do you want to bundle the theme? ([Y]/n) 

This makes a copy of the default theme in your 'theme' directory.  From there you
probably want to modify at least three files:

   * `site/layout.html.ep` − this is the highest-level, or outermost, template.
   * `blog/index.html.ep` − the Blog app uses this to make blog index pages.
     After processing, the result becomes `$content` inside the layout.html file above.
   * `blog/post.html.ep` − the Blog app creates each post with this template,
     also becoming `$content` as above.

Basically we make a new theme by:

   * Changing the link, meta, and script tags in the document's <head>
   * Wrapping the content of the document's <body> in our appropriate tags

How you do that will depend on the CSS framework you choose, and what you want to do
with it.

My plan is to develop a more general theme which puts most of the decisions into
the `site.yml` file, by letting you define a series of containers, and describing
what should go into each one.  This is rather how "widgets" work in systems like
WordPress.

Here is how we use this basic theme and its features.  Below when I specify the
theme store, you probably want to put the files from this project into a
subdirectory under the `theme/` directory of your site, but the example shows how
a theme can be shared across multiple sites with absolute instead of relative
locations.

in `site.yml`:

    site:
      args:
        ...
        images:
            icon:
              src: 'http://wlindley.com/logo.png'
            logo:
              src: 'http://wlindley.com/logo.png'
    ...
    theme:
        class: 'Statocles::Theme'
        args:
            # store: Here we give the location of our theme files, stored in
            # our home directory. Tilde expansion is enabled on *nix systems.
            store: '~/Documents/work/perl/StatTheme/'


