# Admin panel resources not loading

## Problem

You're not use the default craft folder structure and the Admin panel resources css, js, ... are not loading

## Possible solutions

### 1. @web alias is wrong

#### Cause

The @web alias is pointing to the wrong url, this alias is the base of all your admin panel resources `Craft::getAlias('@web') . '/cpresources'`.

#### Solution

Add the following to your config array in `config/general.php` or to your environment's config

```php
'aliases' => [
    '@web'  => 'https://right.url.here'
]
```

If it still doesn't work try emptying the `web/cpresources` folder.