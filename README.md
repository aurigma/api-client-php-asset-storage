# Aurigma Customer's Canvas SDK - Asset Storage API Client
======================================================

This module is a PHP API client for Asset Storage API which is a part of [**Customer's Canvas**](https://customerscanvas.com) web-to-print system. It is supposed that you are familiar with its services and understand how to use its APIs. To learn more about Customer's Canvas and its services, refer the [Getting Started section of its documentation](https://customerscanvas.com/dev/getting-started/intro.html).

## Pre-requisites

To be able to use this package, you need to meet the following requirements:

* You must have an account at Customer's Canvas.

For other platforms, see the [Backend services](https://customerscanvas.com/dev/getting-started/about-backend-services.html) article in Customer's Canvas documentation.

## Installation

```
composer require aurigma/asset-storage-api-client
```

### Requirements

PHP 7.4 and later.

### Composer

To install the bindings via [Composer](https://getcomposer.org/), add the following to `composer.json`:

```json
{
  "require": {
    "aurigma/asset-storage-api-client": "*@dev"
  }
}
```

Then run `composer install`

## Getting Started

Please follow the [installation procedure](#installation).

Receive an access token through your backend as explained in the [documentation](https://customerscanvas.com/dev/getting-started/about-backend-services.html#authorization) and deliver it to your app. 

Then run the following:

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

// Configure API key authorization: ApiKey
$config = Aurigma\AssetStorage\Configuration::getDefaultConfiguration()->setApiKey('X-API-Key', 'YOUR_API_KEY');

// Configure OAuth2 access token for authorization: OAuth2ClientCredentials
$config = Aurigma\AssetStorage\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

$apiInstance = new Aurigma\AssetStorage\Api\ArtifactsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$file = "/path/to/file.txt"; // \SplFileObject | File content.
$name = 'name_example'; // string | Entity name.
$tenant_id = 56; // int | Tenant ID.
$description = 'description_example'; // string | Artifact description.
$group = 'group_example'; // string | Artifact group.
$alias = 'alias_example'; // string | Artifact alias (special name within group).
$type = new \Aurigma\AssetStorage\Model\ArtifactType(); // \Aurigma\AssetStorage\Model\ArtifactType | Artifact type.
$format = 'format_example'; // string | Artifact file format.
$anonymous_access = True; // bool | Artifact 'anonymous access' tag. It indicates whether artifact can be accessed anonymously.
$custom_fields = NULL; // array<string,mixed> | Entity custom attributes.

try {
    $result = $apiInstance->artifactsCreate($file, $name, $tenant_id, $description, $group, $alias, $type, $format, $anonymous_access, $custom_fields);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ArtifactsApi->artifactsCreate: ', $e->getMessage(), PHP_EOL;
}
?>
```

## Author

Aurigma Inc <info@aurigma.com> (https://customerscanvas.com)
