#CONFIGURATION

in `getSettings` you need to define `$ret['recipientSources'] = array('MODEL');` where MODEL is needed for statistics and redirect. Every Model that contains your recipients should be listed here.

Set `$ret['attachImages'] = true` if you need to send images with your mail and want to add it to the mail.

It's also possible to set sender address and name via getSettings.

