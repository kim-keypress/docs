# Admin panel resources not loading

## Problem

You're not using the default craft folder structure and the Admin panel resources css, js, ... are not loading

## Possible causes

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

### 2. set_time_limit() is blocked on your server

#### Cause

The set_time_limit() function is blocked by your hosting provider, this can give uncaught errors at multiple locations.

#### Solution

For me the problem was in `vendor/yiisoft/yii2/web/Response.php` in the `sendContent` method. A couple of lines in, the existence of the function is checked but the errors should be suppressed as well. To do this you just have to add an @ in front off the function call.

```php
if (function_exists('set_time_limit')) {
	@set_time_limit(0); // Reset time limit for big files
} else {
	Yii::warning('set_time_limit() is not available', __METHOD__);
}
```

