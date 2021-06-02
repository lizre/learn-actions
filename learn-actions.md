
# Preface

## What is actions
Actions is a way to make a GitHub computer do things for you, like run some code that makes a file. The steps you make it do are called a "workflow". You can make it do your workflow on a schedule, or when certain events happen (like someone pushes to your repo).


## Why use actions: what you can do 
[Lint](https://github.com/r-lib/actions/blob/master/examples/lint-project.yaml) your code when you push it
<br>[Save data](https://blog.simonpcouch.com/blog/r-github-actions-commit/) at regular intervals
<br>[send messages](https://github.com/orchid00/actions_sandbox/blob/master/.github/workflows/greetings.yml) in response to issues or pull requests 
<br>[Render](https://github.com/orchid00/actions_sandbox/blob/main/.github/workflows/deploy_bookdown.yml) and deploy, e.g., rmarkdown
<br>[Big list](https://github.com/r-lib/actions/tree/master/examples) of other things useful for R

<br>

# Start!!

# 1. make a folder and repo.
I made a folder in lizre/Downloads/learn-actions. 
<br>Do git init and then [make a github repo](https://github.com/new).
<br>Make the repo public for Actions [to be free](https://docs.github.com/en/actions/reference/usage-limits-billing-and-administration).

<br><br>

# 2. Make a [.yml](https://docs.github.com/en/actions/learn-github-actions/introduction-to-github-actions#understanding-the-workflow-file) in .github/workflows. 

### This file says what actions to do.

<br>

Check mine out [here](https://github.com/lizre/learn-actions/tree/main/.github/workflows).
Just copy my .github/workflows into your folder you made in step 1. Or make a blank one.


<br><br>

# 3. Starting the workflow: saying when to do the workflow



Read along at [my workflow](https://github.com/lizre/learn-actions/tree/main/.github/workflows):


## "on": when to do the workflow 

A time or event.

Example event trigger: 
```
on: [push]
```

Or use a time interval. Example: every hour:
```
on:
  schedule:
    - cron: "0 * * * *"
```

generate time intervals as cron expressions at [here](https://crontab.cronhub.io/).


## Note that:
indentation matters for this wole .yml file!
<br>You don't have to do anything to activate the workflow. It starts right away, whenever the triggering event happens!

<br><br>

# 4. Starting the workflow: setting up the "runner" to run your workflow

The steps of a workflow happen on a [runner](https://github.com/actions/runner): a server that has the GitHub Actions runner application installed. A runner listens for available jobs, runs one job at a time, and reports the progress, logs, and results back to GitHub. <b>So you have to put everything your code needs on this runner, including your code and an installation of R.</b>

```
jobs:
  job-name:   # put a job name here!
    runs-on: macOS-latest

    steps:
      - name: Check out repository code
        uses: actions/checkout@v2
        
```
`Checkout` checks out your code from your repo and puts it onto the server where this stuff will run.

`"Uses"`: [says what action to use and its version](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions#jobsjob_idstepsuses). 
<br>This is relevant if you are using a workflow step someone else made instead of starting from scratch. These two steps of checking our the repo and setting up R are already pre-made!

## More on "uses":
- write using github repo notation: `{owner}/{repo}@{ref}`
- Where ref can be a branch: `uses: actions/setup-node@main`
- or version/release:  uses: actions/setup-node@v1
- or commit SHA (a unique identifier for every commit you do)
- For example, you can see that the "Set up R" step "uses" r-lib/actions/setup-r@master, which is at 
[https://github.com/r-lib/actions/tree/master/setup-r](https://github.com/r-lib/actions/tree/master/setup-r)


<br>

<br>

## Now the server has what it needs to run your code!

<br>
<br>


# 5. Reading/writing the workflow: using variables and bash


### Use variables

Examples, and others, [here](https://docs.github.com/en/actions/quickstart):
  
```{r, eval = FALSE}

      - name: Use variables to print text about this workflow and repo
        run: |
          echo "🎉 The job was automatically triggered by a ${{ github.event_name }} event."
          echo "🐧 This job is now running on a ${{ runner.os }} server hosted by GitHub!"

```

Use `|` to run multiple lines in one named step.

<br>

### Running shell commands using the runners shell

```{r, eval = FALSE}

      - name: shell script
        run: echo Look, it's text!

```


### Artifacts

An artifact is a temporary object (like a file) that you might create as part of a workflow, that goes away after a specified amount of time. I don't yet know why you would want this.

<br>
<br>



# 6. Check if workflow worked and see its output

[Actions tab in repo](https://github.com/lizre/learn-actions/actions)


<br>
<br>

# 7. Reading/writing the workflow: Actually doing things: using R!


`Setup R` [installs R on the runner](https://github.com/r-lib/actions/tree/master/setup-r).

```
jobs:
  job-name_doing-actions:   # put a job name here!
    runs-on: macOS-latest

    steps:
      - name: Checkout repo
        uses: actions/checkout@v2
        
        # set up an R session on the Actions server
      - name: Set up R
      - uses: r-lib/actions/setup-r@master
```


### Without creating a separate .R

```{r, eval = FALSE}
- run: Rscript -e 'print("hello")'
- run: Rscript -e 'writeLines("text_lines", "my_file1.txt")'
```



### With a separate .R

```{r, eval = FALSE}
      - name: Generate data
        run: |
          source("R/job.R")
        shell: Rscript {0} 
        
```

### Uploading


xxx


### Install dependencies

Search for "install" [here](https://github.com/tidymodels/extratests/blob/master/.github/workflows/GH-R-CMD-check.yaml)


<br>

<br>


# Debugging

### Failed workflow: find failing step and errors

[Example](https://github.com/lizre/axns/runs/2706797755?check_suite_focus=true)

```{r, eval = FALSE}
Run Rscript -e 'writeLines("text", paste0("data/", "text", ".txt"))'
Error: Error in file(con, "w") : cannot open the connection
Calls: writeLines -> file
In addition: Warning message:
In file(con, "w") :
  cannot open file 'data/text.txt': No such file or directory
Execution halted
Error: Process completed with exit code 1.
```

### Test Rscript steps 

by running the part after "run" in Terminal. 
<br>However, working in Terminal doesn't mean the workflow will work.
Many of the failed workflow pushes [here](https://github.com/lizre/axns/commits/main/.github/workflows/workflow.yaml)
worked in the Terminal.
<br>For example, [this one](https://github.com/lizre/axns/commit/da12475e7dcb69d9b80f2a79abf98701c01e2a44#diff-fde0e5d64aae13964fdda6d47af304cf1a7015cbc17e440ac4a5e662ee1d875e):
```{r, eval = FALSE}
- run: Rscript -e 'writeLines("text", paste0("data/", "text", ".txt"))'
```

This `Rscript -e 'writeLines("text", paste0("data/", "text", ".txt"))'` worked
 just fine in Terminal and is very simple, but it would not run as a workflow.

### Unresolved: workflow completes but file-creating step doesn't appear to have executed

[This run](https://github.com/lizre/axns/runs/2706803576?check_suite_focus=true): 
Ran successfully but there's no file!
Closest I could get was using the upload-artifact Action:
[this run](https://github.com/lizre/axns/actions/runs/893050999), as [here](https://github.com/actions/upload-artifact) (docs [here](https://docs.github.com/en/actions/guides/storing-workflow-data-as-artifacts)).
But other r scripts don't seem to need to use that. And, the artifact still didn't show up in the repo 
or local directory!!

<br>

<br>

# Appendix: Advanced links
"Matrix build": a thing to make it go on multiple OSs and multiple versions of R. Start at 8:45 [here](https://www.jimhester.com/talk/2020-rsc-github-actions/)
<br>[detailed syntax](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions)
<br>[Data version control: pachyderm: MLOps meets DevOps](https://github.blog/2020-10-15-pachyderm-and-the-power-of-github-actions-mlops-meets-devops/)
<br>[https://github.com/learn/devops](https://github.com/learn/devops) : includes Actions
<br>Do on cli https://www.youtube.com/watch?v=UM73gUIoWmE


<br>
<br>

# Appendix: Sources

Some content copied or adapted from: 
<br>[learn by running R scripts on a schedule](https://blog.simonpcouch.com/blog/r-github-actions-commit/)
<br>[jim hester and usethis](https://www.jimhester.com/talk/2020-rsc-github-actions/)
<br>[Bookdown](https://orchid00.github.io/actions_sandbox/understanding-yaml.html#github-action-options); goes with [repo](https://github.com/orchid00/actions_sandbox/tree/main) 
