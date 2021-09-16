# Learn Automation with GitHub Actions 

# Is this for me?

GitHub Actions learning resources aren't made for non-technical people new to automation. It's too bad because it's an otherwise accessible way to learn about automation. This repo should help with that. 

### Pre requisites that might help:
<br>git basics: commit and push
<br>github repositories basics
<br>very basic 1, 2 or 3 line R and bash coding

### Why use actions: what you can do 
[Lint](https://github.com/r-lib/actions/blob/master/examples/lint-project.yaml) your code when you push it
<br>[Save data](https://blog.simonpcouch.com/blog/r-github-actions-commit/) at regular intervals
<br>[send messages](https://github.com/orchid00/actions_sandbox/blob/master/.github/workflows/greetings.yml) in response to issues or pull requests 
<br>[Render](https://github.com/orchid00/actions_sandbox/blob/main/.github/workflows/deploy_bookdown.yml) and deploy, e.g., rmarkdown
<br>[Big list](https://github.com/r-lib/actions/tree/master/examples) of other things useful for R

# Let's start! 

### Start here: [Basic workflow](https://github.com/lizre/learn-actions/blob/main/learn-actions/learn-actions-basic.md)
### [Debug and troubleshoot](https://github.com/lizre/learn-actions/blob/main/learn-actions/debugging.md)
### [Intermediate workflow](https://github.com/lizre/learn-actions/blob/main/learn-actions/learn-actions-intermediate.md)

### [Intermediate workflow in another one of my repos](https://github.com/lizre/learn-ml/blob/main/.github/workflows/lint.yaml): python linter on PR
- This is private; ask me for access if you want. I'll also work on migrating it over here! In the meantime the workflow is available [here](https://github.com/lizre/learn-actions/blob/main/.github/workflows/intermediate_lint-py.yaml)
- [demo PR](https://github.com/lizre/learn-ml/pull/2)
- [demo failed run on that PR, showing pycodestyle error messages](https://github.com/lizre/learn-ml/pull/2/checks?check_run_id=3568237239)


### [Sources and appendices](https://github.com/lizre/learn-actions/blob/main/learn-actions/sources-and-appendices.md)


