nusoap
======

<h2>Nusoap PHP library</h2> 

Copy of original library for supporting packagist composer.

Simple example of Soap client call -
```php
<?php
	require_once('lib/nusoap.php');

	$wsdl   = "http://<your_web_service_url>?wsdl";
	$client = new nusoap_client($wsdl, 'wsdl');
	
	// Input params
	$username = "username";
	$password = "pass";
	
	// In this demo, we use json data , you can use any other data format for same
	$json	  = '{"param1":"value1","param2":"value2"}';

	$client->setCredentials($username, $password);
    $error = $client->getError();
	
	if ($error)
	{
		echo $error; die();
	}
	
	$action = "webservice_methode_name"; // webservice method name
	
	$result = array();

	if (isset($action))
	{
		$result['response'] = $client->call($action, $json);
	}
	
	echo "<h3>Output : </h3>";
	echo $result['response'];
	echo "<h2>Request</h2>";
	echo "<pre>" . htmlspecialchars($client->request, ENT_QUOTES) . "</pre>";
	echo "<h2>Response</h2>";
	echo "<pre>" . htmlspecialchars($client->response, ENT_QUOTES) . "</pre>";
?>
```


