# Drishan Banerjee — personal website

Source code for my academic website, published with GitHub Pages at https://drishanbanerjee.github.io.

Built with [Hugo](https://gohugo.io) using Pascal Michaillat's [hugo-website](https://github.com/pmichaillat/hugo-website) template.

**Copyright:** All website content (papers, drafts, CV, photo and text) is © 2026 Drishan Banerjee (co-authored papers jointly with their co-authors). All rights reserved. Only the template code is under the MIT License. See [LICENSE.md](LICENSE.md) for details.

## Where things live

- `config.yml` — name, bio, menu, and contact icons
- `content/papers/` — one folder per paper (`index.md` plus its PDF). The `weight:` line sets the order (1 = top).
- `content/papers/jmp/` — job market paper page (shown under both the Job Market Paper and Papers tabs; PDF is `static/jmp.pdf`)
- `content/teaching.md` — teaching page
- `static/cv.pdf` — CV
- `static/picture.jpeg` — profile photo

Any change pushed to the `main` branch rebuilds and republishes the site automatically (see the Actions tab).
