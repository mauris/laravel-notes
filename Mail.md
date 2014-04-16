# Mail

[Back to topics](README.md#topics)

## Pretending / Faking mail() when on local development
>tags: [mail, pretend, environment]

We all know that it is difficult to mock or test `mail()` on local development environment. Fortunately, Laravel came with a handy feature to switch `Mail::send()` to **pretend** mode.

On my repository, I created a set of `dev` environment settings, where a `mail.php` configuration exists. The following is my configuration:

````php
<?php

return array(
    'from' => array('address' => 'no-reply@localhost', 'name' => 'Localhost Admin'),
    'pretend' => true
);
````

`mail.pretend` configuration tells the `Mail` package not to attempt any actual sending of email. Instead, it will simply write a message to log that a pretend message was executed.
