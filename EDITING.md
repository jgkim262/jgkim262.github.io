# How to edit this site

GitHub rebuilds the site automatically on every push to `master`. You never
need Ruby or Jekyll installed. Changes go live in one to two minutes.

**Two ways to edit:**

- **In the browser** — open the file on github.com, click the pencil icon,
  edit, then "Commit changes". Best for text edits and swapping the photo.
- **Locally** — edit files in
  `C:\Users\gwanhee\Dropbox (Personal)\JobMarketMaterials\website`, then:

  ```bash
  git add -A
  git commit -m "describe what changed"
  git push
  ```

---

## Which file controls what

| To change | Edit |
|---|---|
| Home page text | `_pages/about.md` |
| Papers | `_pages/research.md` |
| Teaching | `_pages/teaching.md` |
| Sidebar: name, title, location, links | `_config.yml`, the `author:` block |
| Top navigation | `_data/navigation.yml` |
| Site title, description (for Google) | `_config.yml`, the top section |
| Fonts and colors | `_sass/_themes.scss` |
| Headshot | replace `images/profile.jpg` |
| CV, paper PDFs | `files/` |

---

## Common changes

### Change text on a page

Open the `.md` file and type. The format is Markdown:

```markdown
**bold**   *italic*   [link text](https://example.com)

## A section heading

- a bullet
- another bullet
```

Leave the `---` block at the top of the file alone — that is the page's
configuration, not content.

### Swap the headshot

Replace `images/profile.jpg` with your photo, keeping the same filename. A
square image around 800×800 works best. On github.com: open the `images`
folder, click "Add file" → "Upload files", drop in a file named
`profile.jpg`, commit.

If your photo is a PNG, upload it as `profile.png` and change this line in
`_config.yml`:

```yaml
  avatar           : "profile.png"
```

### Add a paper

In `_pages/research.md`, copy the shape of an existing entry:

```markdown
**[Paper Title](/files/YourPaper.pdf)**
with Coauthor One and Coauthor Two

*Revise and resubmit at Journal Name*

Presented at Conference A and Conference B.

<details markdown="1"><summary>[+] Abstract</summary>

Paste the abstract here, exactly as it appears in the paper.

</details>
```

Upload the PDF to `files/` first if you want the title to link to it. Drop
the `[...](...)` link if there is no PDF — just use `**Paper Title**`.

`markdown="1"` is required. Without it the abstract will not render.

### Add or remove a navigation item

Edit `_data/navigation.yml`. Each entry is two lines:

```yaml
  - title: "Discussions"
    url: /discussions/
```

Removing an entry hides it from the menu but does not delete the page.

### Add a whole new page

Two steps.

1. Create `_pages/yourpage.md`:

   ```markdown
   ---
   permalink: /yourpage/
   title: "Your Page"
   author_profile: true
   ---

   Your content here.
   ```

2. Add it to `_data/navigation.yml` as shown above, with `url: /yourpage/`.

The `permalink` and the nav `url` must match exactly, including both slashes.

### Change the sidebar links

In `_config.yml`, under `author:`. A field with a value shows an icon; a blank
field shows nothing. To add GitHub, for example:

```yaml
  github           : "jgkim262"
```

To remove a link, delete the value and leave the key:

```yaml
  linkedin         : # Username
```

### Change the font

In `_sass/_themes.scss`:

```scss
$roboto-slab                : 'Roboto Slab', Georgia, serif;
```

If you switch to a different Google Font, also update the stylesheet link in
`_includes/head.html` so the font actually loads.

---

## After you push

Check the **Actions** tab, or just wait two minutes and reload the site with
Ctrl+F5 (a hard refresh — browsers cache aggressively).

If the site does not update, the build probably failed. On github.com the
commit will show a red ✗ instead of a green ✓. Click it to see the error.
The usual causes are a broken `---` block at the top of a page or bad
indentation in a `.yml` file — YAML requires spaces, never tabs.

## If you break something

Nothing is ever lost; every version is in git history.

- **On github.com:** open the file, click "History", find the last good
  version, and copy the content back.
- **Locally**, to throw away uncommitted changes to one file:

  ```bash
  git checkout -- _pages/about.md
  ```

- To undo the most recent commit after pushing:

  ```bash
  git revert HEAD
  git push
  ```

---

## Still to do

- Replace the placeholder headshot at `images/profile.jpg`.
- Point jasonkim.pro at this site. At the domain registrar: remove the
  forwarding to sites.google.com, add four A records on the apex (`@`) to
  `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`,
  and a CNAME from `www` to `jgkim262.github.io`. **After** DNS resolves, add
  a file named `CNAME` containing `jasonkim.pro`, set the custom domain under
  Settings → Pages, tick "Enforce HTTPS", and change `url:` in `_config.yml`
  to `https://jasonkim.pro`.

  Do not set the custom domain before DNS is live: GitHub will start
  redirecting jgkim262.github.io to jasonkim.pro, and the site would be
  unreachable at both addresses until DNS catches up.
