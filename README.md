# SNMPWrapper
This is a fork of onurkose/snmpwrapper
Laravel SNMP package wrapper for Nelisys/Snmp class

## Requirements

Requires: [Nelisys/Snmp](https://github.com/nelisys/snmp) and net-snmp-utils

## Installation
Install via Composer.
```
$ composer require onurkose/snmp-wrapper
```

Add to ```config/app.php```.
```php
<?php

return [

    // ...

    'providers' => [
        // ...
        OnurKose\SNMPWrapper\SNMPWrapperServiceProvider::class,
    ],

    // ...

    'aliases' => [
        // ...
        'SNMPWrapper' => OnurKose\SNMPWrapper\Facades\SNMPWrapper::class,
    ],
];
```

## Usage
```php
<?php

namespace App\Http\Controllers;

use OnurKose\SNMPWrapper;

use App\Http\Controllers\Controller;

class SNMPController extends Controller
{

    public function get()
    {
        $snmp = new SNMPWrapper();
        
        $snmp::setHost('192.168.0.1', 'public', '2c');
        
        dd($snmp::get('.1.3.6.1.2.1.1.1.0'));
    }
}
```

Result of the test method get()

```shell
Array
(
    [.1.3.6.1.2.1.1.1.0] => LigoDLB 5-20n v7.57.51319
)
```

## License
Laravel SNMPWrapper is open-sourced software licensed under the [MIT license](LICENSE).
