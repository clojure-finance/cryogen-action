# GitHub Action - Cryogen CI/CD 🌱

Cryogen CI/CD Action for automating deployment.

<a href="https://opensource.org/licenses/MIT"><img alt="License: MIT" src="https://img.shields.io/badge/License-MIT-green.svg?logo=github"></a>

This Github Action automating Cryogen deployment workflow, to allow you to leverage GitHub Actions to publish your Cryogen site on Github Pages.

## 🍑Usage

### 🍄Configuring the default `GITHUB_TOKEN` permissions

1. Click **Settings**.
1. In the left sidebar, click **Actions**, then click **General**.
1. Under "Workflow permissions", choose **Read and write permissions**.
1. Click **Save**.

For more information, please refer to the GitHub Help Documentation for [Configuring the default `GITHUB_TOKEN` permissions](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#configuring-the-default-github_token-permissions).

### 🍌Creating a workflow file

Create a workflow `.yml` file in your `.github/workflows` directory. For more information, reference the  GitHub Help Documentation for [Creating a workflow file](https://docs.github.com/en/actions/using-workflows#creating-a-workflow-file).

**Example:** On every `push` to the `main` branch, generate Cryogen pages and publish to the `gh-pages` branch.

```yaml
name: Publish
on:
  push:
    branches:
      - main
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: Deploy
        uses: clojure-finance/cryogen-action@v2
        with:
          folder: public/datajure-website
          java-version: '11' # optional
          java-distribution: 'liberica' # optional
          lein-version: 2.10.0 # optional
          branch: gh-pages # optional
          single-commit: yes # optional
```

### 🌽Publishing from a branch

1. Click **Settings**.
1. In the "Code and automation" section of the sidebar, click **Pages**.
1. Under "Build and deployment", under "Source", select **Deploy from a branch**.
1. Under "Build and deployment", use the branch dropdown menu and select **`gh-pages`**.
1. Click **Save**.

For more information, please refer to the GitHub Help Documentation for [Publishing from a branch](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site#publishing-from-a-branch).

## 🕊License
The scripts and documentation in this project are released under the [MIT License](LICENSE).
