# A Daily Dose of History

A Jekyll blog hosted on GitHub Pages.

## How to publish a new post

1. Go to your live blog → click **"✦ Write Entry"** in the nav
2. Fill in your title, era, image, and article
3. Click **"Generate Post File"**
4. Click **"Download File"** — saves a `.md` file to your computer
5. Go to your GitHub repo → open `_posts` folder
6. Click **Add file → Upload files**
7. Upload the downloaded `.md` file
8. Click **Commit changes**
9. Your post is live in 1–2 minutes! ✅

## How to add images

- **From URL**: Paste any image link (Wikipedia, Wikimedia Commons recommended)
- **From your computer**: Upload image to `/assets/images/` folder in your repo, then use `/assets/images/yourimage.jpg` as the image URL

## Folder structure

```
_posts/          ← Your blog posts go here (YYYY-MM-DD-title.md)
_layouts/        ← Page templates
_includes/       ← Reusable components (header, footer, ads)
assets/css/      ← Stylesheet
assets/images/   ← Upload your images here
```

## AdSense

Your publisher ID `ca-pub-6777857056104326` is already added.
Once approved, replace `YOUR_SLOT_ID_1/2/3` in `_includes/ad-*.html` files.
