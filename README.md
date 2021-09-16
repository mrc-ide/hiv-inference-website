# HIV Inference Group webite

## To do:

- [ ] Get everyone profile done
- [ ] Get working papers to publications page
- [ ] Get a proper domain
- [ ] Get some nice banner images.
- [x] Add blog page
- [ ] Add news / events / updates / features reel.
- [x] Add project pages
- [ ] Add Disqus or other commenting options.

## Editing your profile

The following steps 

- Clone the repository `git clone git@github.com:hiv-inference/hiv-inference-website.git`
- Create a new branch using `git checkout -b <new_branch_name>`. 
- Make changes to file and avatar within `content/authors/yourname`.
- Commit changes using `git commit`.
- Create a pull request to branch `master`. 

### Adding contents

Assumed working directory is the cloned folder above

```{r}
# Start serving a preview of the website
blogdown::serve_site()

# Create a new blog
blogdown::new_post(
  title = "A title alright", 
  kind = "post/", # keep this as is
  author = "Jeff Eaton", # or "jeffeaton"
  categories = "Statistics", 
  tags = c("HIV", "Model"))

# Create a new publication
blogdown::new_content(
  path = "publications/005-Eaton/index.md", 
  kind = "publication")

# or duplicate an existing one and modify it, commit, and pull request
```

Here you can edit and preview contents. Once done, commit and create pull 
request like the previous steps.

#### non-RStudio

Assuming you have cloned this repo to `~/hivref`, then open Terminal and do

```bash
cd ~/hivref
hugo new content/blog/the-title-of-your-blog.md
# on Mac this will open your default markdown's editor
open content/blog/the-title-of-your-blog.md
hugo serve
# add publication
hugo new --kind publication publications/005-ABC/
```

Start to fill in the contents while previewing it at `localhost:1313` on your
browser (assuming [Hugo](https://github.com/gohugoio/hugo/releases) is already
installed).

Once done editing, commit the changes > push > make pull request.

## Design notes

* Theme colors are defined in `data/themes/custom_theme.toml`. The theme can be changed by setting the `theme = ` line in `config/_default/params.toml`.
