# Academic Personal Website

This is a clean, minimalist academic website built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme. It's designed to showcase your academic work, teaching materials, and code snippets in a professional manner.

## Features

- Clean, minimalist design inspired by academic websites
- Full Markdown support for easy content creation
- Code syntax highlighting for sharing code snippets
- Responsive design that works well on all devices
- Fast loading times and good SEO
- KaTeX support for mathematical equations
- Easy organization of publications, teaching, and code
- Tag system for categorizing content by topic
- Search functionality
- Archives page for chronological view of all content

## Getting Started

### Prerequisites

1. Install [Hugo](https://gohugo.io/installation/) (this site uses version 0.95.0 or later)
2. Optional: Install Git for version control

### Local Development

1. Clone this repository
2. Navigate to the repository folder in your terminal
3. Run `hugo server` to start a local development server
4. View the site at http://localhost:1313/
5. Make changes to content and see them live-reload in your browser

## Updating Content

This website uses Markdown for all content, making it easy to update and maintain.

### Adding a New Publication

1. Run: `hugo new content/publications/your-publication-title.md` (or copy an existing file)
2. Edit the new file with your publication details
3. Set `draft: false` when ready to publish

### Adding a New Course

1. Run: `hugo new content/teaching/your-course-title.md`
2. Edit the new file with your course details
3. Set `draft: false` when ready to publish

### Adding Code Snippets

1. Run: `hugo new content/code/your-code-snippet-title.md`
2. Edit the new file with your code details and examples
3. Use Markdown code blocks with language specification for syntax highlighting:

```python
def example_function():
    return "This will be syntax highlighted"
```

### Adding Images

1. Place images in the `static` folder or in the same folder as your content file
2. Reference them in your Markdown files:
   ```markdown
   ![Image Description](/images/your-image.jpg)
   ```
   or for images in the same folder as the content:
   ```markdown
   ![Image Description](your-image.jpg)
   ```

### Math Equations

You can include LaTeX equations using KaTeX:

```markdown
Inline equation: $E = mc^2$

Display equation:
$$
\int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi}
$$
```

## Customization

### Site Configuration

Edit `config.yml` to change:
- Your name and basic information
- Social media links
- Menu items
- Theme colors and other settings

### Profile Picture

Replace `static/profile.jpg` with your own photo (keeping the same filename).

### Custom CSS

If you need to add custom CSS, create a file at `assets/css/extended/custom.css`.

## Deployment

### GitHub Pages

This site is set up to be easily deployed to GitHub Pages:

1. Push your repository to GitHub
2. Enable GitHub Actions and Pages in your repository settings
3. The site will be automatically built and deployed when you push changes

### Other Hosting

You can also deploy this site to any static hosting provider:

1. Run `hugo` to build the site
2. Upload the contents of the `public` folder to your hosting provider

## License

This website template is released under the MIT License. Feel free to use it for your own academic website.

## Acknowledgements

- [Hugo](https://gohugo.io/)
- [PaperMod Theme](https://github.com/adityatelange/hugo-PaperMod)
- [KaTeX](https://katex.org/) for math rendering 