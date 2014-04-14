#Blade

[Back to topics](readme.md)

## XSS prevention / htmlentities
>tags: [xss, output, htmlentities, html, blade]

To protect your site from any XSS vulnerability and ensure that arbitrary user are kept safe from children, triple curly braces should be used instead of double curly braces.

    {{-- Safe for Kids --}}
    {{{$article->Writeup}}}
    
    {{-- Not Safe for Kids --}}
    {{$article->Writeup}}
    
## Comments
>tags: [comments, blade, output]

Comments can be written in Blade templating - and kept well in the templates - using the following syntax:

    {{-- THIS IS A COMMENT --}}
