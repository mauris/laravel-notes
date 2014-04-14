#Validator

[Back to topics](README.md#topics)

## Validating File Upload
>tags: [image, intervention, extend, validator]

In most examples, a typical validation code in the controller looks like this:

````php
    $rules = array(
        'name' => 'required|max:60|min:6',
        'email' => 'required|email',
        'mobile' => 'required|numeric',
        'writeup' => 'required|min:100|max:10000',
        'attachment' => 'imagesize|min:10|max:8192|mimes:jpeg,png'
    );
    $input = Input::only(array_keys($rules));
    $validator = Validator::make($input, $rules, $messages);
    
    if ($validator->fails()) {
        return Redirect::back()->withInput($input)->withErrors($validator);
    }
````

This is cool - but I spent hours wondering why the validation for `attachment` (a File Upload field) did not fire at all. It is because `Input::only()` only takes the parameters from `$_GET` or `$_POST` based on the current request's HTTP method. 

I ended up with the solution of detecting the attachment and adding it to the validation `$input` variable:

````php
    // $rules = array( ...
    $input = Input::only(array_keys($rules));
    if (Input::hasFile('attachment')) {
        $input['attachment'] = Input::file('attachment');
    }
    $validator = Validator::make($input, $rules, $messages);
````

That will help.

PS: I am using custom validation and `intervention/image` package to detect the image dimensions.
