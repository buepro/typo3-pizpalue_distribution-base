# Pizpalue distribution base

This composer package serves as a base to start new [typo3](https://typo3.org) projects based on
[pizpalue distribution](https://extensions.typo3.org/extension/pizpalue_distribution/).

It uses pizpalue version 14 and TYPO3 version 11.

## Quick start

1. **Check shell PHP version**

   Ensure that the PHP version from the shell is compatible with your TYPO3 version.


2. **Get packages**
   ```
   composer create-project buepro/typo3-pizpalue-distribution-base pizpalue
   ```

3. **Enter project directory**
   ```
   cd pizpalue
   ```

4. **Setup TYPO3**
   ```
   php vendor/bin/typo3cms install:setup \
   --no-interaction \
   --use-existing-database \
   --database-host-name="127.0.0.1" \
   --database-port="3306" \
   --database-name="db" \
   --database-user-name="db" \
   --database-user-password="db" \
   --admin-user-name="admin" \
   --admin-password="password" \
   --site-name="Pizpalue site" \
   --web-server-config="apache" \
   --skip-extension-setup
   ```
   > Extension setup is skipped due to a bug in the package `helhum/typo3-console`.

5. **Setup extensions**
   ```
   vendor/bin/typo3 extension:setup
   ```

6. **Review `composer.json`**

   1. Define packages

      Remove the dependency to `"buepro/typo3-pizpalue-distribution"` and all packages not required by the
      site.
      > NOTE: Just use the needed packages. In many projects just `buepro/typo3-pizpalue` and
      `buepro/typo3-container-elements` are required.

   2. Add repository for site package
      ```
      "repositories": [
         {
            "type": "vcs",
            "url": "../../git/typo3-user_pizpalue.git"
         }
      ],
      ```

   3. **Check PHP configuration**

      Make sure the PHP version used in the shell and for cron jobs corresponds to the PHP version used for running the
      website. In case they  differ you might need to add a platform configuration to `composer.json`. A possible
      platform configuration could look as following:
      ```
      "config": {
        "platform": {
          "php": "8.1.9"
        }
      }
      ```

   4. **Finalize installation**

      After modifying the composer configuration finalize the installation:
      ```
      composer finalize-installation
      ```

   5. **Update root template record**

      Not loaded extensions might still have their static template referenced in the root template record. This can result
      in incorrect rendering issues. To update the root template record open and save the template record on the root page.

   6. **Update the core regularly**

      To keep the core up to date a cron job might be defined. A possible command could be as following:
      ```
      cd ~/httpdocs/pizpalue && composer core-update
      ```
