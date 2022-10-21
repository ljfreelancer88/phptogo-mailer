# Very short description of the package

[![Latest Version on Packagist](https://img.shields.io/packagist/v/ljfreelancer88/daily.svg?style=flat-square)](https://packagist.org/packages/ljfreelancer88/daily)
[![Total Downloads](https://img.shields.io/packagist/dt/ljfreelancer88/daily.svg?style=flat-square)](https://packagist.org/packages/ljfreelancer88/daily)
![GitHub Actions](https://github.com/ljfreelancer88/daily/actions/workflows/main.yml/badge.svg)

This is where your description should go. Try and limit it to a paragraph or two, and maybe throw in a mention of what PSRs you support to avoid any confusion with users and contributors.

## Installation

You can install the package via composer:

```bash
composer require ljfreelancer88/daily
```

## Usage

```php
https://stripe.com/docs/api/authentication?lang=php
https://github.com/stripe/stripe-php/blob/master/lib/StripeClient.php
https://github.com/muxinc/mux-php
https://opensource.box.com/spout/docs/
https://docs.guzzlephp.org/en/stable/
https://github.com/amphp/http-client-psr7

use Ljfreelancer88\Configuration;
use Ljfreelancer88\Daily as DailyCo;
use Ljfreelancer88\Daily as DailyCo;

// Authentication Setup
$daily = Configuration::getDefaultConfiguration()
    ->setDomain(getenv('MUX_TOKEN_ID'))
    ->setUsername(getenv('MUX_TOKEN_ID'))
    ->setPassword(getenv('MUX_TOKEN_SECRET'));

// API Client Initialization
$assetsApi = new MuxPhp\Api\AssetsApi(
    new GuzzleHttp\Client(),
    $config
);

$daily->setRoom()->setPrivacy()->setProperties(['exp' => ])

// Authentication
curl --request GET \
  --url https://api.daily.co/v1/rooms \
  --header "Authorization: Bearer DAILY_API_KEY"


// Create a meeting room
curl --request POST \
     --url https://api.daily.co/v1/rooms \
     --header 'Authorization: Bearer $TOKEN' \
     --header 'Content-Type: application/json' \     

// Create a randomly named room that expires in an hour
curl -H "Content-Type: application/json" \
     -H "Authorization: Bearer $TOKEN" \
     -XPOST -d \
     '{"properties":{"exp":'`expr $(date +%s) + 3600`'}}' \
     https://api.daily.co/v1/rooms/

DailyCo()->setRoom()->setPrivacy()->setProperties(['properties' => ['exp' => ]])
        
//Create a private room with a human-readable name and devices turned off at start
curl -H "Content-Type: application/json" \
     -H "Authorization: Bearer $TOKEN" \
     -XPOST -d \
     '{"name": "getting-started-webinar",
       "privacy": "private",
       "properties" : {
          "start_audio_off":true,
          "start_video_off":true}}' \
     https://api.daily.co/v1/rooms/



// A GET request to /rooms/:name retrieves a room object.
//https://docs.daily.co/reference/rest-api/rooms/get-room-config
curl -H "Content-Type: application/json" \
     -H "Authorization: Bearer $TOKEN" \
     https://api.daily.co/v1/rooms/w2pp2cf4kltgFACPKXmX
                
A POST request to /rooms/:name modifies a room object's privacy or configuration properties.
https://docs.daily.co/reference/rest-api/rooms/set-room-config
Change a room's privacy

curl -H "Content-Type: application/json" \
     -H "Authorization: Bearer $TOKEN" \
     -XPOST -d '{"privacy":"private"}' \
     https://api.daily.co/v1/rooms/hello
        
Change a room's max_participants property

curl -H "Content-Type: application/json" \
     -H "Authorization: Bearer $TOKEN" \
     -XPOST -d \
     '{"properties":{"max_participants":20}}' \
     https://api.daily.co/v1/rooms/hello
        
Change a room's max_participants property back to default
curl -H "Content-Type: application/json" \
     -H "Authorization: Bearer $TOKEN" \
     -XPOST -d \
     '{"properties":{"max_participants":null}}' \
     https://api.daily.co/v1/rooms/hello
                                             
//returns a list of rooms in your domain
curl -H "Content-Type: application/json" \
     -H "Authorization: Bearer $TOKEN" \
     https://api.daily.co/v1/rooms?limit=5
        

// Pagination
# list your five most recently created rooms
curl -H "Content-Type: application/json" \
     -H "Authorization: Bearer DAILY_API_KEY" \
     https://api.daily.co/v1/rooms?limit=5

 # data[0] is your most recently created room

 # if you have at least five rooms,
 # data[4] is your fifth-newest room


A DELETE request to /rooms/:name deletes a room
https://docs.daily.co/reference/rest-api/rooms/delete-room

curl -H "Content-Type: application/json" \
     -H "Authorization: Bearer $TOKEN" \
     -XDELETE 
     https://api.daily.co/v1/rooms/room-0253

Sends a message to participants within a room
curl -H "Content-Type: application/json" \
     -H "Authorization: Bearer $TOKEN" \
     -XPOST -d '{"data":{"test": 1}, "recipient": "*"}' \
     https://api.daily.co/v1/rooms/hello
        
        

https://docs.daily.co/reference/rest-api

DailyCo
```

### Testing

```bash
composer test
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

## PHP Package Boilerplate

This package was generated using the [PHP Package Boilerplate](https://laravelpackageboilerplate.com) by [Beyond Code](http://beyondco.de/).
