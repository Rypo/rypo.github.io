- Add milestones to github
- Automate pipeline to strip out nb_raw cells and reformat document headers before committing notebooks to github
## Site
- Reorder front page posts to display most recently changed rather than oldest->newest
- Clean up redundant css/javascript files
- Upload and add github links to each analysis
- Add link to each notebook with a R<->Python equivalent
- Create a page to sort by tags/categories
- Display tags under each analysis preview 
- Remove all comments that are prefixed by "//", it can cause issues with html_compress 

### Aesthetic
- Make collapsable headings work in python files 
- Add picture to sidebar

## Analyses
- Make tags more relevant to each analysis, reduce overlap (e.g. for agaricus, change to mention SHAP, LIME, ect..)
- Flesh out explainations in later analyses
  - Look up specific analyses that need work, add to TODO
### R
- Fix broken R notebooks and add to site.
- Determine suitable automation pipeline for cleaning Rmd html output and adding front matter
  - First ~200 lines are the same, last ~20 lines are the same.
    - Line 14: date-metadata ex. `<meta name="date" content="2018-12-30" />`
    - Line 16: Title ex. `<title>Multiple Linear Models</title>`
    - Line 183: `<body>` tag
    - Line 202: Content start ex. `<div id="overview" class="section level2">`
    - Last 27 lines contain inserted footer code
  - assets/images/rimgs/ needs to be appended to each image
* `multi-linear-regression`: add intrepretations for diagnostic & summary plots

### Python
- Fix/clean errors from jupyter notebooks
- Determine how to circumvent base64 encoding images in jnbs
  - `--to markdown` exports images to files
  - `--to html --template basic` creates minimal html files
  - Write custom exporter that combines both

## General Ideas
- R embeds dataframes as JSON. Python embeds as html tables.
  - Potentially could export pd.dataframes as JSON and use R-tables styles on pd.dataframes
  - Also could store JSON encoded dataframes in seperate location to keep notebooks clean

```bash
mogrify -format png -path thumbs -thumbnail 600x400 python-unsplash.jpg
```
## Notes
- Represent keypress : <kbd>keyboard text</kbd>
- `post`/`page` can be overridden in for-loops to embed includes in interesting ways  

TODO: General catch all for any improvements.
FIXME: Broken but not severe enough to prevent functionality.
OPTIMIZE: Works but could be performed more efficiently.
STOPSHIP: Critical importance, do not push site live until fixed.

To hide the in[] out[] prompts:
```py
from IPython.core.display import display,HTML
display(HTML('<style>.prompt{width: 0px; min-width: 0px; visibility: collapse}</style>'))
```
