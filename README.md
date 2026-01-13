# Nicolas Lelièvre - Personal Blog & Portfolio

> Analytics Engineering Tech Lead blending strong business insight with modern data engineering practices.

Personal blog and portfolio site showcasing my work, technical writing, and professional journey. Built with modern web technologies and deployed as a static site for optimal performance.

## 🚀 Live Site

Visit [nicolaslelievre.github.io](https://nicolaslelievre.github.io)

## ✨ Features

- **Blog**: Technical articles on analytics engineering, data platforms, and modern data stack
- **Work Experience**: Professional background and key accomplishments
- **Projects**: Showcase of personal and professional projects
- **Responsive Design**: Mobile-first, fast-loading experience
- **SEO Optimized**: Built-in meta tags and sitemap generation
- **RSS Feed**: Subscribe to new content

## 🛠️ Tech Stack

- **Framework**: [Astro Nano](https://github.com/markhorn-dev/astro-nano) - A minimal, performant Astro theme
- **Language**: TypeScript for type-safe development
- **Styling**: Tailwind CSS for utility-first styling
- **Deployment**: GitHub Pages with automated CI/CD
- **Content**: Markdown-based blog posts and pages
- **Analytics**: [Umami](https://umami.is/) - Privacy-focused, open-source analytics

## 📊 Analytics Setup (Umami)

This site uses Umami for privacy-friendly website analytics. Umami is a simple, fast, and privacy-focused alternative to Google Analytics.

### Prerequisites

- A [Vercel account](https://vercel.com/signup)
- A database (Vercel provides PostgreSQL)

### Steps to Setup Postgres on Supabase

1. **Create a Supabase Account**
   - Visit [Supabase](https://supabase.com) and sign up for a free account

2. **Create a New Project**
   - Click "New Project" in the Supabase dashboard
   - Choose an organization or create a new one
   - Set your project name, database password, and region
   - Click "Create new project" (this takes about 2 minutes)

3. **Get Database Connection Strings**
   - Go to Project Settings > Database
   - Scroll down to "Connection string" section
   - You will need this information to configure the environment variables for Vercel


### Steps to Deploy Umami on Vercel

1. **Fork or Clone Umami Repository**
   - Visit [https://github.com/umami-software/umami](https://github.com/umami-software/umami)
   - Fork the repository

2. **Deploy to Vercel**
   - Go to [Vercel](https://vercel.com/new)
   - Import your Umami repository
   - Configure environment variables:
     - `DATABASE_URL`: postgres://[db-user].[project-ref]:[db-password]@aws-0-[aws-region].pooler.supabase.com:6543/postgres?pgbouncer=true&connection_limit=1
     - `APP_SECRET`: postgres://[db-user].[project-ref]:[db-password]@aws-0-[aws-region].pooler.supabase.com:5432/postgres
   - Click "Deploy"

3. **Access Umami Dashboard**
   - Once deployed, visit your Umami URL (e.g., `your-umami.vercel.app`)
   - Default login: username `admin`, password `umami`
   - **Important**: Change the default password immediately

4. **Add Your Website**
   - In Umami dashboard, go to Settings > Websites
   - Click "Add website"
   - Enter your website name and domain
   - Copy the tracking code or website ID

### Integrating Umami into Your Site

1. **Add Tracking Script**
   - Open your site's main layout file: `src/layouts/PageLayout.astro`
   - Add the Umami script in the `<head>` section:

   ```html
   <script
     async
     src="https://your-umami.vercel.app/script.js"
     data-website-id="your-website-id"
   ></script>
   ```

2. **Verify Installation**
   - Deploy your site
   - Visit your website
   - Check the Umami dashboard to confirm page views are being tracked

### Viewing Analytics

- Access your Umami dashboard at your Vercel deployment URL
- View real-time visitors, page views, referrers, browsers, and more
- All data is collected anonymously without cookies

## 🏗️ Project Structure

```
/
├── src/
│   ├── components/    # Reusable UI components
│   ├── content/       # Blog posts and content
│   ├── layouts/       # Page layouts
│   ├── pages/         # Site pages and routes
│   └── styles/        # Global styles
└── public/            # Static assets
```

## 💻 Development

### Prerequisites

- Node.js 18+
- npm

### Commands

| Command              | Action                                       |
| :------------------- | :------------------------------------------- |
| `npm install`        | Install dependencies                         |
| `npm run dev`        | Start local dev server at `localhost:4321`   |
| `npm run build`      | Build production site to `./dist/`           |
| `npm run preview`    | Preview build locally before deploying       |

## 📝 Adding Content

Blog posts are written in Markdown and stored in `src/content/blog/`. Each post includes frontmatter for metadata like title, description, and publication date.

## 📫 Connect

- GitHub: [@nicolaslelievre](https://github.com/nicolaslelievre)
- LinkedIn: [Nicolas Lelièvre](https://www.linkedin.com/in/nicolaslelievre-ca/)
