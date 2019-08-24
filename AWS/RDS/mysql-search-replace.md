MySQL Search and Replace Query for WordPress

```
UPDATE  `MySQL_Table`
SET  `MySQL_Table_Column` = REPLACE(`MySQL_Table_Column`, 'oldString', 'newString')
WHERE  `MySQL_Table_Column` LIKE 'oldString%';
```

```
UPDATE `wpqw_posts` 
SET guid = REPLACE(guid, 'https://oldUrl.com/', 'https://newUrl.com/') 
WHERE `guid` LIKE 'https://oldUrl.com/%';
```

Doing a Search and Replace via SQL could be dangerous if you have links that you’re unaware of which shouldn’t be changed. You should Search and Replace only when you’re convinced that you have to change the text in your Database. You should always perform a Database backup before proceeding with any manual changes. This can easily be done through phpMyAdmin:

### Extra
```
curl -O https://wordpress.org/latest.tar.gz
tar xzvf latest.tar.gz --strip 1
tar -tf latest.tar.gz | head
```
