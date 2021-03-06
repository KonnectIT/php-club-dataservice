# Sportlink Club.Dataservice
This package contains a PHP wrapper around the Sportlink Club.Dataservice API. It aims to make working with the API a breeze.

#### Installation

Install the package using composer:
```
composer require pendonl/php-club-dataservice
```

Require the vendor/autoload.php file:
```
require 'vendor/autoload.php';
```

Create an instance of the API using your Sportlink Club.Dataservice Client ID:
```
use \PendoNL\ClubDataservice\Api as KnvbApi;
$api = new KnvbApi('client_id');
```

It al starts by getting the club details.
```
$club = $api->getClub()
```

All properties - similar to the json response provided by the API - are made public, so you are free to use `$club->clubnaam` for example. Once you get the club details you can proceed by requesting the teams and related entities.

```
$teams = $club->getTeams();
foreach($teams as $team) {

    // $team->teamnaam;

    // Get competitions
    $competitions = $team->competitions();
    
    foreach($competitions as $competition) {
    
        // $competition->competitienaam;
    
        // Fixtures
        $competition->fixtures();
        
        // Results
        $competition->results();
        
        // Table standings
        $competition->table();
        
    }
    
}
```

### Thanks to

- [KNVB Dataservice API Wrapper](https://github.com/fruitcake/php-knvb-dataservice-api) by @barryvdh - for providing a basis for this API wrapper.

### Security

If you discover any security related issues, please email joshua@pendo.nl instead of using the issue tracker.

### About Pendo

Pendo is a webdevelopment agency based in Maastricht, Netherlands. If you'd like, you can [visit our website](https://pendo.nl).

### License

The MIT License (MIT). Please see [License File](LICENSE) for more information.