#USER RELATED CONFIG SETTINGS

There different settings related to users:

##User Model

    user.model = Kwf_User_Model
    
Change this setting to use a custom user model. Your own user model has at least to extend `Kwf_User_Model`.

##User Forms

    user.form.self = Kwf_User_Form
    user.form.grid = Kwf_User_Form
    
With these settings you can change the form used when editing users. Using that you can add new fields to a user.

* `self` is used when the user edits himself (link in the top right)
* `grid` is used in the user management grid, use a different form if the user should not be able to change settings himself

##Pasword Validator

    user.passwordValidator = Kwf_Validate_Password3of4
    
    
Using that setting you can change the validator used on passwords. Set to false to have no validator at all.

The default is fairly strict (and relatively secure)