# Go Container Action Template

[![Action Template](https://img.shields.io/badge/Action%20Template-Go%20Container%20Action-blue.svg?colorA=24292e&colorB=0366d6&style=flat&longCache=true&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAOCAYAAAAfSC3RAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAAM6wAADOsB5dZE0gAAABl0RVh0U29mdHdhcmUAd3d3Lmlua3NjYXBlLm9yZ5vuPBoAAAERSURBVCiRhZG/SsMxFEZPfsVJ61jbxaF0cRQRcRJ9hlYn30IHN/+9iquDCOIsblIrOjqKgy5aKoJQj4O3EEtbPwhJbr6Te28CmdSKeqzeqr0YbfVIrTBKakvtOl5dtTkK+v4HfA9PEyBFCY9AGVgCBLaBp1jPAyfAJ/AAdIEG0dNAiyP7+K1qIfMdonZic6+WJoBJvQlvuwDqcXadUuqPA1NKAlexbRTAIMvMOCjTbMwl1LtI/6KWJ5Q6rT6Ht1MA58AX8Apcqqt5r2qhrgAXQC3CZ6i1+KMd9TRu3MvA3aH/fFPnBodb6oe6HM8+lYHrGdRXW8M9bMZtPXUji69lmf5Cmamq7quNLFZXD9Rq7v0Bpc1o/tp0fisAAAAASUVORK5CYII=)](https://github.com/jacobtomlinson/go-container-action)
[![Actions Status](https://github.com/jacobtomlinson/go-container-action/workflows/Build/badge.svg)](https://github.com/jacobtomlinson/go-container-action/actions)
[![Actions Status](https://github.com/jacobtomlinson/go-container-action/workflows/Integration%20Test/badge.svg)](https://github.com/jacobtomlinson/go-container-action/actions)

This is a template for creating GitHub actions and contains a small Go application which will be built into a minimal [Container Action](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/creating-a-docker-container-action). Our final container from this template is ~3MB, yours may be a little bigger once you add some code, but it'll still be tiny!

In `main.go` you will find a small example of accessing Action inputs and returning Action outputs. For more information on communicating with the workflow see the [development tools for GitHub Actions](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/development-tools-for-github-actions).

> 🏁 To get started, click the `Use this template` button on this repository [which will create a new repository based on this template](https://github.blog/2019-06-06-generate-new-repositories-with-repository-templates/).

## Usage

Describe how to use your action here.

### Example workflow

```yaml
name: "Find and Replace"
description: "Find and replace a string in your project files"
author: "N Tomlinson"
inputs:
  include:
    description: "A glob of files to include in our find and replace"
    default: "**/*.html" # Include everything by 
    required: false
  exclude:
    description: "A glob of files to exclude in our find and replace"
    default: ".git/**" # Ignore the `.git` directory by default
    required: false
  find:
    description: "fonts\\.googleapis\\.{2,3}\\/css2\\?"
    required: true
  replace:
    description: "api.fonts.coollabs.io"
    required: true
  regex:
    description: "Find as a regular expression instead of a fixed string"
    required: false
outputs:
  modifiedFiles:
    description: "The number of files which have been modified"
runs:
  using: "docker"
  image: "Dockerfile"
```

### Inputs

| Input                                             | Description                                        |
|------------------------------------------------------|-----------------------------------------------|
| `myInput`  | An example mandatory input    |
| `anotherInput` _(optional)_  | An example optional input    |

### Outputs

| Output                                             | Description                                        |
|------------------------------------------------------|-----------------------------------------------|
| `myOutput`  | An example output (returns 'Hello world')    |

## Examples

> NOTE: People ❤️ cut and paste examples. Be generous with them!

### Using the optional input

This is how to use the optional input.

```yaml
with:
  myInput: world
  anotherInput: optional
```

### Using outputs

Show people how to use your outputs in another action.

```yaml
steps:
- uses: actions/checkout@master
- name: Run action
  id: myaction

  # Put your action name here
  uses: me/myaction@master

  # Put an example of your mandatory arguments here
  with:
    myInput: world

# Put an example of using your outputs here
- name: Check outputs
    run: |
    echo "Outputs - ${{ steps.myaction.outputs.myOutput }}"
```
