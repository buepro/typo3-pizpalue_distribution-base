# Pizpalue distribution base

This composer package serves as a base to start new [typo3](https://typo3.org) projects based on 
[pizpalue distribution](https://extensions.typo3.org/extension/pizpalue_distribution/).

## Quick start

1. Get packages
    ```
    composer create-project buepro/typo3-pizpalue-distribution-base pizpalue 
    ```

1. Enter project directory
    ```
    cd pizpalue
    ```

1. Setup TYPO3
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

1. Reactivate extensions
    ```
    vendor/bin/typo3cms extension:setupactive
    vendor/bin/typo3cms extension:deactivate user_pizpalue
    vendor/bin/typo3cms extension:deactivate pizpalue_distribution
    vendor/bin/typo3cms extension:deactivate pizpalue
    vendor/bin/typo3cms extension:deactivate bootstrap_package
    vendor/bin/typo3cms extension:activate bootstrap_package
    vendor/bin/typo3cms extension:activate pizpalue
    vendor/bin/typo3cms extension:activate pizpalue_distribution
    vendor/bin/typo3cms extension:activate user_pizpalue
    vendor/bin/typo3cms extension:activate flux
    vendor/bin/typo3cms extension:activate flux_elements
    vendor/bin/typo3cms cache:flush
    ```