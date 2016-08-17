#PARSING

When a new string is added to the source code, it must be added to `trl.xml` (in application or kwf, depending on source). 
But this doesn't need to be done manually, Koala provides a cli controller that does that automatically: 

`php bootstrap.php trl-parse`