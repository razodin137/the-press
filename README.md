# The Press

A Hugo site that is finished. Not "good enough for now" -- finished.
One week ago you picked Hugo for the last time; this repo is what that
decision looks like as files.

## The rules (non-negotiable)

1. **If it's not in the repo, it doesn't exist.** Phone notes, scratch apps,
   other drafts -- temporary buffers with an expiry date. Transcribe or let go.
2. **`posts/` is the finished shelf. `notes/` is the labeled junk drawer.**
   Unfinished, half-argued, quote-plus-three-sentences: all legal in notes.
   Most scattered-writing anxiety is just having no legal place for the
   60%-done stuff. Now you do.
3. **File by date, browse by tag.** A file lives in exactly one physical
   place and wears many labels. Never split writing across topic folders;
   that is where duplicate diverging drafts come from.
4. **The `draft` flag is the publish switch.** `draft: true` is invisible to
   the world. Flip to `false`, push, it's live. That is the entire pipeline.
5. **The press is frozen until 2027-04-14.** No Hugo upgrades, no theme
   tweaks, no new plugins, no layout changes. You may write, publish, tag,
   and link. Everything else waits. Reopen the question on that date, in
   writing, if it still matters.

## Everyday workflow

```bash
hugo new posts/2026/my-new-post.md     # for the finished shelf
hugo new notes/thought-on-menus.md     # for the drawer

hugo server                            # preview; drafts are visible locally
# edit, save, look, edit again

git add -A
git commit -m "Post: my new post"
git push                               # if draft: false, it is now published
```

Publishing is `draft: false` + `git push`. Deleting the local clone when you
need disk space is safe -- GitHub holds the repo, and the repo is the archive
of record. Clone again on any machine, it all comes back.

## First-time setup (15 minutes)

```bash
git init -b main
git add -A
git commit -m "Build the press, freeze the press"

# create the GitHub repo and push (needs `gh auth login` once):
gh repo create the-press --public --source=. --push

# point GitHub Pages at the Actions workflow:
gh api repos/{owner}/{repo}/pages -X POST -f build_type=workflow
```

Push to `main` and the site builds and deploys itself. The workflow installs
the exact same Hugo version you have locally, so what you preview is what
ships.

## Frozen configuration

| Component  | Pinned at                | Where pinned                          |
|------------|--------------------------|---------------------------------------|
| Hugo       | 0.165.0 extended         | local binary + `.github/workflows/deploy.yml` (`HUGO_VERSION`) |
| Theme      | `press`, yours, vendored | `themes/press/` (every line readable) |
| Deploy     | GitHub Actions -> Pages  | `.github/workflows/deploy.yml`        |

Upgrading any row during the freeze period requires breaking rule 5 on purpose,
in a commit message, so future-you can see the exact moment discipline failed.

## The last ten percent -- the done checklist

Timebox: one weekend. When every box is checked, sign and date the bottom.
After that, the answer to "should I tweak X on the site" is "no" until April.

- [ ] 1. Repo created on GitHub, first push done
- [ ] 2. Pages source set to "GitHub Actions", first deploy green (Actions tab)
- [ ] 3. `hugo.yaml`: set real `baseURL`, `title`, `params.author`, `params.description`
- [ ] 4. Rewrite `content/_index.md` intro and `content/about.md`
- [ ] 5. Publish one real post (`draft: false`, push)
- [ ] 6. Publish one real note (prove the drawer works)
- [ ] 7. Starter tag set: pick 5-8, write them here so you stay consistent:
      `_______`, `_______`, `_______`, `_______`, `_______`, `_______`, `_______`, `_______`
- [ ] 8. Check RSS at `/index.xml`; add to your reader if you use one
- [ ] 9. Optional: custom domain (Pages settings + `static/CNAME`) - or decide "github.io is fine" and check the box anyway
- [ ] 10. Add one photo or don't. Decision made either way = box checked.

**Freeze declaration**

> The press is frozen. I will not touch the theme, the Hugo version, or the
> layout until 2027-04-14. I will only write, publish, tag, and link.
>
> Signed: ____________________   Date: ____________

## Where things live

```
content/posts/2026/   finished shelf, filed by year
content/notes/        the drawer, flat, dated titles
content/about.md      three sentences, that's the spec
hugo.yaml             the whole control panel
themes/press/         your theme; every line is a line you could have written
.github/workflows/    the printer; pinned Hugo, builds and deploys on push
```

Migrating old writing: import only what you would still stand behind. Paste
into `posts/<year>/slug.md`, give it its original date, tag it, move on.
The archive is not a museum; it is a going concern.
