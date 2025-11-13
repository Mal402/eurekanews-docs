# Eureka News Documentation

Documentation for Eureka News - A community-led crypto content platform dedicated to indexing Abstract ecosystem content.

This documentation is built with [Mintlify](https://mintlify.com) and provides comprehensive guides for:
- **Readers**: How to browse, interact with, and stay updated with Eureka News content
- **Writers**: How to apply, write articles, use tags, and navigate the review process
- **Editors**: How to publish breaking news and manage content

## 📚 Documentation Structure

```
├── index.mdx                    # Homepage
├── about.mdx                    # About Eureka News
├── readers/                     # Reader documentation
│   ├── getting-started.mdx
│   ├── browsing-content.mdx
│   ├── engaging-with-content.mdx
│   ├── staying-updated.mdx
│   └── reader-tips.mdx
├── writers/                     # Writer documentation
│   ├── getting-started.mdx
│   ├── first-article.mdx
│   ├── tags.mdx
│   ├── review-workflow.mdx
│   ├── best-practices.mdx
│   ├── troubleshooting.mdx
│   └── faq.mdx
├── editors/                     # Editor documentation
│   └── breaking-news.mdx
├── platform-capabilities.mdx   # Platform features overview
├── additional-resources.mdx     # External resources
├── support.mdx                 # Support information
└── docs.json                   # Mintlify configuration
```

## 🚀 Local Development

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn

### Step 1: Install Mintlify CLI

Install the Mintlify CLI globally:

```bash
npm i -g mint
```

### Step 2: Start Local Preview

Navigate to the root directory (where `docs.json` is located) and run:

```bash
mint dev
```

### Step 3: View Your Documentation

Open your browser and navigate to:

```
http://localhost:3000
```

The preview will automatically reload when you make changes to any `.mdx` files.

### Troubleshooting Local Preview

- **If the dev server won't start**: Run `mint update` to ensure you have the latest CLI version
- **If pages show 404**: Make sure you're running the command in the directory containing `docs.json`
- **If changes don't appear**: Hard refresh your browser (Ctrl+Shift+R or Cmd+Shift+R)

## 🌐 Deployment to eurekanews.xyz

### Option 1: Mintlify Hosting (Recommended)

Mintlify provides free hosting for documentation sites. This is the easiest way to deploy.

#### Step 1: Create a Mintlify Account

1. Go to [https://mintlify.com](https://mintlify.com)
2. Sign up for a free account
3. Access your [dashboard](https://dashboard.mintlify.com)

#### Step 2: Connect Your GitHub Repository

1. In your Mintlify dashboard, click **"Add Integration"** or **"New Site"**
2. Select **GitHub** as your source
3. Authorize Mintlify to access your GitHub account
4. Select the repository: `eurekanews-docs` (or your repo name)
5. Select the branch: `main` (or your default branch)
6. Set the root directory: `/` (or leave empty if `docs.json` is in root)

#### Step 3: Configure Custom Domain

1. In your Mintlify dashboard, go to **Settings** → **Domain**
2. Click **"Add Custom Domain"**
3. Enter: `docs.eurekanews.xyz` (or your preferred subdomain)
4. Follow the DNS configuration instructions:
   - Add a CNAME record pointing to Mintlify's provided domain
   - Or add an A record if using the root domain

#### Step 4: Deploy

- Push changes to your `main` branch
- Mintlify will automatically deploy your documentation
- Changes typically go live within 1-2 minutes

### Option 2: Subdomain Setup (docs.eurekanews.xyz)

If you want to host at `docs.eurekanews.xyz`:

1. **In Mintlify Dashboard:**
   - Go to Settings → Domain
   - Add custom domain: `docs.eurekanews.xyz`

2. **In Your DNS Provider (where eurekanews.xyz is managed):**
   - Add a CNAME record:
     - Name: `docs`
     - Value: `[mintlify-provided-domain]` (Mintlify will show you this)
   - Wait for DNS propagation (can take up to 24 hours, usually much faster)

3. **SSL Certificate:**
   - Mintlify automatically provisions SSL certificates via Let's Encrypt
   - No additional configuration needed

### Option 3: Root Domain Setup (eurekanews.xyz/docs)

If you want to host at `eurekanews.xyz/docs`:

1. **In Mintlify Dashboard:**
   - Go to Settings → Domain
   - Add custom domain: `eurekanews.xyz`
   - Set base path: `/docs`

2. **In Your DNS Provider:**
   - Add an A record:
     - Name: `@` (or root)
     - Value: `[mintlify-ip-address]` (Mintlify will provide this)
   - Or use CNAME if your DNS provider supports it

### Option 4: Self-Hosting (Advanced)

If you prefer to host on your own infrastructure:

1. **Build Static Site:**
   ```bash
   mint build
   ```
   This generates static files in a `mint.json` directory (or as configured)

2. **Deploy to Your Server:**
   - Upload the built files to your web server
   - Configure your web server (Nginx, Apache, etc.) to serve the static files
   - Set up SSL certificate (Let's Encrypt recommended)

3. **Configure Your Main Site:**
   - Set up a reverse proxy or subdirectory to serve the docs
   - Example Nginx config:
     ```nginx
     location /docs {
         alias /path/to/mint/build;
         try_files $uri $uri/ /docs/index.html;
     }
     ```

## 📝 Making Changes

### Editing Content

1. Edit any `.mdx` file in your preferred editor
2. Save the file
3. If running `mint dev`, changes will auto-reload
4. Commit and push to trigger deployment

### Updating Navigation

Edit `docs.json` to:
- Add/remove pages
- Reorder navigation groups
- Update branding (colors, logo, etc.)

### Adding Images

1. Place images in the `/images` directory
2. Reference them in markdown: `![Alt text](/images/filename.png)`
3. Commit and push

## 🔧 Configuration

### Customizing Branding

Edit `docs.json`:

- **Colors**: Update `colors.primary`, `colors.light`, `colors.dark`
- **Logo**: Update `logo.light` and `logo.dark` paths
- **Favicon**: Update `favicon` path
- **Name**: Update `name` field

### Navigation Structure

The navigation is defined in `docs.json` under the `navigation.tabs` section. Each tab contains groups, and each group contains pages.

## 📖 Resources

- [Mintlify Documentation](https://mintlify.com/docs)
- [Mintlify Components](https://mintlify.com/docs/components)
- [MDX Guide](https://mdxjs.com)

## 🆘 Need Help?

- **Documentation Issues**: Check [Mintlify Docs](https://mintlify.com/docs)
- **Eureka News Support**: See [Support Page](/support) or email support@eurekanews.xyz
- **GitHub Issues**: Open an issue in this repository
