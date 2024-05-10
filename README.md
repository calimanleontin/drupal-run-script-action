# Runs a drush script on a remote Drupal 8+ instance

This GitHub action runs remote scripts over SSH to update a Drupal 8+ instance
## Inputs

- `server_name` - (Default: `server`) - Is the name of the server given in the SSH configuration (`.ssh/config`)
- `drush` - (Default: `./vendor/bin/drush`) - Name of Drush executable to use for deployments instead of default one from vendor
- `script_path` - (Required ) - The script to run

Here's an example how to configure a remote SSH server `myserver` given in the example below:

## Example

```yml
on:
  workflow_dispatch:

name: Tests and code
jobs:
  update:
    runs-on: ubuntu-latest
    steps:

      - name: "Reset test users"
        id: release
        uses: calimanleontin/drupal-run-script-action@1.x
        with:
          path: ${{ secrets.PROJECT_DIR }}/live
          server_name: myserver
          script_path: etc/scripts/reset_users.php
```