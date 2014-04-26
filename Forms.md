# Forms

[Back to topics](README.md#topics)

## Form Model and Explicit Values
>tags: [form, model, explicit, values]

When binding a model to its form, Laravel cleverly assigns values from the model's properties to it's matching form input counterpart:


    {{Form::model($user, array('route' => 'users.login'))}}
    
    {{Form::text('name')}}
    
    {{Form::password('password')}}
    
    {{Form::submit('Log In')
    
    {{Form::close()}}
    
This is cool. However, when we want to add attributes / classes in the 3rd parameter of `Form::text()`, we need to fill `null` in the second parameter (the explicit value):

    {{Form::text('name', null, array('class' => 'form-control'))}}
    
How Laravel decides which value to use for the input is through this order:

1. **Session Flash Data (Old Input)**  
   This value comes from a session flash via a Post-Redirect-Get
2. **Explicitly Passed Value**  
   This is the value that has been explicitly set in the declaration / 2nd parameter
3. **Model Attribute Data**  
   This is the value from the Model's property

If you place an empty string i.e. `''` in the 2nd parameter (explicitly passed value), the form will never show the value from the model.
