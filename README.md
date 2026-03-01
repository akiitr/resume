<h1 align="center">online-resume</h1>

<h4 align="center">A minimalist Jekyll theme for your resume.</h4>

---

## Getting Started

Online-Resume is a Jekyll theme designed for creating resumes. It enables you to write your resume in YAML file using Markdown and manage it through Git. It can be displayed on a web page and printed as a PDF file directly from the browser.

You can deploy it on various platforms that support Jekyll or static files, such as GitHub Pages, Cloudflare Pages, Vercel, Netlify, your own hosting service, and others.

Features:

- User-friendly and easy to deploy.
- Built with Jekyll and Markdown.
- Supports multiple languages.
- Customizable theme color and basic styles.
- Modular content design.
- Responsive display.

### Usage

- Edit the `_data/data.yml` file to update your resume.
- The website will be available at `https://akiitr.github.io/resume`.

#### Customization

- `_data/data.yml`: Edit the resume content.
- `assets/images/profile.jpg`: Your profile photo.
- `_config.yml`: Website and theme style settings.

## FAQ

#### How to change the order of the sections in the resume?

There is an `order` option in each section, you can adjust the order by modifying this, the smaller the value the more forward the position.

#### How to hide the specified section in the resume?

If there is no content you want to keep in the section, you can remove it directly. If you want to keep the content, you can set the value of the `show` option of the section to `false`.

#### How to create a resume in other languages?

For example, if you already have an English version resume and you want to create a Chinese version. Copy a `data.yml` file in the `_data` folder named `cn.yml` and edit the content, then copy an `index.html` file in the root directory named `cn.html` and change the `{%- assign data = site.data.data %}` in the `cn.html` file to `{%- assign data = site.data.cn %}`. After successful building, you can preview the Chinese version of your resume by visiting `https://akiitr.github.io/resume/cn`.

#### How to deploy on other platforms, like cloudflare, vercel?

You can read and follow [Cloudflare Pages][Cloudflare Pages], [Vercel][Vercel] documents.

[Cloudflare Pages]: https://developers.cloudflare.com/pages/framework-guides/deploy-a-jekyll-site/
[Vercel]: https://vercel.com/guides/deploying-jekyll-with-vercel
