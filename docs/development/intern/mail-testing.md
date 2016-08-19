#SEND MAILS FOR TESTING

####Put the following into bootstrap.php and run "kwf" in the terminal from your project-folder:

    $view = new Kwf_View_Ext();
    $view->absoluteUrlPart = 'host url for example http://www.skoda.at';
    $html = $view->render('path to your template under views (without "views/")');
    $mail = new Kwf_Mail();
    $mail->setBodyHtml($html);
    $mail->setSubject('email subject');
    $mail->addTo('some email adress');
    $mail->send();