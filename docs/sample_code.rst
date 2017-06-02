Sample Code
===========

Create order [POST /order]
--------------------------

PHP:

.. code-block:: php

  <?php
  require 'vendor/autoload.php';

  $api_token = 'TLnrQjh0w1nZRv41UFEQXOuY0NgoIufTaEPagPqPNqNuSZF3o0AJGPFa56mt';

  try {
    $params = [
        'trackingNumber' => 'MTK88888888',
        'consigneeCompanyName' => 'ABC Company',
        'consigneeContactName' => 'Chris Wong',
        'consigneePhone' => '1878200',
        'consigneeAddress' => 'Room 123, Dummy Building, District, Kowloon',
        'consigneeCountry' => 'Hong Kong',
        'consigneePostalCode' => '00000',
        'shipperCompanyName' => 'Client Company Limited',
        'shipperContactName' => 'John Lee',
        'shipperPhone' => '21800000',
        'shipperAddress' => 'Room 88, Some Building, District, N.T.',
        'shipperCountry' => 'Hong Kong',
        'shipperPostalCode' => '000000',
        'parcelValue' => 5888,
        'paymentMethod' => 'COD',
        'shipmentType' => 'CROSS-BORDER',
        'referenceNumber' => 'HAWB12345678',
        'sortCode' => 'AB1234',
        'items[0][categoryId]' => '',
        'items[0][categoryName]' => '',
        'items[0][description]' => 'iPhone 7 32GB Black',
        'items[0][pieces]' => '1',
        'items[0][unitPrice]' => '5888',
        'items[0][unitPriceCurrency]' => 'HKD',
    ];

    $client = new GuzzleHttp\Client();
    $res = $client->request('POST', 'http://127.0.0.1:8010/api/order', [
        'headers' => [
            'Authorization' => "Bearer {$api_token}"
        ],
        'form_params' => $params
    ]);

    $statusCode = $res->getStatusCode();

    $body = $res->getBody();

    // 201
    var_dump($statusCode);

    // {"message":"Success","status_code":201}
    var_dump($body->getContents());

  } catch (GuzzleHttp\Exception\ClientException $e) {
    // 409 or else
    var_dump($e->getResponse()->getStatusCode());

    // {"message":"Tracking Number MTK88888888 already exist @ Local","status_code":409}
    var_dump($e->getResponse()->getBody()->getContents());
  }
