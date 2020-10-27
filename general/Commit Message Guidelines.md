---
permalink: /general/commit-guidelines
title: Git Commit Message Guidelines
---

# Git Commit Message Guidelines

## Introduction 
This guide serves to show you how to write commit messages while working on Titan Scouting projects. There are many opinions on the "ideal" style in the world of development. Therefore, in order to reduce the confusion on what style you should follow, we urge all committers to refer to this style guide.

## Message Structure
A commit messages consists of three distinct parts separated by a blank line: the title, an optional body and an optional footer. The layout looks like this:

```
type: subject

body

footer
```
The title consists of the type of the message and subject.

### Types
The type is contained within the title and can be one of these types:
* feat: a new feature
* fix: a bug fix
* docs: changes to documentation
* style: formatting, missing semi colons, etc; no code change
* refactor: refactoring production code
* test: adding tests, refactoring test; no production code change
* chore: updating build tasks, package manager configs, etc; no production code change
* deps: dependency-related change

Note: for the `titanscouting.github.io` documentation repository, all commits can be assumed to be of type `docs`.
