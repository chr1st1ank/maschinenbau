# Maschinenbau action

This github action synchronizes blueprints for common elements into github repositories.
Each blueprint is an ansible playbook. The built-in blueprints are in the 
[blueprints](./blueprints) folder.  

## Inputs
| Input Name | Description | Default Value |
|------------|-------------|---------------|
| `blueprint-repository` | The name of the repository to fetch blueprints from. | `chr1st1ank/maschinenbau` |
| `blueprints` | The names of the blueprints to install (space separated). | - |
| `blueprint-vars` | Extra variables to pass to the blueprint playbooks (space separated). | `license=apache2` |
| `target-branch` | Branch where the changes should be pushed to. | `maschinenbau-sync` |
| `push` | Whether to push the changes. | `true` |
| `github-token` | Github Token for pushing the changes | - |


## Example usage

```yaml
  - name: Maschinenbau
    uses: chr1st1ank/maschinenbau@main
    with:
      blueprints: github-paperwork
      github-token: ${{ secrets.GITHUB_TOKEN }}
```
