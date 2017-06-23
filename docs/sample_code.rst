Sample Code
===========

Sample code below are for reference only.

Please refer to corresponding API documents for latest field definations.

Create order [POST /orders/{trackingNumber}]
--------------------------------------------

PHP:

.. code-block:: php

  <?php
  require 'vendor/autoload.php';

  $api_token = 'TLnrQjh0w1nZRv41UFEQXOuY0NgoIufTaEPagPqPNqNuSZF3o0AJGPFa56mt';

  try {
    $params = [
        'consigneeCompanyName' => 'Supachai Piamthong',
        'consigneeContactName' => 'Supachai Piamthong',
        'consigneePhone' => '123456789',
        'consigneeAddress' => '12 34 Moo 8 Chom Bueng Ratchaburi Ratchaburi Chom Bueng 70150',
        'consigneeCountry' => 'Thailand',
        'consigneeDistrict' => 'Bangkok',
        'consigneePostalCode' => '70150',
        'consigneeCompanyNameLocale' => '\u0e28\u0e38\u0e20\u0e0a\u0e31\u0e22  \u0e40\u0e1b\u0e35\u0e48\u0e22\u0e21\u0e17\u0e2d\u0e07',
        'consigneeContactNameLocale' => '\u0e28\u0e38\u0e20\u0e0a\u0e31\u0e22  \u0e40\u0e1b\u0e35\u0e48\u0e22\u0e21\u0e17\u0e2d\u0e07',
        'consigneeAddressLocale' => '90 100 \u0e21 8 \u0e15 \u0e08\u0e2d\u0e21\u0e1a\u0e36\u0e07  \u0e23\u0e32\u0e0a\u0e1a\u0e38\u0e23\u0e35  Ratchaburi \u0e08\u0e2d\u0e21\u0e1a\u0e36\u0e07  Chom Bueng 70150',
        'shipperCompanyName' => 'Client Company Limited',
        'shipperContactName' => 'John Lee',
        'shipperPhone' => '21800000',
        'shipperAddress' => 'Room 88, Some Building, District, N.T.',
        'shipperCountry' => 'China',
        'shipperPostalCode' => '000000',
        'paymentMethod' => 'COD',
        'parcelValue' => 5888,
        'productType' => 'Express',
        'shipmentType' => 'Mobile & Tablet',
        'salePlatformName' => 'Taobao',
        'referenceNumber' => 'HAWB12345678',
        'sortCode' => 'AB1234',
        'items[0][sku]' => 'sku-test-1234567890',
        'items[0][categoryId]' => 'ASQW987654',
        'items[0][categoryName]' => 'Mobile Phone',
        'items[0][description]' => 'iPhone 7 32GB Black',
        'items[0][brand]' => 'Apple',
        'items[0][model]' => 'iphone 7',
        'items[0][pieces]' => '1',
        'items[0][unitPrice]' => 5888,
        'items[0][unitPriceCurrency]' => 'THB',
        'items[0][CODValue]' => 5888,
    ];

    $client = new GuzzleHttp\Client();
    $res = $client->request('POST', 'http://127.0.0.1:8010/api/order', [
        'headers' => [
            'Authorization' => "Bearer {$api_token}"
        ],
        'json' => $params
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

Java:

.. code-block:: java

  import okhttp3.*;

  import java.io.IOException;

  public class OrderCreate {
    public static void main(String[] args) {

        OkHttpClient client = new OkHttpClient();

        RequestBody formBody = new FormBody.Builder()
                .add("consigneeCompanyName", "Supachai Piamthong")
                .add("consigneeContactName", "Supachai Piamthong")
                .add("consigneePhone", "123456789")
                .add("consigneeAddress", "12 34 Moo 8 Chom Bueng Ratchaburi Ratchaburi Chom Bueng 70150")
                .add("consigneeCountry", "Thailand")
                .add("consigneeDistrict", "Bangkok")
                .add("consigneePostalCode", "70150")
                .add("consigneeCompanyNameLocale", "\u0e28\u0e38\u0e20\u0e0a\u0e31\u0e22  \u0e40\u0e1b\u0e35\u0e48\u0e22\u0e21\u0e17\u0e2d\u0e07")
                .add("consigneeContactNameLocale", "\u0e28\u0e38\u0e20\u0e0a\u0e31\u0e22  \u0e40\u0e1b\u0e35\u0e48\u0e22\u0e21\u0e17\u0e2d\u0e07")
                .add("consigneeAddressLocale", "90 100 \u0e21 8 \u0e15 \u0e08\u0e2d\u0e21\u0e1a\u0e36\u0e07  \u0e23\u0e32\u0e0a\u0e1a\u0e38\u0e23\u0e35  Ratchaburi \u0e08\u0e2d\u0e21\u0e1a\u0e36\u0e07  Chom Bueng 70150")
                .add("shipperCompanyName", "Client Company Limited")
                .add("shipperContactName", "John Lee")
                .add("shipperPhone", "21800000")
                .add("shipperAddress", "Room 88, Some Building, District, N.T.")
                .add("shipperCountry", "China")
                .add("shipperPostalCode", "000000")
                .add("paymentMethod", "COD")
                .add("parcelValue", "5888")
                .add("productType", "Express")
                .add("shipmentType", "Mobile & Tablet")
                .add("salePlatformName", "Amazon")
                .add("referenceNumber", "HAWB12345678")
                .add("items[0][sku]", "sku-test-1234567890")
                .add("items[0][categoryId]", "ASQW987654")
                .add("items[0][categoryName]", "Mobile")
                .add("items[0][description]", "iPhone 7 32GB Black")
                .add("items[0][brand]", "Apple")
                .add("items[0][model]", "iphone 7")
                .add("items[0][pieces]", "1")
                .add("items[0][unitPrice]", "5888")
                .add("items[0][unitPriceCurrency]", "HKD")
                .add("items[0][CODValue]", "5888")
                .build();

        Request request = new Request.Builder()
                .url("http://127.0.0.1:8010/api/orders/MTK88888888")
                .addHeader("Authorization", "Bearer kazTyZlbtJEZ2KsGkPBFSas8sz16jcCzs00Kw59q7IqyiIrOqDml3x79xqAZ")
                .post(formBody)
                .build();

        try {
            Response response = client.newCall(request).execute();

            // 201
            System.out.println(response.code());

            // {"message":"Success","status_code":201}
            System.out.println(response.body().string());
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
  }

Get order [GET /orders/{trackingNumber}]
----------------------------------------

PHP:

.. code-block:: php

  <?php
  require 'vendor/autoload.php';

  $api_token = 'TLnrQjh0w1nZRv41UFEQXOuY0NgoIufTaEPagPqPNqNuSZF3o0AJGPFa56mt';

  try {
      $client = new GuzzleHttp\Client();
      $res = $client->request('GET', 'http://127.0.0.1:8010/api/orders/MTK88888888', [
          'headers' => [
              'Authorization' => "Bearer {$api_token}"
          ]
      ]);

      $statusCode = $res->getStatusCode();

      $body = $res->getBody();

      // 200
      var_dump($statusCode);

      // {"trackingNumber":"MTK88888888","milestones":{"upload":"2017-06-02 13:55:09","sort_in":null,"sort_out":null,"close_box":null,"handover_linehaul":null,"pickup":null,"export":null,"uplift":null,"import":null,"handover_lastmile":null}}
      var_dump($body->getContents());

  } catch (GuzzleHttp\Exception\ClientException $e) {
      // 404 or else
      var_dump($e->getResponse()->getStatusCode());

      // '{"message":"Order not found","status_code":404}
      var_dump($e->getResponse()->getBody()->getContents());

  }


Java:

.. code-block:: java

  import okhttp3.*;

  import java.io.IOException;

  public class OrderGet {
      public static void main (String[] args) {

          String token = "kazTyZlbtJEZ2KsGkPBFSas8sz16jcCzs00Kw59q7IqyiIrOqDml3x79xqAZ";

          OkHttpClient client = new OkHttpClient();

          Request request = new Request.Builder()
                  .url("http://127.0.0.1:8010/api/orders/MTK88888888")
                  .addHeader("Authorization", "Bearer " + token)
                  .get()
                  .build();

          try {
              Response response = client.newCall(request).execute();

              // 200
              System.out.println(response.code());

              // {"trackingNumber":"MTK88888888","milestones":{"upload":"2017-06-02 16:27:42","sort_in":null,"sort_out":null,"close_box":null,"handover_linehaul":null,"pickup":null,"export":null,"uplift":null,"import":null,"handover_lastmile":null}}
              System.out.println(response.body().string());
          } catch (IOException e) {
              e.printStackTrace();
          }
      }
  }
