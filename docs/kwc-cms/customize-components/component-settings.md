#COMPONENT SETTINGS

Components have static settings that you can set in your custom component. To do that simply overwrite the getSettings method and return your own values. Keep in mind that this data needs to be static as it will be cached.
To get the list of possible settings for every component open it's `Component.php` and have a look at the existing settings.