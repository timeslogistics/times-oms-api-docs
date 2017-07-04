Sample Code
===========

Sample code below are for reference only.

Please refer to corresponding API documents for latest field definitions.

Create order [POST /orders/{trackingNumber}] or [POST /orders]
-------------------------------------------------------------------

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
        'consigneeSubdistrict' => 'ท่ายาง',
        'consigneeDistrict' => 'เมืองพิษณุโลก',
        'consigneeProvince' => 'Bangkok',
        'consigneePostalCode' => '70150',
        'consigneeCompanyNameLocale' => '\u0e28\u0e38\u0e20\u0e0a\u0e31\u0e22  \u0e40\u0e1b\u0e35\u0e48\u0e22\u0e21\u0e17\u0e2d\u0e07',
        'consigneeContactNameLocale' => '\u0e28\u0e38\u0e20\u0e0a\u0e31\u0e22  \u0e40\u0e1b\u0e35\u0e48\u0e22\u0e21\u0e17\u0e2d\u0e07',
        'consigneeAddressLocale' => '90 100 \u0e21 8 \u0e15 \u0e08\u0e2d\u0e21\u0e1a\u0e36\u0e07  \u0e23\u0e32\u0e0a\u0e1a\u0e38\u0e23\u0e35  Ratchaburi \u0e08\u0e2d\u0e21\u0e1a\u0e36\u0e07  Chom Bueng 70150',
        'shipperCompanyName' => 'Client Company Limited',
        'shipperContactName' => 'John Lee',
        'shipperPhone' => '21800000',
        'shipperAddress' => 'Room 88, Some Building, District, N.T.',
        'shipperSubdistrict' => 'Baoan',
        'shipperDistrict' => 'Shenzheng',
        'shipperProvince' => 'Guangdong',
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
  import org.json.JSONObject;

  import java.io.IOException;

  public class OrderCreate {
      public static void main(String[] args) {
          String token = "Tog6MsaTGzdKyssA1w5boxBOxsm6OfiqyQYgbYbZ2dHWz7UrQXMtYpbRLXpT";

          OkHttpClient client = new OkHttpClient();

          JSONObject jsonObject = new JSONObject();

          jsonObject
                .put("consigneeCompanyName", "Supachai Piamthong")
                .put("consigneeContactName", "Supachai Piamthong")
                .put("consigneePhone", "123456789")
                .put("consigneeAddress", "12 34 Moo 8 Chom Bueng Ratchaburi Ratchaburi Chom Bueng 70150")
                .put("consigneeSubdistrict", "ท่ายาง")
                .put("consigneeDistrict", "เมืองพิษณุโลก")
                .put("consigneeProvince", "Bangkok")
                .put("consigneeCountry", "Thailand")
                .put("consigneeDistrict", "Bangkok")
                .put("consigneePostalCode", "70150")
                .put("consigneeCompanyNameLocale", "\u0e28\u0e38\u0e20\u0e0a\u0e31\u0e22  \u0e40\u0e1b\u0e35\u0e48\u0e22\u0e21\u0e17\u0e2d\u0e07")
                .put("consigneeContactNameLocale", "\u0e28\u0e38\u0e20\u0e0a\u0e31\u0e22  \u0e40\u0e1b\u0e35\u0e48\u0e22\u0e21\u0e17\u0e2d\u0e07")
                .put("consigneeAddressLocale", "90 100 \u0e21 8 \u0e15 \u0e08\u0e2d\u0e21\u0e1a\u0e36\u0e07  \u0e23\u0e32\u0e0a\u0e1a\u0e38\u0e23\u0e35  Ratchaburi \u0e08\u0e2d\u0e21\u0e1a\u0e36\u0e07  Chom Bueng 70150")
                .put("shipperCompanyName", "Client Company Limited")
                .put("shipperContactName", "John Lee")
                .put("shipperPhone", "21800000")
                .put("shipperAddress", "Room 88, Some Building, District, N.T.")
                .put("shipperSubdistrict", "Baoan")
                .put("shipperDistrict", "China")
                .put("shipperProvince", "Guangdong")
                .put("shipperCountry", "China")
                .put("shipperPostalCode", "000000")
                .put("paymentMethod", "COD")
                .put("parcelValue", "5888")
                .put("productType", "Express")
                .put("shipmentType", "Mobile & Tablet")
                .put("salePlatformName", "Amazon")
                .put("referenceNumber", "HAWB12345678")
                .put("items[0][sku]", "sku-test-1234567890")
                .put("items[0][categoryId]", "ASQW987654")
                .put("items[0][categoryName]", "Mobile")
                .put("items[0][description]", "iPhone 7 32GB Black")
                .put("items[0][brand]", "Apple")
                .put("items[0][model]", "iphone 7")
                .put("items[0][pieces]", "1")
                .put("items[0][unitPrice]", "5888")
                .put("items[0][unitPriceCurrency]", "HKD")
                .put("items[0][CODValue]", "5888");

          RequestBody formBody = RequestBody.create(MediaType.parse("application/json; charset=utf-8"), jsonObject.toString());

          Request request = new Request.Builder()
                  .url("http://dev.timesoms.com/api/orders/MTK88888888")
                  .addHeader("Authorization", "Bearer " + token)
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

Receive Webhook Status Update
--------------------------------

PHP:

.. code-block:: php

  <?php
  require 'vendor/autoload.php';
  
  function webhook() {
      $webhook_secret = 'TLnrQjh0w1nZRv41UFEQXOuY0NgoIufTaEPagPqPNqNuSZF3o0AJGPFa56mt';
      
      try {
          $token = $this->getBearerToken();
          if (empty($token)) {
              throw new Exception("Authentication Error.");
          }
          if ($token != $webhook_secret) {
              throw new Exception("Authentication Error.");
          }
          
          /*
           * Get own reference number and their related timestamp 
           */
          
          $content = array();
          parse_str(urldecode(file_get_contents("php://input")), $content);
          
          $tracking_number = $content['tracking_number'];
          $reference_number = $content['reference_number'];
          $sort_in = $content['sort_in'];
          $sort_out = $content['sort_out'];
          $close_box = $content['close_box'];
          $handover_linehaul = $content['handover_linehaul'];
          $reject = $content['reject'];
          $return = $content['return'];
          $receive = $content['receive'];
                    
          /*
           * Check and update your database if authenticate successs
           */
          
          
 
          echo json_encode(
              array(
                  'tracking_number' => $tracking_number,
                  'reference_number' => $reference_number,
                  'message' => 'Success',
              )
          );
      } catch (Exception $e) {
          echo json_encode(
              array(
                  'message' => $e->getMessage(),
              )
          );
      }
  }
  
  function getAuthorizationHeader(){
      $headers = null;
      if (isset($_SERVER['Authorization'])) {
          $headers = trim($_SERVER["Authorization"]);
      }
      else if (isset($_SERVER['HTTP_AUTHORIZATION'])) { //Nginx or fast CGI
          $headers = trim($_SERVER["HTTP_AUTHORIZATION"]);
      } elseif (function_exists('apache_request_headers')) {
          $requestHeaders = apache_request_headers();
          // Server-side fix for bug in old Android versions (a nice side-effect of this fix means we don't care about capitalization for Authorization)
          $requestHeaders = array_combine(array_map('ucwords', array_keys($requestHeaders)), array_values($requestHeaders));
          //print_r($requestHeaders);
          if (isset($requestHeaders['Authorization'])) {
              $headers = trim($requestHeaders['Authorization']);
          }
      }
      return $headers;
  }
  
  function getBearerToken() {
      $headers = $this->getAuthorizationHeader();
      // HEADER: Get the access token from the header
      if (!empty($headers)) {
          if (preg_match('/Bearer\s(\S+)/', $headers, $matches)) {
              return $matches[1];
          }
      }
      return null;
  }
