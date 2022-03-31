# Yamllint PR Annotator

## Usage

Annotate pull requests with yamllint errors detected during CI.

This is designed to work with the "parsable" output format of yamllint.

Note: This doesn't install or run yamllint, it just sets up the PR annotations.

### Example workflow

```yaml
name: My Workflow
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master

      - name: Set up Python 3.8
        uses: actions/setup-python@v2
        with:
          python-version: "3.8"
        
      - name: Install yamllint
        run: |
          pip install yamllint

      - name: Add yamllint annotator
        uses: jpy-git/yamllint-pr-annotator@master

      - name: Run yamllint
        run: |
          yamllint -f parsable src/
```
