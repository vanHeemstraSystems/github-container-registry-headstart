# 200 - Authenticating to GitHub Packages

You need an access token to publish, install, and delete packages.

You can use a personal access token (PAT) to authenticate to GitHub Packages or the GitHub API. When you create a personal access token, you can assign the token different scopes depending on your needs. For more information about packages-related scopes for a PAT, see "[About permissions for GitHub Packages](https://docs.github.com/en/packages/learn-github-packages/about-permissions-for-github-packages#about-scopes-and-permissions-for-package-registries)."

To authenticate to a GitHub Packages registry within a GitHub Actions workflow, you can use:

- ```GITHUB_TOKEN``` to publish packages associated with the workflow repository. See "[The GITHUB_TOKEN in GitHub Actions: How it Works, Change Permissions, Customizations](https://dev.to/github/the-githubtoken-in-github-actions-how-it-works-change-permissions-customizations-3cgp)"
- a PAT to install packages associated with other private repositories (which ```GITHUB_TOKEN``` can't access).

**NOTE**: A GITHUB_TOKEN expires as soon as a job (in a GitHub Action) has been completed, whereas a PAT doesn't expire unless you choose to. Hence, why a GITHUB_TOKEN is a more secure way to authenticate as it does not allow an intruder to use it after it expires.

For more information about ```GITHUB_TOKEN``` used in GitHub Actions workflows, see "[Authentication in a workflow](https://docs.github.com/en/actions/reference/authentication-in-a-workflow#using-the-github_token-in-a-workflow)."

## 100 - Authenticating with a personal access token

You must use a personal access token with the appropriate scopes to publish and install packages in GitHub Packages. For more information, see "[About GitHub Packages](https://docs.github.com/en/packages/learn-github-packages/about-github-packages#authenticating-to-github-packages)."

You can authenticate to GitHub Packages with npm by either editing your per-project ```.npmrc``` file to include your personal access token.

To authenticate by adding your personal access token to your ```.npmrc``` file, edit the ```.npmrc``` file for your project to include the following line, replacing **TOKEN** with your personal access token. Create a new ```.npmrc``` file if one doesn't exist.

```
//npm.pkg.github.com/:_authToken=TOKEN
```
.npmrc



WE ARE HERE
