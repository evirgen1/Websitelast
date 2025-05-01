# Deploying Your Hugo Website to Hostinger via Git

This guide will walk you through the process of deploying your Hugo website to Hostinger using Git deployment.

## Prerequisites
- A GitHub repository with your Hugo website
- A Hostinger account with an active hosting plan
- Your website files built with Hugo

## Step 1: Generate a Personal Access Token (PAT) on GitHub

1. Log in to your GitHub account
2. Click on your profile picture in the top-right corner
3. Select **Settings**
4. Scroll down to **Developer settings** in the left sidebar
5. Click on **Personal access tokens**, then **Tokens (classic)**
6. Click **Generate new token** and select **Generate new token (classic)**
7. Give your token a descriptive name like "Hostinger Deployment"
8. Select the **repo** scope to give access to your repositories
9. Click **Generate token**
10. **IMPORTANT**: Copy the generated token immediately and save it somewhere secure. You won't be able to see it again!

## Step 2: Create a Repository on GitHub

1. Use the curl command with your personal access token to create a new repository:

```bash
curl -H "Authorization: token YOUR_TOKEN" https://api.github.com/user/repos -d '{"name":"academia-website","private":false,"description":"My academic website built with Hugo"}'
```

2. Add the remote to your local repository:

```bash
git remote add origin https://github.com/YOUR_USERNAME/academia-website.git
```

3. Push your code to GitHub:

```bash
git push -u origin main
```

## Step 3: GitHub Actions for Automatic Building (Already Set Up)

Your repository already includes a GitHub Actions workflow in `.github/workflows/hugo.yml` that automatically builds your Hugo site whenever you push changes to the main branch. The workflow:

1. Sets up the Hugo environment with the extended version
2. Builds your site with minification
3. Deploys the built files to the `gh-pages` branch

This means you don't need to manually build your site before deployment - GitHub Actions will handle this for you. You can adjust the workflow if needed to fit your specific requirements.

## Step 4: Configure Hostinger for Git Deployment

When setting up Git deployment on Hostinger, you have two options:

### Option A: Deploy from the main branch (requires manual build)

If you deploy directly from the main branch, you'll need to make sure your repository contains the built files in the `public` directory.

### Option B: Deploy from the gh-pages branch (recommended)

Since your GitHub Actions workflow publishes the built files to the `gh-pages` branch, you should configure Hostinger to deploy from this branch:

1. Log in to your Hostinger account
2. Go to your **Hosting** dashboard
3. Select your website and click **Manage**
4. In the left sidebar, search for **Git** and click on it
5. In the **Create a New Repository** field:
   - Enter your GitHub repository URL: `https://github.com/YOUR_USERNAME/academia-website.git`
   - Select the branch `gh-pages` (this contains the built website files)
   - For the install path, if you want the website to be your main site, leave it empty to deploy to your account's root folder (`/public_html`)
   - If you want to deploy to a subdirectory, specify the path (e.g., `subdirectory`)

6. Click **Add Repository**

## Step 5: Deploy Your Site

After adding your repository:

1. Click the **Deploy** button to manually trigger the first deployment
2. Your Hugo website will be deployed to your Hostinger hosting

## Step 6: Set Up Automatic Deployment

1. In the Git deployment page on Hostinger, click on the **Auto-Deployment** button
2. You'll get a Webhook URL
3. Go to your GitHub repository
4. Click on **Settings**
5. Select **Webhooks** from the left sidebar
6. Click **Add webhook**
7. Paste the Webhook URL that Hostinger provided
8. Set Content type to `application/json`
9. Select **Just the push event**
10. Click **Add webhook**

With this setup, the complete automated workflow will be:
1. You push changes to your main branch
2. GitHub Actions builds your Hugo site
3. GitHub Actions publishes the built files to the gh-pages branch
4. The webhook triggers Hostinger to pull the latest changes from the gh-pages branch
5. Your updated website is deployed on Hostinger

## Step 7: Test the Deployment

1. Make a small change to your local repository
2. Commit and push the change:

```bash
git add .
git commit -m "Test automatic deployment"
git push
```

3. Wait a few moments (the GitHub Actions workflow takes a minute or two to complete)
4. Check your website to see if the changes appear

## Important Notes

- The install path directory on Hostinger must not contain any files or folders; otherwise, deployment will fail
- If you make changes to your website configuration, make sure to test them locally before pushing
- Keep your GitHub token secure and rotate it periodically for security

## Troubleshooting

If you encounter issues with the deployment:

1. Check the **View latest build output** button in Hostinger to see the deployment logs
2. Go to the "Actions" tab on your GitHub repository to see if the build workflow completed successfully
3. Verify that your repository URL and branch are correct
4. Make sure your GitHub token has the necessary permissions
5. If using automatic deployment, check that the webhook is properly configured
6. Contact Hostinger support if issues persist 