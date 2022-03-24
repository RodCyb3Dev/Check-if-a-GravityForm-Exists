# Check-if-a-GravityForm-Exists
```php
/**
 * This checks if a GravityForm exists for a certain ID
 * 
 * @param  integer 		$id 	ID for the form to check
 * @return boolean 					if exists TRUE, if not FALSE.
 */
function rod_if_gravity_form_exists( $id ) {
 global $wpdb;
 
 // We checks the records in rg_form table where the form is recorded, simply use $wpdb class to query the SQL and If the value back is greater than 0, then the from exists.
 $gravityformtablename = $wpdb->prefix . 'rg_form';
 $countformssql = "SELECT COUNT( * ) FROM " . $gravityformtablename . " WHERE id = %d";
 $countforms = $wpdb->get_var( $wpdb->prepare( $countformssql, $id ) );
 
 if ( $countforms != 0 ) {
    return TRUE;
  } else {
    return FALSE;
  }
}
```

To use the function above, simply add:
```php
// Check if Gravity form of ID 1 Exists
if ( rod_if_gravity_form_exists( 2 ) ) { // 2 is the gravity_form ID
   // Form exists
} else {
   // Form does not exist
}
```
