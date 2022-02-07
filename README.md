# Pizpalue distribution base

This composer package serves as a base to start new [typo3](https://typo3.org) projects based on 
[pizpalue distribution](https://extensions.typo3.org/extension/pizpalue_distribution/).

It uses pizpalue version 12 (bootstrap 5) and TYPO3 version 11.

## Quick start

1.  **Get packages**
    ```
    composer create-project buepro/typo3-pizpalue-distribution-base pizpalue 
    ```

1.  **Enter project directory**
    ```
    cd pizpalue
    ```

1.  **Setup TYPO3**
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
    --web-server-config="apache"
    ```

1.  **Review `composer.json`**

    1.  Enable platform check
    
        Depending on the hosting environment the platform check might be enabled:
        ```
        "platform-check": true,
        ```
    
    1.  Define packages
    
        To have more control maintaining the site the composer configuration might be adjusted according the 
        actual requirements. For this replace `"buepro/typo3-pizpalue-distribution": "^3.0.0"` with the required 
        packages:
        ```
        "buepro/typo3-container-elements": "^3.0.0",
        "buepro/typo3-pizpalue": "^12.0.0",
        "buepro/typo3-timelog": "^1.7.0",
        "friendsoftypo3/tt-address": "^5.2.1 || dev-master",
        "georgringer/news": "^8.5.2 || dev-master",
        "typo3/cms-base-distribution": "^11.3.0",
        "typo3/cms-indexed-search": "^11.3.0",
        "typo3/cms-lowlevel": "^11.3.0",
        "typo3/cms-recycler": "^11.3.0",
        "typo3/cms-redirects": "^11.3.0"
        ```
        > NOTE: Just add the needed packages. In many projects just `buepro/typo3-pizpalue` and 
        `buepro/typo3-container-elements` are used.
   
1.  **Finalize installation**
    
    After modifying the composer configuration finalize the installation:
    ```
    composer finalize-installation
    ```

1.  **Update root template record**
    Not loaded extensions might still have their static template referenced in the root template record.
    This can result in incorrect rendering issues. To update the root template record open and save the template
    record on the root page.