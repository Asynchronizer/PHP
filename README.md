## Asynchronizer's PHP API 

---

This works hand-in-hand with the [Asynchronizer](https://github.com/Asynchronizer/jQuery/) JavaScript (and jQuery) file.

---

### Function List

```php
__construct( $account_id, $api_key, $api_password )
submit( $base64_queue, $requester )
```

---

### __construct() - Create a new instance of our Class.

Parameter(s)

```
int     $account_id     Your Asynchronizer Account ID.
string  $api_key        Your Asynchronizer API Key.
string  $api_password   Your Asynchronizer API Password.
```

Example(s)

```php
$Asynchronizer = new Asynchronizer( ACCOUNT_ID, API_KEY, API_PASSWORD );
```

---

### submit() - Submit all collected Asynchronous requests.

Parameter(s)

```
string  $base64_queue   A base64-encoded string provided by the Asynchronizer JavaScript file.
mixed   $requester      Either an e-mail address or an array {email, id, name}.
```

Example(s)

```php
try
{
    // Submit all queued requests from the e-mail address kevin@asynchronizer.com
    $submit = $Asynchronizer->submit( $_POST["queue"], "kevin@asynchronizer.com" );

    // Print the results.
    print_r( $submit );
  
    // Submit all queued requests and associate it with a User from your application.
    $submit = $Asynchronizer->submit( $_POST["queue"], array(
        "email" => "kevin@asynchronizer.com",
        "id"    => 4,
        "name"  => "Kevin D"
    ) );
  
    // Print the results.
    print_r( $submit );
}
catch( Exception $e )
{
    die( $e->getMessage( ) );
}
```
