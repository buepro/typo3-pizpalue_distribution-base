# Pizpalue distribution base

This composer package serves as a base to start new [typo3](https://typo3.org) projects based on 
[pizpalue distribution](https://extensions.typo3.org/extension/pizpalue_distribution/).

## Quick start

1.  Get packages
    ```
    composer create-project buepro/typo3-pizpalue-distribution-base pizpalue 
    ```

1.  Enter project directory
    ```
    cd pizpalue
    ```

1.  Setup TYPO3
    ```
    php vendor/bin/typo3cms install:setup \
        --no-interaction \
        --database-user-name=typo3 \
        --database-user-password=typo3 \
        --database-host-name=127.0.0.1 \
        --database-port=3306 \
        --database-name=typo3 \
        --use-existing-database \
        --admin-user-name=admin \
        --admin-password=password \
        --site-setup-type=site
    ```

1.  Adjust `composer.json`

    To have more control maintaining the site the composer configuration might be adjusted according the 
    actual requirements. For this replace `"buepro/typo3-pizpalue-distribution": "^2.0.0"` with the required 
    packages:
    ```
    "typo3/cms-recycler": "^10.4",
    "typo3/cms-indexed-search": "^10.4",
    "typo3/cms-lowlevel": "^10.4",
    "typo3/cms-redirects": "^10.4",
    "buepro/typo3-pizpalue": "^11.4.1",
    "buepro/typo3-container-elements": "^1.0.0",
    "georgringer/news": "^8.5.0",
    "georgringer/eventnews": "^4.0.0",
    "friendsoftypo3/tt-address": "^5.2.0",
    "svewap/ws-flexslider": "^1.5.14",
    "buepro/typo3-timelog": "^1.6.0"
    ```
    > NOTE: Just add the needed packages. In many projects just `buepro/typo3-pizpalue` and 
    > `buepro/typo3-container-elements` are used.
   
    After modifying the composer configuration finalize the installation:
    ```
    composer finalize-installation
    ```