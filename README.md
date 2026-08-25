# jasonkim.pro

Personal academic website for Jason G. Kim, Ph.D. candidate in accounting at the
MIT Sloan School of Management.

Live at [jasonkim.pro](https://jasonkim.pro) and
[jgkim262.github.io](https://jgkim262.github.io).

## Editing the site

GitHub builds the site automatically on every push to `master` — no local Ruby
or Jekyll installation is needed.

| What to change | File |
|---|---|
| Home page bio | `_pages/about.md` |
| Papers | `_pages/research.md` |
| Teaching | `_pages/teaching.md` |
| Name, photo, sidebar links | `_config.yml` (the `author:` block) |
| Top navigation | `_data/navigation.yml` |
| CV, paper PDFs | `files/` |
| Headshot | `images/profile.jpg` |

Edit, commit, push; the site rebuilds in a minute or two.

Built on the [Academic Pages](https://github.com/academicpages/academicpages.github.io)
template, a fork of [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes).
Design notes are in `docs/superpowers/`.
