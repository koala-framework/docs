# Using external fonts
In Koala Framework 5.0 and later.

## Using webfontloader
#### 1. Add webfontloader to `composer.json`:

```js
"extra": {
    "require-npm": {
        "webfontloader": "^1.6.28"
    }
}
```

#### 2. Load your font in `themes/Theme/Web.js`:

```js
var WebFont = require('webfontloader');
WebFont.load({
    monotype: {
        projectId: 'my-awesome-font-project'
   }
});
```

#### 3. Make sure Web.js has been added to your assets in the `getRootSettings()` function of `themes/Theme/Component.php`:

```php
$ret['assets']['files'][] = 'web/themes/Theme/Web.js';
```

## Using a font repository
#### 1. Add your font repository to `composer.json`:

```js
"extra": {
    "require-bower": {
        "myawesomefonts": "git@example.com:user/myawesomefonts.git#1.0.0"
    }
}
```

#### 2. Add the fonts to your assets in the `getRootSettings()` function of `themes/Theme/Component.php`:
```php
$ret['assets']['files'][] = 'myawesomefonts/fonts.css';
```

<br>
<br>
Then run `composer update`, build the project and have fun with your fonts.
