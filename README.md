# Autopretty - the automated code prettifier

Are you tired of configuring `.pre-commit-config.yaml` all over your projects, and
keeping those up-to-date?

Me too. 🤦‍

Thus, here's autopretty. It uses [Copier][] to keep your projects updated with the
latest code formatters and linters.

[copier]: https://copier.readthedocs.io/

## 1st usage

1. [Install Copier](https://copier.readthedocs.io/en/stable/#installation)
1. [Install pre-commit](https://pre-commit.com/#install)
1. Enter your project folder: `cd my-project`
1. Make it a git repo: `git init`
1. Run `copier copy https://github.com/copier-org/autopretty.git .`
1. Answer questions
1. Activate pre-commit: `pre-commit install`
1. Commit: `git commit -am 'Apply autoprettier'` (repeat if pre-commit reformats
   anything and makes the update fail)
1. Update your code `pre-commit run -a`
1. Commit: `git commit -am 'Run pre-commit'`

## Get updates

1. Enter your project folder: `cd my-project`
1. Update: `copier -a .copier-answers.autopretty.yml update`
1. Answer questions, if anything changed
1. Commit: `git commit -am 'Update autoprettier'` (repeat if pre-commit reformats
   anything and makes the update fail)
1. Update your code `pre-commit run -a`
1. Commit: `git commit -am 'Run pre-commit'`

## Notes for template maintainers

This template is self-applied, but due to 🐔+🥚 problems, to update it, this must be
done manually:

```bash
cd autopretty
copier -a .copier-answers.autopretty.upstream.yml -f -d js=false -d main_branches=[main] . .
mv -f .github/workflows/pre-commit.yml .github/workflows/pre-commit.upstream.yml
```

Not so nice, but neither so hard.
