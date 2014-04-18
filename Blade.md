#Blade

[Back to topics](README.md#topics)

## XSS prevention / htmlentities
>tags: [xss, output, htmlentities, html, blade]

To protect your site from any XSS vulnerability and ensure that arbitrary variables are kept safe from children, triple curly braces should be used instead of double curly braces.

    {{-- Safe for Kids --}}
    {{{$article->Writeup}}}
    
    {{-- Not Safe for Kids --}}
    {{$article->Writeup}}
    
## Comments
>tags: [comments, blade, output]

Comments can be written in Blade templating - and kept well in the templates - using the following syntax:

    {{-- THIS IS A COMMENT --}}

## Optional Variables
>tags: [variables, blade, output, optional]

It is awesome that we can just show variables directly using the double or triple curly braces `{{{$title}}}`. However, sometimes these variables can be shown on certain pages, and other pages it will be missing.

You can use the `or` Blade syntax to define a default replacement when the variable does not show up: 

    {{{ $title or 'Default title' }}}
    
Or you can use the good ol' `isset()` to check if your variable exists

    @if isset($user)
        // ... code code code
    @endif

Or:

    {{ isset($user) ? $user : 'Guest' }}
