Create a new blog post with the given title.

Use the title provided in $ARGUMENTS to:

1. Generate a URL-friendly slug from the title (lowercase, hyphens, no special characters — match the style of existing posts like "supercharging-feedback" or "the-product-expert")
2. Create the directory at `content/posts/YYYY/MM/<slug>/` using today's date for the year and month
3. Create `index.md` in that directory with this front matter:

```
---
title: "<the provided title>"
date: <current datetime in RFC3339 format with timezone offset, e.g. 2026-03-27T09:00:00-04:00>
description: ""
displayInMenu: false
displayInList: true
featuredImage: ""
featuredImageDescription: ""
categories: []
draft: true
---
```

4. Output the full path to the created file so the user can start editing immediately.

Important: The post must be created as a draft. Do not add any body content below the front matter.
