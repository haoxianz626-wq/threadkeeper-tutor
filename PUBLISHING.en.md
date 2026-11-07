# Publishing and updating the public GitHub repository

[English](PUBLISHING.en.md) | [简体中文](PUBLISHING.md)

The public repository is [haoxianz626-wq/threadkeeper-tutor](https://github.com/haoxianz626-wq/threadkeeper-tutor). The canonical bilingual Skill is `SKILL.md` on `main`.

## Update an existing clone

```bash
git clone https://github.com/haoxianz626-wq/threadkeeper-tutor.git
cd threadkeeper-tutor
# Edit and test the files in both languages.
git add .
git commit -m "docs: improve bilingual tutor"
git push origin main
```

Git access and repository permissions are required. Contributors without push access can fork the repository and submit a pull request. Never commit private learning checkpoints or credentials.

## Release checklist

1. Verify `SKILL.md` has valid frontmatter (`name` and `description`), the correct version, and complete English/Chinese command aliases.
2. Check links in both README files and test both language prompts and checkpoint restoration.
3. Check JSON templates: same field schema; correct `language` and `language_mode` values.
4. Run [English tests](tests/scenarios.en.md) and [Chinese tests](tests/scenarios.md), including a mid-session language switch.
5. Check that `LICENSE` is present, repository visibility is public if sharing, and no personal state is tracked.
6. Optionally create a Git tag and GitHub Release for `v1.3.0`. A commit is not a tagged Release.

## Platform compatibility

GitHub publication is not an executable deployment. Agent Skills work when a host supports Skill discovery and reading. Others can use the standalone prompts.
