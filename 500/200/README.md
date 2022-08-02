# 200 - Authenticating to GitHub Packages

You need an access token to publish, install, and delete packages.

You can use a personal access token (PAT) to authenticate to GitHub Packages or the GitHub API. When you create a personal access token, you can assign the token different scopes depending on your needs. For more information about packages-related scopes for a PAT, see "[About permissions for GitHub Packages](https://docs.github.com/en/packages/learn-github-packages/about-permissions-for-github-packages#about-scopes-and-permissions-for-package-registries)."

To authenticate to a GitHub Packages registry within a GitHub Actions workflow, you can use:

- ```GITHUB_TOKEN``` to publish packages associated with the workflow repository. See "[GitHub Actions: GITHUB_TOKEN Explained | How it works, Change Permissions, Customizations](https://www.youtube.com/watch?v=jEK07KPEjnY)"
- a PAT to install packages associated with other private repositories (which ```GITHUB_TOKEN``` can't access).

For more information about ```GITHUB_TOKEN``` used in GitHub Actions workflows, see "[Authentication in a workflow](https://docs.github.com/en/actions/reference/authentication-in-a-workflow#using-the-github_token-in-a-workflow)."

## 100 - Authenticating with a personal access token

WE ARE HERE
