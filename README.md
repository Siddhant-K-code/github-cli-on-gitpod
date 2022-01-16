## What is GitHub CLI?

It is GitHub’s official command line tool. It brings pull requests, issues, and other GitHub concepts to the terminal next to where you are already working with git and your code.

So, Recently GitHub CLI made a new update to Run Your GitHub Workflow Files through Command Line.

## What is GitPod?

Gitpod is an open-source Kubernetes application for ready-to-code developer environments that spins up fresh, automated dev environments for each task, in the cloud, in seconds. It enables you to describe your dev environment as code and start instant, remote and cloud-based developer environments directly from your browser or your Desktop IDE.

## Open Your GitHub Repository in Gitpod:

just add this prefix following to your github repository: `https://gitpod.io/#`

Example: `https://gitpod.io/#https://github.com/GITHUB_USERNAME/REPOSITORY_NAME/`

## GitHub CLI Setup at Gitpod ([official docs](https://cli.github.com/manual/installation)):

Run Following Commands:

```sh
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
sudo apt update
sudo apt install gh
```

```sh
sudo apt update
sudo apt install gh
```

Output:

![Installation of GitHub CLI on Gitpod](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/zl63b9f2xoswealtdj2a.png)

## Setting up the Workflow:

- Create a empty file under `.github/workflows/` named as `github-action-demo.yml`

- File Content:

    ```yml
    name: Demo

    on:
    # Triggers the workflow on push or pull request events but only for the main branch
    pull_request:
        branches: [main]

    # Allows you to run this workflow manually from the Actions tab
    workflow_dispatch:

    jobs:
    cli-gitpod:
        name: CLI and Gitpod Demo
        runs-on: ubuntu-latest
        steps:
        - name: Hello From Gitpod
            run: |
            echo "Hello! From Gitpod 🍊"
    ```

## Login with gh cli

- Run:

    ```sh
    gh auth login
    ```

- Complete whole step and login.

## Test & Run GitHub Workflow with gh cli:

- To View the list of your workflows:

    ```sh
    gh workflow list
    ```
> you Will not see anything, because you first have to enbale that workflow.

- To Enable the workflow:

    ```sh
    gh workflow enable
    ```
![Workflow Enabled](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/pvzq20e335rgh63dwsh1.png)

-  To Run the Workflow:

    ```sh
    gh workflow run demo
    ```
> Here `demo` was my workflow name, you can replace it with your workflow's name.

![Workflow Run](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/s2jmvjnjcqvpf3fezdsl.png)

On GitHub Dashboard:

![GitHub Dashboard](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/0ze6hhbudlbtoipqy2oa.png)

- run history list & analysis:

    ```sh
    gh run list --workflow=github-action-demo.yml
    ```
> `github-action-demo.yml` is the filename, replace it with your workflow's filename.

![Run List](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/x3vq1z7mhfxfwvh37zuu.png)

- Specific Result of any run ID:

    ```sh
    gh run view 1703727006
    ```
> `1703727006` is ID, replace it with your workflow run ID.

![Github workflow run view](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/j51bds0b8s7d4sy5ii11.png)

---

## Similarly, You Can Run all GitHub CLI Commands in GitPod ([gh cli commands](https://cli.github.com/manual/gh))

---

[![Contribute in the browser using Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/Siddhant-K-code/youtube-views-badge)
