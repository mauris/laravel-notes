#Authentication

[Back to topics](README.md#topics)

## Changing 'auth' Filter Redirect URL
>tags: [authentication, filter, redirect]

I wanted to use the `'before' => 'auth' ` filter on my protected pages - but when authentication is required, the page redirects to a fixed `/login` URL. I wanted to change this URL to something else, like `/users/login`.

This was hardly documented, but the `auth` filter can be found in the `app/filters.php` file, where you can modify the closure:

````php
Route::filter('auth', function () {
    if (Auth::guest()) return Redirect::guest('login'); // update this to whatever you want.
});
````

Have a nice day and don't spend 1 hour trying to solve this like me.
