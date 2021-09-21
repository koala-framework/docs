# Delete newsletter subscribers using CLI

This will delete all newsletter subscribers, within a newsletter-component and newsletter-source.

The given params `newsletterComponentId` and `newsletterSource` must match the `newsletter_component_id` and `newsletter_source` columns respectively in the `kwc_newsletter_subscribers` table. 

## Command

```bash
kwf symfony kwc_newsletter:delete-newsletter-subscriber
    --newsletterComponentId=[component-id of target newsletter]
    --newsletterSource=[newsletter-source]
```

### Example

```bash
kwf symfony kwc_newsletter:delete-newsletter-subscriber --newsletterComponentId=root-at_newsletter --newsletterSource=newsletter
```
