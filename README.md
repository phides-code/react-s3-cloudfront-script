# react-s3-cloudfront-template

This Bash script sets up a React application hosted on AWS with S3 and CloudFront, using GitHub Actions.

-   It creates a basic TypeScript React app by cloning the official Vite template from Redux-toolkit.
-   It creates an S3 bucket and sets up a CloudFront distribution pointing to it with Origin Access Control.
-   It sets up a GitHub repo and a GitHub Actions workflow that builds, tests, and deploys the app.
-   Bonus: To ensure updates to the app are immediately available, the workflow includes a step to invalidate the CloudFront distribution, clearing cached content in edge locations.

## Prerequisites:

### \* Linux or a POSIX-compliant shell (for example MacOS or WSL on Windows)

### \* An AWS account and AWS CLI set up with credentials:

-   AWS CLI : https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

-   AWS credentials configured in the home directory under .aws/

### \* git and gh (GitHub CLI) set up with your credentials:

-   git : https://git-scm.com/

-   gh : https://cli.github.com/

### \* npm and jq

-   npm : https://www.npmjs.com/

-   jq : https://jqlang.github.io/jq/

## Usage

`./build-s3-frontend.sh my-app-name`

## Example run

```
$ ./build-s3-frontend.sh my-app-name

> cloned reduxjs/redux-templates#HEAD to my-app-name
> make_bucket: my-app-name-1b00d7f5
> Created S3 bucket: my-app-name-1b00d7f5
> Created distribution: ESFZHWCRI9TTL
> Initialized empty Git repository in /home/phil/dev/react-s3-cloudfront-template/my-app-name/.git/

1. public
2. private
   Please select repo visibility: Make this GitHub repo Public (1) or Private (2)? 2
   ✓ Created repository phides-code/my-app-name on GitHub
   https://github.com/phides-code/my-app-name
   ✓ Added remote git@github.com:phides-code/my-app-name.git
   ✓ Set Actions secret AWS_DISTRIBUTION for phides-code/my-app-name
   ✓ Set Actions secret AWS_S3_BUCKET for phides-code/my-app-name
   ✓ Set Actions secret AWS_ACCESS_KEY_ID for phides-code/my-app-name
   ✓ Set Actions secret AWS_SECRET_ACCESS_KEY for phides-code/my-app-name
   ✓ Set Actions secret AWS_REGION for phides-code/my-app-name
   AWS secrets set in GitHub Actions.
   [main (root-commit) cdce3e7] initial commit
   29 files changed, 1055 insertions(+)
   create mode 100644 .eslintrc.json
   create mode 100644 .github/workflows/main.yml
   create mode 100644 .gitignore
   create mode 100644 README.md
   create mode 100644 index.html
   create mode 100644 package.json
   create mode 100644 src/App.css
   create mode 100644 src/App.test.tsx
   create mode 100644 src/App.tsx
   create mode 100644 src/app/createAppSlice.ts
   create mode 100644 src/app/hooks.ts
   create mode 100644 src/app/store.ts
   create mode 100644 src/features/counter/Counter.module.css
   create mode 100644 src/features/counter/Counter.tsx
   create mode 100644 src/features/counter/counterAPI.ts
   create mode 100644 src/features/counter/counterSlice.test.ts
   create mode 100644 src/features/counter/counterSlice.ts
   create mode 100644 src/features/quotes/Quotes.module.css
   create mode 100644 src/features/quotes/Quotes.tsx
   create mode 100644 src/features/quotes/quotesApiSlice.ts
   create mode 100644 src/index.css
   create mode 100644 src/index.tsx
   create mode 100644 src/logo.svg
   create mode 100644 src/setupTests.ts
   create mode 100644 src/utils/test-utils.tsx
   create mode 100644 src/vite-env.d.ts
   create mode 100644 tsconfig.json
   create mode 100644 tsconfig.node.json
   create mode 100644 vite.config.ts
   Enumerating objects: 39, done.
   Counting objects: 100% (39/39), done.
   Delta compression using up to 8 threads
   Compressing objects: 100% (34/34), done.
   Writing objects: 100% (39/39), 13.39 KiB | 1.49 MiB/s, done.
   Total 39 (delta 1), reused 0 (delta 0), pack-reused 0
   remote: Resolving deltas: 100% (1/1), done.
   To github.com:phides-code/my-app-name.git

-   [new branch] main -> main

Created distribution at domain: https://dc92i0ma5qczg.cloudfront.net

Please allow a few moments for the GitHub Actions workflow to complete.
View the progress by running:
cd my-app-name
gh run watch
```
