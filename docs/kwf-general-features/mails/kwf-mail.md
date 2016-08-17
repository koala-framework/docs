#KWF_MAIL

Kwf_Mail inherits Zend_Mail and adds support for the [config settings](config.md). Use it like Zend_Mail, also see the [ZF Docs](https://framework.zend.com/manual/1.12/en/zend.mail.html).

##Example:

    $mail = new Kwf_Mail();
    $mail->setBodyText('This is the text of the mail.');
    $mail->setFrom('somebody@example.com', 'Some Sender');
    $mail->addTo('somebody_else@example.com', 'Some Recipient');
    $mail->setSubject('TestSubject');
    $mail->send();