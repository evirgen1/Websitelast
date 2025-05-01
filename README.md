# Academic Website

This repository contains my academic website built with Hugo.

## About

This is a personal academic website that showcases my research, teaching, publications, and other professional activities. The site is built using the Hugo static site generator with the PaperMod theme.

## Features

- Responsive design
- Research publications and working papers
- Teaching materials and course information
- Public appearances
- Contact information
- Data visualizations

## Local Development

### Prerequisites

- [Hugo Extended](https://gohugo.io/installation/) (v0.147.0 or later)
- Git

### Setup

1. Clone this repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/academia-website.git
   cd academia-website
   ```

2. Initialize and update the theme submodule:
   ```bash
   git submodule init
   git submodule update
   ```

3. Start the Hugo development server:
   ```bash
   hugo server -D
   ```

4. View the site at [http://localhost:1313/](http://localhost:1313/)

### Making Changes

1. Edit files in the `content/` directory to update the website's content
2. Modify templates in the `layouts/` directory to change the site's structure
3. Adjust styling in the `assets/css/extended/custom.css` file
4. Configure site settings in `config.yml`

## Deployment

This website is automatically deployed to Hostinger via Git deployment. The process is as follows:

1. Changes are pushed to the main branch
2. GitHub Actions builds the site and publishes to the gh-pages branch
3. Hostinger pulls the latest changes from the gh-pages branch

For detailed deployment instructions, see the [HOSTINGER_DEPLOYMENT_INSTRUCTIONS.md](HOSTINGER_DEPLOYMENT_INSTRUCTIONS.md) file.

## Project Structure

- `content/`: All the content of the website (Markdown files)
  - `research/`: Research publications and working papers
  - `teaching/`: Teaching materials and course information
  - `public-appearances/`: Public appearances and media mentions
  - `data/`: Data visualizations and resources
  - `code/`: Code examples and projects
- `layouts/`: Custom HTML templates
- `static/`: Static files (images, PDFs, etc.)
- `themes/`: The PaperMod theme as a Git submodule
- `.github/workflows/`: GitHub Actions workflows for automatic building and deployment

## License

All content is copyright © 2024. All rights reserved unless otherwise specified. 