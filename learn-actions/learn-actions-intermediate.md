
# Doing things in your repo (like responding to issues) requires [Authentication](https://docs.github.com/en/actions/reference/authentication-in-a-workflow) with GITHUB_TOKEN 

GitHub automatically creates a GITHUB_TOKEN secret.
to interact with your repo without needing to create a token or secret yourself.

## Intermediate_token.yaml

Check out [intermediate_token.yaml](https://github.com/lizre/learn-actions/blob/main/.github/workflows/intermediate_token.yaml) (content taken directly from 
[here](https://github.com/orchid00/actions_sandbox/blob/master/.github/workflows/greetings.yml)). It comments on new issues and assigns me (lizre) to them.

<br>

Actions using GITHUB_TOKEN will be done by github-actions, a GitHub bot: 
![image](https://user-images.githubusercontent.com/38010821/122679545-4a431f80-d1b9-11eb-880f-c662623a6bf5.png)


<br>

# Encrypted secrets
This is not the same as GITHUB_TOKEN.

Add in Settings > secrets. Now access it by secret key using ${{ secrets.<your-key> }} in the yml file.


[secrets](https://docs.github.com/en/actions/reference/encrypted-secrets)

[Use secrets tutorial](https://github-actions-hero.vercel.app/lessons/9)


<br>


# More Ideas for intermediate 

[matrix build](https://github-actions-hero.vercel.app/lessons/12)
"Matrix build": a thing to make it go on multiple OSs and multiple versions of R. Start at 8:45 [here](https://www.jimhester.com/talk/2020-rsc-github-actions/)

[Linter](https://github.com/r-lib/actions/blob/master/examples/lint-project.yaml)

[https://github.com/sdras/awesome-actions](https://github.com/sdras/awesome-actions) 

actually use R??

[use actions to get data](https://github.com/marketplace/actions/flat-data) 


[detailed syntax](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions)


# Ideas for advanced:  ci/cd and deployment


<br>[Data version control: pachyderm: MLOps meets DevOps](https://github.blog/2020-10-15-pachyderm-and-the-power-of-github-actions-mlops-meets-devops/)

<br>[https://github.com/learn/devops](https://github.com/learn/devops) : includes Actions

<br>Do on cli https://www.youtube.com/watch?v=UM73gUIoWmE

[setup GitHub Actions to connect to AML](https://github.com/github/data-science/pull/772/files?short_path=0a9ad0f#diff-0a9ad0fcb754212ac21763b0e0cb1d5c823d7e69f44db6c9f4fc2b7b5806878a)

[secretshub secrets manager](https://github.com/secrethub/actions) 

[use CLI to manage Actions secrets](https://github.com/unfor19/githubsecrets)

[https://gist.github.com/br3ndonland/f9c753eb27381f97336aa21b8d932be6#secrets](https://gist.github.com/br3ndonland/f9c753eb27381f97336aa21b8d932be6#secrets) 
