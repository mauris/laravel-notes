# Mail

[Back to topics](README.md#topics)

## Pretending / Faking mail() when on local development
>tags: [mail, pretend, environment]

We all know that it is difficult to mock or test `mail()` on local development environment. I used to set up hMailServer on my Windows computer and created a mail box in Mozilla Thunderbird to view the messages sent out.

Fortunately, Laravel came with a handy feature to switch `Mail::send()` to **pretend** mode.

On my repository, I created a set of `dev` environment settings, where a `mail.php` configuration exists. The following is my configuration:

````php
<?php

return array(
    'from' => array('address' => 'no-reply@localhost', 'name' => 'Localhost Admin'),
    'pretend' => true
);
````

`mail.pretend` configuration tells the `Mail` package not to attempt any actual sending of email. Instead, it will simply write a message to log that a pretend message was executed.

## Viewing Pretend Mails
>tags: [pretend, mail. logging]

Pretend is cool. We don't need to set up mail servers and all in order to test if mails were sent out. However, the log entry does not show the email contest. 

One trick to show the email contest, is to detect if the configuration is set to `mail.pretend` = true, then log the rendered view.

Simply paste the following code before all `Mail::send()` statements:

````php
if (Config::get('mail.pretend')) {
    Log::info(View::make('submissions.email', $data)->render());
}
````

And you can view your emails sent out in the log file.
