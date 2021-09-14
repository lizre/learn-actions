ci/cd and deployment

# Encrypted secrets
This is not the same as GITHUB_TOKEN.

Add in Settings > secrets. Now access it by secret key using ${{ secrets.<your-key> }} in the yml file.


[secrets](https://docs.github.com/en/actions/reference/encrypted-secrets)

[Use secrets tutorial](https://github-actions-hero.vercel.app/lessons/9)

# Other 

[Check for a grep](https://github.com/github/airflow-sources/blob/master/.github/workflows/ensure_no_orc_usage.yaml)

[Close stale issues](https://github.com/github/airflow-sources/blob/master/.github/workflows/stale.yml)


<br>Use octopy in actions, Example: https://github.com/github/actions-aml/tree/main/.github/workflows

<br>[https://github.com/mxschmitt/action-tmate](https://github.com/mxschmitt/action-tmate)
debug Actions interactively. gives you a browser terminal connected to your Actions runner. dont expose sensitive information if you use this.

<br>[Data version control: pachyderm: MLOps meets DevOps](https://github.blog/2020-10-15-pachyderm-and-the-power-of-github-actions-mlops-meets-devops/)

<br>[https://github.com/learn/devops](https://github.com/learn/devops) : includes Actions

<br>Do on cli https://www.youtube.com/watch?v=UM73gUIoWmE

[setup GitHub Actions to connect to AML](https://github.com/github/data-science/pull/772/files?short_path=0a9ad0f#diff-0a9ad0fcb754212ac21763b0e0cb1d5c823d7e69f44db6c9f4fc2b7b5806878a)

[secretshub secrets manager](https://github.com/secrethub/actions) 

[use CLI to manage Actions secrets](https://github.com/unfor19/githubsecrets)

[https://gist.github.com/br3ndonland/f9c753eb27381f97336aa21b8d932be6#secrets](https://gist.github.com/br3ndonland/f9c753eb27381f97336aa21b8d932be6#secrets) 

[use actions to get data](https://github.com/marketplace/actions/flat-data) 

[detailed syntax and options](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions)

[https://github.com/sdras/awesome-actions](https://github.com/sdras/awesome-actions) 
