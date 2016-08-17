#FORM VALIDATOR

Create a class extending `Zend_Validate_Abstract` or any subclass of this class. 
This way it's only possible to validate a single value of a form.

In `isValid` you have to implement your logic. It's also important to remember the reasons if it's not valid because 
getMessages should return an array of messages for the user to understand why his input wasn't allowed.
To set your validator to a field you have to call addValidator(Validator) for your field.
To create a validator considering different values of a form extend `Kwf_Validate_Row_Abstract` and 
implement `isValidRow($value, $row)`.

Row contains all data of your form.