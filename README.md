# FCJ Cloud Portfolio

Bilingual Hugo site for documenting an FCJ Cloud learning journey, projects, events, and workshops.

## Make this copy yours

1. Update the profile fields in `content/_index.md` and `content/_index.vi.md`.
2. Review every page under `content/`. The cloned report includes sample material written for another person's internship; replace it with your own work before publishing.
3. Replace or remove images in `static/images/` unless you own them or have permission to use them.
4. Set `baseURL` and `author` in `config.toml`. The URL currently uses `YOUR_GITHUB_USERNAME` and `YOUR_REPOSITORY` placeholders.
5. Change the Git remote to your own repository after creating it: `git remote set-url origin https://github.com/YOUR_GITHUB_USERNAME/YOUR_REPOSITORY.git`.

## Run locally

Install Hugo Extended (the deployment workflow uses Hugo 0.134.3), then run:

```sh
hugo server
```

Build the static site with:

```sh
hugo --minify
```

The GitHub Actions workflow publishes pushes to `main` to the `gh-pages` branch. Configure GitHub Pages to deploy from that branch.
