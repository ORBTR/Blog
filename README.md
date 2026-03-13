# ORBTR Blog Posts

This repository contains blog post content for [orbtr.io/blog](https://orbtr.io/blog), served as a remote YAML config.

## How It Works

The `orbtr.io` marketing site periodically fetches `posts.yaml` from this repository's raw GitHub URL and caches the posts in memory. Each post gets its own page at `/blog/{slug}` for SEO purposes.

## File Format

Posts are defined in `posts.yaml` as a YAML array. Each post has the following fields:

| Field         | Required | Description                                              |
|---------------|----------|----------------------------------------------------------|
| `slug`        | Yes      | URL slug (unique) — appears as `/blog/{slug}`            |
| `title`       | Yes      | Post title                                               |
| `date`        | Yes      | Publication date, e.g. `"7 Mar 2026"`                    |
| `author`      | No       | Author name                                              |
| `tags`        | No       | List of tag labels                                       |
| `description` | Yes      | Short summary for listing cards and meta tags            |
| `image`       | No       | Hero/card image URL                                      |
| `content`     | Yes      | Full post body as HTML                                   |

## Adding a Post

Add a new entry to the top of the `posts` array in `posts.yaml` (newest first):

```yaml
posts:
  - slug: my-new-post
    title: "My New Post Title"
    date: "1 Apr 2026"
    author: "ORBTR Team"
    tags:
      - announcement
    description: "A short summary for cards and meta tags."
    content: |
      <h2>Section heading</h2>
      <p>Post body as HTML.</p>
```

## Notes

- Posts display in the order they appear in the file (newest first)
- Content supports full HTML including headings, code blocks, images, and links
- Use YAML literal block scalars (`|`) for multi-line content
- Images can be absolute URLs or relative to `/static/images/` on orbtr.io
- Changes are picked up automatically on the configured refresh interval (default: 5 minutes)
