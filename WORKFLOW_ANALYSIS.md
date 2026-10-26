# GitHub Actions Workflow Analysis

# What triggers this workflow to run?

The workflow runs when code is pushed to the `main` branch or when a pull request is opened or updated targeting the `main` branch. These triggers are defined in the `on:` section of `deploy.yml`.

# What are the four main steps this workflow performs?

The four steps in the `build-and-test` job are:

1. Checkout code – Gets the repository files so the workflow can work with them.
2. Validate HTML– Checks the HTML files for errors.
3. Check links – Checks for broken links in the project.
4. Upload artifact – Packages the website files so they can be used by the deployment job.

The separate `deploy` job then publishes the website to GitHub Pages.

# What does the "Checkout code" step do and why is it necessary?

The Checkout code step downloads the repository's files into the GitHub Actions runner. This is necessary because the workflow needs access to the website files before it can validate the HTML, check links, and prepare the website for deployment.

# What is the purpose of the environment configuration?

The environment configuration identifies the GitHub Pages deployment environment and provides the deployed website URL. It also works with the deployment job's permissions to allow GitHub Actions to publish the website.

# How does automated deployment improve reliability compared to manual deployment?

Automated deployment follows the same steps each time, reducing the chance of forgetting a step or uploading the wrong files. It also runs checks before deployment, helping catch HTML errors and other issues earlier. This makes the process more consistent and easier to track.

# What would happen if you pushed code to a different branch (not main)?

The workflow would not automatically run just because code was pushed to a different branch, since the push trigger only includes `main`. A pull request targeting `main` would still trigger the workflow. The deployment job only deploys when the event is a push to `main`, so changes on other branches would not be deployed to GitHub Pages.