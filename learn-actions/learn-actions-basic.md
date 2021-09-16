

## Preface: What is actions even?
Actions is a way to make a GitHub computer do things for you, like run some code that makes a file. The steps you make it do are called a "workflow". You can make it do your workflow on a schedule, or when certain events happen (like someone pushes to your repo).


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


I decided to make this workflow run whenever I push, but not counting certain files. If I push to any of these paths, it will not trigger the workflow to run. This will keep things clean while I make frequent pushes to these files.

```
on:
    push:
        branches: main
        paths-ignore: 
          - README.md
          - learn-actions/
          - .github/workflows/workflow_basic.yaml
          - .github/workflows/workflow_intermediate.yaml
    
```

This is a learning repo, so there is actually no need to trigger workflows automatically. Being able to run the workflow manually any time is actually better for learning, testing, etc. That way, no need to do pushes/commits just to get the workflow to run (which you might do to, say, test or debug it).
To do this, use workflow_dispatch:

```
    workflow_dispatch:
```

Now you can run your workflow any time in the Actions tab of your repo:

![image](https://user-images.githubusercontent.com/38010821/122676864-d8190d80-d1ad-11eb-949d-a2a13a5a5628.png)


## Note that:
indentation matters for this whole file!
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

