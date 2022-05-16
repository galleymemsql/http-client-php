# SingleStore\HttpApi

All URIs are relative to http://localhost.

Method | HTTP request | Description
------------- | ------------- | -------------
[**exec()**](HttpApi.md#exec) | **POST** /api/v2/exec | Exec
[**ping()**](HttpApi.md#ping) | **GET** /ping | Ping
[**rows()**](HttpApi.md#rows) | **POST** /api/v2/query/rows | Query
[**spec()**](HttpApi.md#spec) | **GET** /api/v2/spec | Spec
[**tuples()**](HttpApi.md#tuples) | **POST** /api/v2/query/tuples | Query


## `exec()`

```php
exec($exec_input): \SingleStore\Client\ExecOutput
```

Exec

Executes a SQL statement without returning result sets; typically used for executing DDL and DML statements for which result sets are not expected, such as CREATE TABLE and INSERT statements.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: BasicAuth
$config = SingleStore\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new SingleStore\Api\HttpApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$exec_input = new \SingleStore\Client\ExecInput(); // \SingleStore\Client\ExecInput | The request should include a JSON payload in the HTTP POST body. The payload must match the following specification precisely, invalid payloads will raise a validation error describing the issue.

try {
    $result = $apiInstance->exec($exec_input);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling HttpApi->exec: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **exec_input** | [**\SingleStore\Client\ExecInput**](../Model/ExecInput.md)| The request should include a JSON payload in the HTTP POST body. The payload must match the following specification precisely, invalid payloads will raise a validation error describing the issue. | [optional]

### Return type

[**\SingleStore\Client\ExecOutput**](../Model/ExecOutput.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `ping()`

```php
ping(): string
```

Ping

Verifies that the HTTP service is running and connectable.  Note: To verify that the database can receive queries or check specific health metrics, use the /exec and /query endpoints.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: BasicAuth
$config = SingleStore\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new SingleStore\Api\HttpApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->ping();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling HttpApi->ping: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

**string**

### Authorization

[BasicAuth](../../README.md#BasicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `text/plain`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `rows()`

```php
rows($query_input): \SingleStore\Client\QueryOutput
```

Query

Executes a SQL statement and returns result sets; typically used for the SELECT statement for which result sets are expected. The result sets contain column names mapped to row values in a single field.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: BasicAuth
$config = SingleStore\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new SingleStore\Api\HttpApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$query_input = new \SingleStore\Client\QueryInput(); // \SingleStore\Client\QueryInput | The request should include a JSON payload in the HTTP POST body. The payload must match the following specification precisely, invalid payloads will raise a validation error describing the issue.

try {
    $result = $apiInstance->rows($query_input);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling HttpApi->rows: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **query_input** | [**\SingleStore\Client\QueryInput**](../Model/QueryInput.md)| The request should include a JSON payload in the HTTP POST body. The payload must match the following specification precisely, invalid payloads will raise a validation error describing the issue. | [optional]

### Return type

[**\SingleStore\Client\QueryOutput**](../Model/QueryOutput.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `spec()`

```php
spec(): string
```

Spec

Returns the OpenAPI specification for this service.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: BasicAuth
$config = SingleStore\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new SingleStore\Api\HttpApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->spec();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling HttpApi->spec: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

**string**

### Authorization

[BasicAuth](../../README.md#BasicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `text/plain`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `tuples()`

```php
tuples($query_input): \SingleStore\Client\StreamOutput
```

Query

Executes a SQL statement and returns result sets along with the schema; typically used for the SELECT statement for which result sets are expected. The result sets contain rows and columns in separate fields with the schema displayed for each column.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: BasicAuth
$config = SingleStore\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new SingleStore\Api\HttpApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$query_input = new \SingleStore\Client\QueryInput(); // \SingleStore\Client\QueryInput | The request should include a JSON payload in the HTTP POST body.  The payload must match the following specification precisely, invalid payloads will raise a validation error describing the issue.

try {
    $result = $apiInstance->tuples($query_input);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling HttpApi->tuples: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **query_input** | [**\SingleStore\Client\QueryInput**](../Model/QueryInput.md)| The request should include a JSON payload in the HTTP POST body.  The payload must match the following specification precisely, invalid payloads will raise a validation error describing the issue. | [optional]

### Return type

[**\SingleStore\Client\StreamOutput**](../Model/StreamOutput.md)

### Authorization

[BasicAuth](../../README.md#BasicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
