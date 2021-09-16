# HIV Inference Group webite

This website is created with Hugo via [blogdown](https://bookdown.org/yihui/blogdown/)
using the [Academic](https://sourcethemes.com/academic/) theme.

The site is hosted on Netifly.

The [_blogdown_ book]((https://bookdown.org/yihui/blogdown/) contains an overview and comprehensive documentation. Alison Hill's [_Summer of Blogodown_](https://summer-of-blogdown.netlify.app/) course provided an easy to follow step-by-step guide.

## Editing the site

The following steps 

- Build via blogdown.
- Pull request.

- Clone the repository `git clone git@github.com:hiv-inference/hiv-inference-website.git`
- Create a new branch using `git checkout -b <new_branch_name>`. 
- Call `blogdown::serve_site()` to render the R markdown files and preview the site.
  * `mypage.Rmd` -> `mypage.html`: This was rendered to HTML using Pandoc.
  * `mypage.Rmarkdown` -> `mypage.md`: This will be rendered to HTML using Blackfriday by Hugo. See `blogdown` documentation on [output format](https://bookdown.org/yihui/blogdown/output-format.html). 
- Make changes.
- Commit changes using `git commit`.
- Create a pull request to branch `master`. 

The folder `content/` contains all site content.

The files `config/_default/menus.toml` and `config/_default/params.toml` define the menu and site layout.

### Adding a blog post

### Adding a team member

## To do:

- [ ] Get some nice banner images.
- [ ] Add project pages.
- [ ] Add blog page.
- [ ] Add publications page.
- [ ] Add news / events / updates / features reel.
- [ ] Add Disqus or other commenting options.
- [ ] Use page bundles (https://alison.rbind.io/post/2019-02-21-hugo-page-bundles/)

## Design notes

* Theme colors are defined in `data/themes/custom_theme.toml`. The theme can be changed by setting the `theme = ` line in `config/_default/params.toml`.
