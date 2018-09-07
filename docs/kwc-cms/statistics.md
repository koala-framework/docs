# STATISTICS
Koala Framework supports Google Analytics and Piwik (aka Matomo) right out of the box.  
To enable statistics you just need to add the component of your preferred method to your `Root_Component`:

```php 
<?php
class Root_Component extends Kwc_Root_Component
{
    public static function getSettings($param = null)
    {
        $ret = parent::getSettings($param);
        $ret['generators']['statistics'] = array(
            'class' => 'Kwf_Component_Generator_Box_Static',
            'component' => 'Your_Statistics_Component',
            'inherit' => true
        );
        return $ret;
    }
}
```

## Google Analytics

Use `Kwc_Statistics_Analytics_Component` as your statistics component.  
Then add your analytics-code to your `config.ini`:

```ini
statistics.analytics.code = UA-12345-6
```

## Piwik (Matomo)

Use `Kwc_Statistics_Piwik_Component` as your statistics component.  
Then add your piwik-domain and id to your `config.ini`:

```ini
statistics.piwik.domain = https://my.piwik-domain.com
statistics.piwik.id = 20
```

