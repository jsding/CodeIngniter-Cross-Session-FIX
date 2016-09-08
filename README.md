In many cases, we want to use PHP native $_SESSION data in CodeIgniter application.
Since V3, CodeIgniter implement it's own session hander that make all $_SESSION lost.

## define variable that keep the native $_SESSION data ##
```
  protected $_cross_session_data;
```
## obtain all native session data ##
```
// FIX: keep external session data
session_start();
$this->_cross_session_data = array_merge(array(), $_SESSION);
session_destroy();
// FIX: END
```
## copy the php native session data into CodeIgniter ##
```
// FIX: keep external session data
if ($this->_cross_session_data) {
  foreach($this->_cross_session_data as $key => $value) {
    $_SESSION[$key] = $value;
  }
}
// FIX: END
```

[DbFace](https://www.dbface.com "Reports and Dashboards builder for SQL databases")
