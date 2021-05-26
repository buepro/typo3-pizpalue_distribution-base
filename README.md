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

1.  Review `composer.json`

    1.  Enable platform check
    
        Depending on the hosting environment the platform check might be enabled:
        ```
        "platform-check": true,
        ```
    
    1.  Select packages
    
        To have more control maintaining the site the composer configuration might be adjusted according the 
        actual requirements. For this replace `"buepro/typo3-pizpalue-distribution": "^2.0.0"` with the required 
        packages:
        ```
        "buepro/typo3-bookmark-pages": "^2.0.1",
        "buepro/typo3-container-elements": "^2.1.0",
        "buepro/typo3-pizpalue": "^11.6.3",
        "buepro/typo3-timelog": "^1.6.0",
        "friendsoftypo3/tt-address": "^5.2.0",
        "georgringer/eventnews": "^4.0.0",
        "georgringer/news": "^8.5.0",
        "svewap/ws-flexslider": "^1.5.14",
        "typo3/cms-recycler": "^10.4",
        "typo3/cms-indexed-search": "^10.4",
        "typo3/cms-lowlevel": "^10.4",
        "typo3/cms-redirects": "^10.4"
        ```
        > NOTE: Just add the needed packages. In many projects just `buepro/typo3-pizpalue` and 
        `buepro/typo3-container-elements` are used.
   
1.  Finalize installation
    
    After modifying the composer configuration finalize the installation:
    ```
    composer finalize-installation
    ```