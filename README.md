tParseJSON
============
tParseJSON is a Talend component which parses JSON document in a column and emits several rows which contains columns with JSON element values.

Please also refer [Wiki](https://github.com/ijokarumawak/tParseJSON/wiki). There is a screenshot of this component configuration.

How To Use it
==============

Basic Settings
---------------

- ***Schema***: Set output schema, there is a limitation of acceptable type, please reffer "Schema" section below.
- ***Input Object***: specify where the JSON document is. If you want to parse a JSON within a row which comes from a data flow named "row1" and the column named "column1" holds the JSON, then 'Input Object' should be **row1.column1** (without quote)
- ***Loop JsonPath Query***: Specify a JSONPath to define what elements are the record elements. If you have a JSON look like {people: [{name: "foo", age: 23}, {name: "var", age:31}]} and you want to iterate every person in the people array, then the Loop JsonPath Query should be **"people[*]"** (with quote). This component emits rows from this JSONPath result.
- ***Query mapping***: Specify which JSON element is mapped to the output column. The JSONPaths are relevant path from the element you extract with 'Loop JsonPath Query'. So, if you want to extract name and age from the example JSON described above, then 'name' column's JSONPath Query should be **"name"** and 'age' column's is **"age"**.

Schema
=======
Currently, tParseJSON can output these type of columns (and available JSON types). I think it is enough based on the JSON specification.

- String (string, any)
- Object (object)
- Integer (number)
- Double (number)
- Long (number)
- Boolean (true, false)
- List (array)


Release note
=============

0.2
----

- Make JSON Path query optional.
- Add proper type conversion. It used to treat all values as String.


0.1
----
Initial release.