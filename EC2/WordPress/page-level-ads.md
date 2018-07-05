## Conditional Tags

AdSense Auto Ads conditional show/hide for WP child theme

```
<?php if(in_category('CATEGORY')) : ?>
 /*$first_condition is true*/
 show something else for specific category
<?php elseif (is_page( array( 5, 'About', 'Contact') )) : ?>
  /*$first_condition is false and $second_condition is true*/
 <!--hide auto ads on pages -->
 <?php else: ?>
  /*$first_condition and $second_condition are false*/
  <!-- Page Level Ads -->
<?php endif ?>
```

Note: Publishers are not permitted to place ads on any non-content-based pages like thank you, error, login, or exit pages.
