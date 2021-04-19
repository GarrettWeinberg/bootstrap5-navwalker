# Sage 10 friendly Bootstrap 5 Navwalker

**Forked from [MWDelaney/sage-bootstrap4-navwalker](https://github.com/MWDelaney/sage-bootstrap4-navwalker)**

Sets up a Bootstrap 5 Navwalker for Sage 9-based themes.

To install, run the following in your Sage9-based theme directory:
```bash
composer require "mwdelaney/sage-bootstrap5-navwalker"
```

Include the navwalker in your `wp_nav_menu` function:

## As a [Controller](https://github.com/soberwp/controller) method (Recommended)
In your Controller, probably `app.php`
```php
/**
 * Primary Nav Menu arguments
 * @return array
 */
public function primarymenu() {
  $args = array(
    'theme_location'    => 'primary_navigation',
    'menu_class'        => 'navbar-nav',
    'walker'            => new \App\wp_bootstrap5_navwalker(),
    ...
  );
  return $args;
}
```

In your Blade file, probably `header.blade.php`
```php
@if (has_nav_menu('primary_navigation'))
  {!! wp_nav_menu($primarymenu) !!}
@endif
```

## Without Controller
If you're not setting up your template data with Controller, you'll need to fully reference the `\App\wp_bootstrap5_navwalker()`.
In your Blade file, probably `header.blade.php`
```php
@if (has_nav_menu('primary_navigation'))
  {!! wp_nav_menu(['theme_location' => 'primary_navigation', 'menu_class' => 'navbar-nav', 'walker' => new \App\wp_bootstrap5_navwalker()]) !!}
@endif
```
