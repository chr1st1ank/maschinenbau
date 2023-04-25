# Maschinenbau action

This github action synchronizes blueprints for common elements into github repositories.
Each blueprint is an ansible playbook. The built-in blueprints are in the 
[blueprints](./blueprints) folder.  

## Inputs
| Input Name             | Description                                                           | Default Value             |
|------------------------|-----------------------------------------------------------------------|---------------------------|
| `blueprint-repository` | The name of the repository to fetch blueprints from.                  | `chr1st1ank/maschinenbau` |
| `blueprints`           | The names of the blueprints to install (space separated).             | -                         |
| `blueprint-vars`       | Extra variables to pass to the blueprint playbooks (space separated). | `license=apache2`         |
| `pull-request-branch`  | Branch where the changes should be pushed to.                         | `maschinenbau-sync`       |
| `base-branch`          | Branch to merge changes into.                                         | `main`                    |
| `push`                 | Whether to push the changes.                                          | `true`                    |
| `github-token`         | Github Token for pushing the changes.                                 | -                         |
| `pull-request-labels`  | Labels to apply to created pull requests.                             | `maschinenbau`            |


## Example usage

```yaml
  - name: Maschinenbau
    uses: chr1st1ank/maschinenbau@main
    with:
      blueprints: github-paperwork
      github-token: ${{ secrets.GITHUB_TOKEN }}
```

Or [use a github APP for authentication](https://github.com/peter-evans/create-pull-request/blob/main/docs/concepts-guidelines.md#authenticating-with-github-app-generated-tokens). This has the advantage that also PR checks are triggered:
```yaml
  - uses: tibdex/github-app-token@v1
    id: generate-token
    with:
      app_id: "${{ secrets.MASCHINENBAU_APP_ID }}"
      private_key: "${{ secrets.MASCHINENBAU_APP_PRIVATE_KEY }}"
  - name: Maschinenbau
    uses: chr1st1ank/maschinenbau@main
    with:
      blueprints: github-paperwork
      github-token: ${{ steps.generate-token.outputs.token }}
```
