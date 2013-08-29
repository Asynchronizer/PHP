## Asynchronizer's PHP API

---

This works hand-in-hand with the [Asynchronizer](https://github.com/Asynchronizer/jQuery/) JavaScript (and jQuery) file.

---

### Function List

```php
__construct( $account_id, $api_key, $api_password )
submit( $requester, $base64_queue )
```

---

### __construct() - Create a new instance of our Class.

Parameter(s)

```
int     $account_id     Your Raide Account ID.
string  $api_key        Your Raide API Key.
string  $api_password   Your Raide API Password.
```

Example(s)

```php
$Asynchronizer = new Asynchronizer( ACCOUNT_ID, API_KEY, API_PASSWORD );
```

---

### submit() - Submit a new Support Ticket.

Parameter(s)

```
mixed   $requester      Either an e-mail address or an array {email, id, name}.
string  $base64_queue   A base64-encoded string provided by the RaideIOTraffic Object.
```

Example(s)

```php
try
{
    // Submit all queued requests from the e-mail address kevin@asynchronizer.com
    $submit = $Asynchronizer->submit( "kevin@asynchronizer.com", $_POST["queue"] );

    // Print the results.
    print_r( $submit );
  
    // Submit all queued requests and associate it with a User from your application.
    $submit = $Asynchronizer->submit( array(
        "email" => "kevin@asynchronizer.com",
        "id"    => 4,
        "name"  => "Kevin D"
    ), $_POST["queue"] );
  
    // Print the results.
    print_r( $submit );
}
catch( Exception $e )
{
    die( $e->getMessage( ) );
}
```
