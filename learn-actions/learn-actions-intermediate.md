
# [Authentication](https://docs.github.com/en/actions/reference/authentication-in-a-workflow) with GITHUB_TOKEN

GitHub automatically creates a GITHUB_TOKEN secret.
It lets you make authenticated calls to the GitHub API in your workflow runs. 

Actions generates a new token for each job and expires the token when a job completes.

<br>

# Encrypted secrets
This is not the same as GITHUB_TOKEN.

Add in Settings > secrets. Now access it by secret key using ${{ secrets.<your-key> }} in the yml file.

<br>


# Ideas for intermediate 

[Linter](https://github.com/r-lib/actions/blob/master/examples/lint-project.yaml)

[Send greetings ](https://github.com/orchid00/actions_sandbox/blob/master/.github/workflows/greetings.yml)

[matrix build](https://github-actions-hero.vercel.app/lessons/12)

[https://github.com/sdras/awesome-actions](https://github.com/sdras/awesome-actions) 

actually use R??

[use actions to get data](https://github.com/marketplace/actions/flat-data) 

"Matrix build": a thing to make it go on multiple OSs and multiple versions of R. Start at 8:45 [here](https://www.jimhester.com/talk/2020-rsc-github-actions/)

[detailed syntax](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions)


# Ideas for advaned

<br>[Data version control: pachyderm: MLOps meets DevOps](https://github.blog/2020-10-15-pachyderm-and-the-power-of-github-actions-mlops-meets-devops/)

<br>[https://github.com/learn/devops](https://github.com/learn/devops) : includes Actions

<br>Do on cli https://www.youtube.com/watch?v=UM73gUIoWmE

