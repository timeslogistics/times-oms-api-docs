Sample Code
===========

Sample code below are for reference only.

Please refer to coresponding API documents for latest field definations.

Create order [POST /orders/{trackingNumber}]
--------------------------------------------

PHP:

.. code-block:: php

  <?php
  require 'vendor/autoload.php';

  $api_token = 'TLnrQjh0w1nZRv41UFEQXOuY0NgoIufTaEPagPqPNqNuSZF3o0AJGPFa56mt';

  try {
    $params = [
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
        'instruction' => '',
        'sortCode' => 'AB1234',
        'items[0][categoryId]' => '',
        'items[0][categoryName]' => '',
        'items[0][description]' => 'iPhone 7 32GB Black',
        'items[0][pieces]' => 1,
        'items[0][unitPrice]' => 5888,
        'items[0][unitPriceCurrency]' => 'HKD',
    ];

    $client = new GuzzleHttp\Client();
    $res = $client->request('POST', 'http://127.0.0.1:8010/api/order/MTK88888888', [
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

Java:

.. code-block:: java

  import okhttp3.*;

  import java.io.IOException;

  public class OrderCreate {
    public static void main(String[] args) {

        OkHttpClient client = new OkHttpClient();

        RequestBody formBody = new FormBody.Builder()
                .add("consigneeCompanyName", "ABC Company")
                .add("consigneeContactName", "Chris Wong")
                .add("consigneePhone", "1878200")
                .add("consigneeAddress", "Room 123, Dummy Building, District, Kowloon")
                .add("consigneeCountry", "Hong Kong")
                .add("consigneePostalCode", "00000")
                .add("shipperCompanyName", "Client Company Limited")
                .add("shipperContactName", "John Lee")
                .add("shipperPhone", "21800000")
                .add("shipperAddress", "Room 88, Some Building, District, N.T.")
                .add("shipperCountry", "Hong Kong")
                .add("shipperPostalCode", "000000")
                .add("parcelValue", "5888")
                .add("paymentMethod", "COD")
                .add("shipmentType", "CROSS-BORDER")
                .add("referenceNumber", "HAWB12345678")
                .add("instruction", "")
                .add("sortCode", "AB1234")
                .add("items[0][categoryId]", "")
                .add("items[0][categoryName]", "")
                .add("items[0][description]", "iPhone 7 32GB Black")
                .add("items[0][pieces]", "1")
                .add("items[0][unitPrice]", "5888")
                .add("items[0][unitPriceCurrency]", "HKD")
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
