#CONTROLLERS

Koala Framework relies on Zend_Controller, so you might want also [read the Zend documentation](https://framework.zend.com/manual/1.12/en/zend.controller.html) on that topic. 

Controllers are used to to implement all backend functionality. There is a number of predefined controllers in Koala Framework that you can either use directly or reuse by inheriting and configuring.

###For performance reasons controllers are not used for:
   
* component output
*  media output (images)
*  assets output (css/javascript)