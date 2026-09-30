# cobolwork-action-test

Runs [cobolwork](https://github.com/Portll/cobolwork)'s GitHub Action on GitHub-hosted runners, as
its [documentation](https://github.com/Portll/cobolwork/blob/main/docs/github-action.md) describes.

- `src/` holds two of cobolwork's bench cases. `COK.cbl` (007) checks the length of its
  communication area before reading it and passes the gate. `CNOEIB.cbl` (006) reads it without the
  check and fails it: that is the debt `main` carries.
- `.github/workflows/cobolwork.yml` gates pull requests in ratchet mode, against the pull request's
  base, and pushes to `main` in absolute mode, and uploads the SARIF to code scanning.
- `.github/workflows/exit-codes.yml` runs the action once for each exit status of `cobolwork build`
  and checks whether the step failed.

The COBOL is cobolwork's, under the GNU Affero General Public License 3.0 or later (`LICENSE`).
