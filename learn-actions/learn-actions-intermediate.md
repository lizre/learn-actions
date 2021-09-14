
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
<br>


# Next:

[matrix build](https://github-actions-hero.vercel.app/lessons/12)
"Matrix build": a thing to make it go on multiple OSs and multiple versions of R. Start at 8:45 [here](https://www.jimhester.com/talk/2020-rsc-github-actions/)

[Linter](https://github.com/r-lib/actions/blob/master/examples/lint-project.yaml)

Docker with actions
[https://github.com/actions/hello-world-docker-action](https://github.com/actions/hello-world-docker-action)
[https://docs.github.com/en/actions/creating-actions/creating-a-docker-container-action](https://docs.github.com/en/actions/creating-actions/creating-a-docker-container-action)
[https://github.com/docker/github-actions](https://github.com/docker/github-actions)
Docker actions [here](https://github.com/sdras/awesome-actions)
