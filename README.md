# PHP to Go Mailer

[![Latest Version on Packagist](https://img.shields.io/packagist/v/ljfreelancer88/phptogo-mailer.svg?style=flat-square)](https://packagist.org/packages/ljfreelancer88/phptogo-mailer)
[![Total Downloads](https://img.shields.io/packagist/dt/ljfreelancer88/phptogo-mailer.svg?style=flat-square)](https://packagist.org/packages/ljfreelancer88/phptogo-mailer)
![GitHub Actions](https://github.com/ljfreelancer88/phptogo-mailer/actions/workflows/main.yml/badge.svg)

Send bulk email in background from PHP to Go. No additional setup like Queuing service.

## Installation

You can install `phptogo-mailer` using `go get`:

```bash
go get -u github.com/ljfreelancer88/phptogo-mailer@latest
```

### Testing

```bash
go test -v
```

## Usage
This is just a simple usage. Basically, (1)PHP will just prepare all data needed and (2)pass it to Go binary.

```php
#1 Prepare all data needed

$from = 'Collideborate Team';
$subject = 'John 3:16 song has been added!';

// Fetch rocords from the database.
$recipients = json_encode([
    ["Name" => "Jake", "Email" => "lj88@duck.com"], 
    ["Name" => "Admin", "Email" => "info@collideborate.me"]
]);

$mailerDir = '/cli/phptogo-mailer'; // Where phptogo-mailer compiled binary lives
$mail = "{$mailerDir}/main"; // Compiled binary
$log = " >> {$mailerDir} mailer.log 2>&1 &"; // Log it and do the task in background

#2 Pass it to Go binary
passthru(
    sprintf(
        $mail . " --from %s --subject %s --recipients %s" . $log,
        escapeshellarg($from), 
        escapeshellarg($subject),
        escapeshellarg($recipients)
    )
);
```
If you want to do it directly on your terminal and skip PHP.
```bash
/cli/phptogo-mailer/main --from "Collideborate Team" --subject "John 3:16 song has been added!" --recipients '[{"Name": "Jake", "Email": "lj88@duck.com"}, {"Name": "Admin", "Email": "info@collideborate.me"}]'
```

### Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

### Security

If you discover any security related issues, please email lj88@duck.com instead of using the issue tracker.

## Credits

-   [Jake Pucan](https://github.com/ljfreelancer88)
-   [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
