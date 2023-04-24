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


