# MkDocs

1. Go to the [Installation](https://www.mkdocs.org/#installation) instructions for MkDocs,

```
alias python=python3
python --version
alias pip=pip3
pip --version   
pip install --upgrade pip
pip install mkdocs
mkdocs --version
```

2. To install `Material for MkDocs` go to the [Getting Started](https://squidfunk.github.io/mkdocs-material/getting-started/) instructions,

```
pip install mkdocs-material
```

1. Add a `~/README.md` file to the root folder of the project, this is the landing page for the Github repository different from the MkDocs landing page. MkDocs assumes its root to be the `docs` folder.
2. Create a new directory `docs`, or when converting from Gitbook, rename `workshop` to `docs`, edit `gitbook.yaml` and change `workshop` to `docs` references.
3. Add a `docs/README.md` file, which is the homepage for the MkDocs documentation,
4. Create a new file `.github/workflows/ci.yml`,

```
name: ci
on:
  push:
    branches:
      - main
      - master
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-python@v2
        with:
          python-version: 3.x
      - run: pip install mkdocs-material
      - run: mkdocs gh-deploy --force
```

5. In the root folder of your project, create a new file `~/mkdocs.yml`,

```
# Project information
site_name: <SITE_NAME>
site_url: https://ibm.github.io/c
site_author: IBM Developer

# Repository
repo_name: <REPO_NAME>
repo_url: https://github.com/ibm/<REPO_NAME>
edit_uri: edit/master/docs

# Navigation
nav:
  - Welcome:
    - About the workshop: README.md
  - Workshop:
    - Title1: link1/README.md
    - Title2: link2/README.mdREADME.md
  - References:
    - Additional resources: references/RESOURCES.md
    - Contributors: references/CONTRIBUTORS.md

## DO NOT CHANGE BELOW THIS LINE

# Copyright
copyright: Copyright &copy; 2020 IBM Developer

# Theme
theme:
  name: material
  font:
    text: IBM Plex Sans
    code: IBM Plex Mono
  icon:
    logo: material/library
  features:
    - navigation.tabs
    #- navigation.instant
  palette:
    scheme: default
    primary: blue
    accent: blue

# Plugins
plugins:
  - search

# Customization
extra:
  social:
    - icon: fontawesome/brands/github
      link: https://github.com/ibm
    - icon: fontawesome/brands/twitter
      link: https://twitter.com/ibmdeveloper
    - icon: fontawesome/brands/linkedin
      link: https://www.linkedin.com/company/ibm/
    - icon: fontawesome/brands/youtube
      link: https://www.youtube.com/user/developerworks
    - icon: fontawesome/brands/dev
      link: https://dev.to/ibmdeveloper

# Extensions
markdown_extensions:
  - abbr
  - admonition
  - attr_list
  - def_list
  - footnotes
  - meta
  - toc:
      permalink: true
  - pymdownx.arithmatex:
      generic: true
  - pymdownx.betterem:
      smart_enable: all
  - pymdownx.caret
  - pymdownx.critic
  - pymdownx.details
  - pymdownx.emoji:
      emoji_index: !!python/name:materialx.emoji.twemoji
      emoji_generator: !!python/name:materialx.emoji.to_svg
  - pymdownx.highlight
  - pymdownx.inlinehilite
  - pymdownx.keys
  - pymdownx.mark
  - pymdownx.smartsymbols
  - pymdownx.snippets:
      check_paths: true
  - pymdownx.superfences:
      custom_fences:
        - name: mermaid
          class: mermaid
          format: !!python/name:pymdownx.superfences.fence_code_format
  - pymdownx.tabbed
  - pymdownx.tasklist:
      custom_checkbox: true
  - pymdownx.tilde
```

6. Edit the above file `mkdocs.yml`, change:
    * `<SITE_NAME>`
    * `<REPO_NAME>`
    * If converting from Gitbook: copy the navigation links from `workshop/SUMMARY.md` to the `Navigation` section and copy-edit the links for the navigation,

7. Test the docs locally with the command `mkdocs serve`,
8. 