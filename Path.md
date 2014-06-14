# Path

[Back to topics](README.md#topics)

## Getting paths to the different folders in Laravel

I found these functions on [a blog via Google](http://www.kathirvel.com/laravel-4-get-app-path-public-path-storage-path-base-path/). In my case, I used `public_path()` so that I can move uploaded images there.

````php
<?php

/**
 * Path to the 'app' folder
 */
echo app_path();

/**
 * Path to the project's root folder
 */
echo base_path();

/**
 * Path to the 'public' folder
 */
echo public_path();

/**
 * Path to the 'app/storage' folder
 */
echo storage_path();

?>
````
