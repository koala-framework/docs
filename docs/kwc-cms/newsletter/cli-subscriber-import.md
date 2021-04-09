# Import Newsletter Subscribers (CLI)

Import newsletter subscribers using the command-line in projects using [kwc-newsletter](https://github.com/koala-framework/kwc-newsletter).

### Import Command

```bash
kwf symfony kwc_newsletter:import-subscribers
    --file=[path to csv of subscribers]
    --newsletterComponentId=[component-id of target newsletter]
    --categoryId=[id of target newsletter category]
    --source=[Short message, where the subscribers came from]
    --newsletterSource=[optional newsletter-source]
    --ignoreDoubleOptIn [optional, only specify if the subscribers should be set to "active" immediately]
```

### CSV Of Subscribers

Following fields can be set in the CSV File:
- email [required]
- title [optional]
- firstname [optional]
- lastname [optional]
- gender [optional - if specified this must be "male" or "female"]

### Example.csv
```
title;gender;firstname;lastname;email
Dr.;male;Lorem;Ipsum;lorem@ipsum.com
;female;Lorem;Ipsum;lorem2@ipsum.com
;male;Lorem;Ipsum;lorem3@ipsum.com
```

### Example Import Command

```bash
kwf symfony kwc_newsletter:import-subscribers --file=new_owners_april_2020.csv --newsletterComponentId=root-at_newsletter --categoryId=1000 --source="New Owners April 2020"
```

## Combine Newsletter-Categories


```bash
kwf symfony kwc_newsletter:combine-category-subscribers
    --newsletterComponentId=[component-id of target newsletter]
    --sourceCategoryIds=[id of source newsletter category]
    --targetCategoryId=[id of target newsletter category]
    --source=[Short message for log]
```

### Example

The following command will delete the source-category and add every subscriber of the source-category to the target-category.

```bash
kwf symfony kwc_newsletter:combine-category-subscribers --newsletterComponentId=root_newsletter --sourceCategoryIds=200 --targetCategoryId=250 --source="Move subscribers from 200 into 250"
```
