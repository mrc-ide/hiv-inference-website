# HIV Inference Group webite

## To do:

- [ ] Make logo and favicon
- [ ] Get working papers to publications page
- [ ] Get some nice banner images.
- [ ] Add news / events / updates / features reel.
- [x] Get everyone profile done
- [x] Get a proper domain
- [x] Add blog page
- [x] Add project pages
- [x] Add utterances commenting option.

## Editing your profile

The following steps 

- Clone the repository `git clone git@github.com:mrc-ide/hiv-inference-website.git`
- Create a new branch using `git checkout -b <new_branch_name>`. 
- Make changes to file and avatar within `content/authors/yourname`.
- Commit changes using `git commit`.
- Create a pull request to branch `master`. 

## Adding contents (blog post, paper)

Assumed working directory is the cloned folder above

```r
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
  path = "publication/005-Eaton/index.md", 
  kind = "publication")

```

> It's easier to duplicate an existing one and modify it, commit, and pull
> request.

## Notes on content formatting



### Format text in YAML field

To write content in YAML fields, such as paper's `summary`, `abstract`, there
are three options:

- short text: quote the text with double quote
  
  ```yaml
  summary: "text go here"
  ```

- a paragraph without structure: using `>` after the field allows you to break 
  the line for easier editing without reflecting the line breaks on the actual
  results. For example, 

  ```yaml
  summary: >
    Text
    with arbitrarily line
    break.
  ```

  will show up as
  
  Text
  with arbitrarily line
  break.
  
- a structured page: using `|` instead of `>` allow writing normal markdown,
  including splitting text into paragraphs. 

  ```yaml
  summary: |
    **Text**
    with arbitrarily line

    break.
  ```

  will appear as 

  **Text**
  with arbitrarily line

  break.


### Publication fields

### authors

Using full names for co-authors who does not have a profile in the team and and
name tags for team members to link their profile page. Team's name tags can be
found in `content/authors/`

### summary

Text will appear on publication listing but not on the main paper article.

### 

### Type

Classify publication type using the YAML field `publication_types`, see
Tim's or Katherine's publication for examples.

- `0`: Uncategorized
- `1`: Conference paper
- `2`: Journal article
- `3`: Preprint / Working Paper
- `4`: Report
- `5`: Book
- `6`: Book section
- `7`: Thesis (v4.2+ required)
- `8`: Patent (v4.2+ required)
