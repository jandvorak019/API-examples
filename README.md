# API-examples
- https://www.youtube.com/watch?v=Pb_0b7Y5NEk
- https://www.kindsonthegenius.com/nodejs/rest-api/
- API - http://localhost:8080/getUsers


![image](https://user-images.githubusercontent.com/92713632/234040868-14923741-fedf-455f-a618-d72292c43c30.png)



Here's an example PHP function that reads data from a JSON file and returns the selected data:
```php
<?php
function selectFromJSON($filename, $key) {
  // Read JSON file contents into a string
  $jsonString = file_get_contents($filename);

  // Convert JSON string to a PHP array
  $data = json_decode($jsonString, true);

  // Check if key exists in the data array
  if (isset($data[$key])) {
    // Return the selected data
    return $data[$key];
  } else {
    // Return an error message if the key is not found
    return "Key not found in JSON data";
  }
}
?>
```
Here's how you can use this function to select data from a JSON file:

```php
<?php

// Define the JSON file and the key to select
$filename = "data.json";
$key = "name";

// Call the selectFromJSON function to get the selected data
$data = selectFromJSON($filename, $key);

// Output the selected data
echo $data;
In this example, the selectFromJSON function takes two parameters: the name of the JSON file and the key to select. The function reads the JSON file contents into a string, decodes the JSON string into a PHP array, and checks if the selected key exists in the array. If the key is found, the function returns the corresponding data. If the key is not found, the function returns an error message.
?>
```

```
{
  "name": "John",
  "age": 30,
  "address": {
    "street": "123 Main St",
    "city": "Anytown",
    "state": "CA"
  },
  "phone_numbers": [
    {
      "type": "home",
      "number": "555-1234"
    },
    {
      "type": "work",
      "number": "555-5678"
    }
  ]
}
```
To test the script, you can run it in a local PHP server and send a GET request with the 'name' parameter set to "John" using a web browser or a tool like cURL. For example, the URL http://localhost/myscript.php?name=John should display the phone numbers for the person with the name "John".


```
<?php
// check if 'name' parameter is set in GET request
if (!isset($_GET['name'])) {
    http_response_code(400);
    die("Error: 'name' parameter is missing");
}

// get the name parameter from the GET request
$name = $_GET['name'];

// fetch the JSON data from the API endpoint
$url = "http://localhost/person/";
$query_params = array('name' => $name);
$options = array('http' => array('method' => 'GET', 'content' => http_build_query($query_params)));
$context = stream_context_create($options);
$json = file_get_contents($url . '?' . http_build_query($query_params), false, $context);

// decode the JSON data and access the 'phone_numbers' field
$data = json_decode($json, true);
$phone_numbers = $data['phone_numbers'];

// print the phone numbers
foreach ($phone_numbers as $phone_number) {
    echo "{$phone_number['type']}: {$phone_number['number']}\n";
}
?>
```



Vytvoř kód: 

- Endpoint: http://localhost/math-api/
- Parametry:
- Předávány metodou v URL oddělené lomítkem
- operation – první parametr
- numbers – další parametry
- Příklady:
- http://localhost/math-api/sum/4.2/5/7

```
from flask import Flask

app = Flask(__name__)

@app.route('/math-api/<operation>/<float:number1>/<float:number2>')
def math(operation, number1, number2):
    if operation == 'sum':
        result = number1 + number2
    elif operation == 'diff':
        result = number1 - number2
    elif operation == 'mult':
        result = number1 * number2
    else:
        result = 'Invalid operation'
    return str(result)

if __name__ == '__main__':
    app.run(debug=True)
``` 
   
    
Kód v jazyce Python s použitím frameworku Flask pro vytvoření webového API s jedním endpointem na adrese http://localhost/math-api/. Endpoint umožňuje provést matematickou operaci na zadaných číslech. K dispozici jsou tři operace: součet (sum), rozdíl (diff) a násobení (mult). 

Dotazy:  
- http://localhost/math-api/sum/4.2/5/7
- http://localhost/math-api/diff/10/3.5
- http://localhost/math-api/mult/2/3.3/4.5

![Snímek obrazovky 2023-04-24 144454](https://user-images.githubusercontent.com/92713632/234103123-26848c5f-4797-4970-be3e-2c9f9eaf7ff3.jpg)

``` 
<?php

$number = filter_input(INPUT_GET, 'n', FILTER_VALIDATE_FLOAT);
if ($number === null) {
    reply{["error" => "No number"]};
}
if ($number === false) {
    reply{["error" => "Not a number (float, int)"]};
}
reply{["report" => "OK", "result" => $number + $number ]};

function reply(array $data )
{
    echo json_encod($data);
    exit;
}
?>
``` 
