# X-CITE

[![publish-badge]][publish-workflow]

This repository is for CyberInfrastructure Training and Education for
Synchrotron X-Ray Science (X-CITE) course materials.

X-CITE is geared toward the community of scientists and researchers
using the [CHESS] synchrotron X-ray facility and similar light
sources.

See [index] for an outline of the course material.

## Authoring content

The content in this repository is written in the form of markdown
files or Jupyter notebooks, and processed using [Quarto] in order to
generate the website seen at https://xcitecourse.org/.

(There is a backup site at https://x-cite.quarto.pub/, in case
https://xcitecourse.org/ becomes unavailable for some reason.)

To add/update content, do this:

- Download and install Quarto from [quarto.org][Quarto].
- Clone/fork this repository.
- Create a branch to work on, with `git checkout -b <branch-name>`.
- Add/edit content in the form of `.md`, `.qmd`, or `.ipynb` files.
  If you need tutorials or reference material about authoring, [Quarto
  Guide][quarto-guide] is very helpful.
- Run `quarto preview` in a terminal, which will start a local web
  server with a live preview that opens in your web browser.
- Once you are satisfied with your changes, commit them, push the
  branch to GitHub, and submit a pull request.  A project member will
  eventually review and merge the PR.

Once content is in the `main` branch of this GitHub repository, the
[publish] workflow should take care of the building and publishing the
site.

## License

The content in this repository is available under [Creative Commons
Attribution-ShareAlike 4.0 International][cc-by-sa] license.  Code
snippets may be used under [CC0 1.0 Universal][cc-zero] license.

Copyrights for logos are owned by the respective organizations.

<!-- References -->

[publish-workflow]: https://github.com/RENCI-NRIG/X-CITE/actions/workflows/publish.yml
[publish-badge]: https://github.com/RENCI-NRIG/X-CITE/actions/workflows/publish.yml/badge.svg (Publish)

[CHESS]: https://www.chess.cornell.edu/
[index]: ./index.md
[publish]: .github/workflows/publish.yml

[Quarto]: https://quarto.org/
[quarto-guide]: https://quarto.org/docs/guide/
[x-cite]: https://xcitecourse.org/

[cc-by-sa]: https://creativecommons.org/licenses/by-sa/4.0/
[cc-zero]: https://creativecommons.org/publicdomain/zero/1.0/
