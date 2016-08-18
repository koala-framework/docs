#RECIPIENTS PLACEHOLDER

####If you are sending your mail via Kwc_Mail_Abstract_Component->send() you can use following placeholder in your template. Those will be substituted by the mail component and filled with data from your recipient.

* %firstname%
* %lastname%

####If Kwc_Mail_Recipient_TitleInterface is implemented:

* %salutation_polite% = "Dear Mr. {0} {1}", "Dear Mrs. {0} {1}" or "Dear Sir or Madam" (0 = title, 1 = lastname)
* %salutation_title% = "Mr. {0}", "Mrs. {0}" or only title. (0 = title)
* %title%

####If Kwc_Mail_Recipient_GenderInterface is implemented:

* %salutation_polite_notitle%= "Dear Mr. {0}
* %salutation_hello%= "Hello Mr. {0}"
* %salutation%= "Mr."
* %salutation_firstname% = "Dear {0}"