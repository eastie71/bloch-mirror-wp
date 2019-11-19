# bloch-mirror-wp
Bloch Mirror Wordpress Empty Site setup
Thanks to https://www.smashingmagazine.com/2019/03/composer-wordpress/

A very simple repo example for setting up a new Wordpress site with minimum code.
This makes use of the Composer PHP package installer for Wordpress CORE and Wordpress PLUGINS, and default THEMES

Instructions for setting up a NEW WP site using this REPO:
- Clone this repo
- Make sure you have "composer" installed. See: https://getcomposer.org/doc/00-intro.md
- Create a new (empty) database in your chosen MYSQL tool/app
- In the NEW root repo folder enter command "composer install --prefer-dist"
- Create a copy of the "wp/wp-config-sample.php" into the root folder as "wp-config.php"
- Modify the "wp-config.php" to have following - just before the database variable setup:
```
// Load Composer’s autoloader
require_once (__DIR__.'/content/vendor/autoload.php');

// Move the location of the content dir
define('WP_CONTENT_DIR', dirname(__FILE__).'/content');

$s = empty($_SERVER["HTTPS"]) ? '' : ($_SERVER["HTTPS"] == "on") ? "s" : "";
$sp = strtolower($_SERVER["SERVER_PROTOCOL"]);
$protocol = substr($sp, 0, strpos($sp, "/")) . $s;
$port = ($_SERVER["SERVER_PORT"] == "80") ? "" : (":".$_SERVER["SERVER_PORT"]);
define('WP_CONTENT_URL', $protocol."://".$_SERVER['SERVER_NAME'].$port.'/content');
```
- Modify the usual "DB_NAME", "DB_USER", and "DB_PASSWORD" to match your database (as from created above)
- Now 2 options:
  - Load up your WP site by going to the URL + /wp eg. http://domain.com/wp
  - Setup WP as new site - ie. Create the admin user and login
