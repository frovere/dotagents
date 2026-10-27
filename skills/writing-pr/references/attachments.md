# GitHub CLI attachments

Use `--attach` to upload local images or videos when publishing an authorized PR body or comment. GitHub CLI inserts the uploaded URLs into the body so the media renders inline. Uploads require push access to the repository; only image and media files are supported. See GitHub's [supported file types](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/attaching-files#image-and-media-files).

The flag is available on `gh pr create`, `gh pr edit`, and `gh pr comment`, and on the equivalent `gh issue` commands. Check the installed command's `--help` for flag availability; if uploads are unavailable, disclose the limitation.

## Draft with local references

For images, use ordinary Markdown with descriptive alt text. A before/after table can reference local files:

```markdown
| Before | After |
| --- | --- |
| ![Sign-in screen showing an authentication error](./before.png) | ![Sign-in screen showing the form](./after.png) |
```

For a video player, put the image-style reference alone in its paragraph:

```markdown
![](./demo.mp4)
```

A video reference within a sentence renders as a link instead of a player.

## Upload when publishing

Pass each referenced local file with `--attach`, using the same path as in the Markdown:

```shell
gh pr create \
  --base TARGET-BRANCH \
  --title "PR title" \
  --body-file ./pr-body.md \
  --attach ./before.png \
  --attach ./after.png
```

For an existing PR or a comment:

```shell
gh pr edit PR-NUMBER --body-file ./pr-body.md --attach ./demo.mp4
gh pr comment PR-NUMBER --body-file ./comment.md --attach ./demo.mp4
```

GitHub CLI rewrites matching local references to uploaded URLs in place, preserving surrounding Markdown and image alt text. This works with `--body`, `--body-file`, standard input, or the editor. For videos, it replaces the entire image-style reference with the uploaded URL.

Repeat `--attach` for multiple files; attach each file only once per command. Files without matching body references are appended in flag order. To give an appended image alt text, quote the path with a `#` suffix:

```shell
gh pr comment PR-NUMBER --body "Updated sign-in screen:" \
  --attach './after.png#Sign-in screen showing the form'
```

Without a suffix, appended images use the filename as alt text. For rewritten references, Markdown alt text takes precedence over the suffix. Video files do not support alt text.

After publishing, verify that the intended media appears at the intended positions, with uploaded URLs replacing local references and no unintended duplicate attachments. Report any upload or rendering gap.
