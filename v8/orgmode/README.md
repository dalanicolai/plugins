This plugin implements an Emacs Org-mode based compiler for Nikola.

## Setup

If your emacs does not ship with org-mode (>=8.x), you will have to edit the
`init.el` file supplied with this plugin, and load a newer version of org-mode.

You will also need to add the orgmode compiler to your list of compilers, and
modify your POSTS & PAGES variables.  (See the sample conf file provided.)

### Syntax highlighting with pygments

By default, the plugin uses `pygments` for syntax highlighting. You can disable
this by setting `nikola-use-pygments` to `nil` in `init.el` or `conf.el` (see
Customization section below).

To get proper syntax highlighting, you will need to add custom CSS to your
theme. You can generate this CSS using the `pygmentize` command as follows:

    mkdir -p files/assets/css
    pygmentize -S <PYGMENTS_STYLE> -a .highlight -f html >> files/assets/css/custom.css

and make sure that `custom.css` is included in your site by your
theme. The various available style options for `<PYGMENTS_STYLE>` can be found
using the command `pygmentize -L style`.

## Customization

You can add any customization variables that you wish to add, to modify the
output generated by org-mode to `conf.el` inside the plugin directory.  This
lets you have custom configuration, that doesn't get wiped out each time the
plugin is updated.

## Teasers

You may use teasers by enabling `INDEX_TEASERS = True` in conf.py, and
use `{{{TEASER_END}}}` to generate `<!-- TEASER_END -->` in org posts.

## Image URLs

The image url in ox-html is a little fuzzy. For example, `[[/images/test.jpg]]` will be
generated as `<img src="file:///images/test.jpg" alt="test.jpg">`
because the path is considered as an absolute file path.

In order to correctly generate image urls, you may write `[[img-url:/images/test.jpg]]`,
and then it should be generated as `<img src="/images/test.jpg" alt="test.jpg">`.

The internal link in ox-html is a little fuzzy. For example, `[[./test.org][test]]` will be generated as `<a href="file:///./test.org">"test"` because the path is considered as an absolute file path.

In order to correctly generate internal link urls, you may write `[[internal:./test.org][test]`, and then it should be generated as <a href="./test/index.html">"test".
