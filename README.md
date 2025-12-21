# Personal Site - Dominik Reiner

This is the repository for my personal website and blog, built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme.

## 🚀 About the Site

I am an AI Engineer who enjoys turning ideas into tangible products. This site serves as a corner of the web where I share my personal projects, technical insights, and interesting findings in the world of technology and artificial intelligence.

**Visit the live site:** [dominik-reiner.github.io](https://dominik-reiner.github.io/)

## 🛠 Tech Stack

- **Static Site Generator:** [Hugo](https://gohugo.io/)
- **Theme:** [PaperMod](https://github.com/adityatelange/hugo-PaperMod)
- **Deployment:** [GitHub Pages](https://pages.github.com/) via GitHub Actions
- **Styling:** CSS (PaperMod defaults)
- **Forms:** [Formspark](https://formspark.io/) for the contact form

## 💻 Local Development

To run this site locally, you'll need to have Hugo installed.

1. **Clone the repository:**
   ```bash
   git clone --recursive https://github.com/dominik-reiner/personal-site.git
   cd personal-site
   ```

2. **Start the Hugo server:**
   ```bash
   hugo server -D
   ```
   The `-D` flag includes content marked as `draft: true`.

3. **Open in browser:**
   Navigate to `http://localhost:1313`.

## 📂 Project Structure

- `content/`: Contains all Markdown files for the site (posts, imprint, privacy).
- `layouts/`: Custom HTML layouts and partials.
- `static/`: Static assets like images and favicons.
- `themes/`: Hugo themes (PaperMod is included as a submodule).
- `hugo.yaml`: Main configuration file.

## 🚢 Deployment

The site is automatically built and deployed to GitHub Pages whenever changes are pushed to the `main` branch. This is handled by the GitHub Actions workflow located in `.github/workflows/deploy.yaml`.

## ⚖️ License

All content on this site is my own unless otherwise specified. Please feel free to explore the code!
