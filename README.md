# This is the data for jodaiber.de

## Running locally

To preview the website locally, run the following command:

```bash
bundle exec jekyll serve --host 0.0.0.0 --port 4000
```

## Development

This repository uses [pre-commit](https://pre-commit.com/) to automatically format HTML, CSS and Markdown files. Install the hooks with:

```bash
pre-commit install
```

You can run the checks manually on all files using:

```bash
pre-commit run --all-files
```
