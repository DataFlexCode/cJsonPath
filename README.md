# cJsonPath

cJsonPath.pkg

 A DataFlex class which will allow you to get either object handles or values from JSON
 objects using their path.
 
 Author:  Mike Peat
 Date:    06/02/2020

 Usage:
   To return a JSON object at a path:
       Get JsonAtPath of oJsonPathObject hoSourceJsonObject, path to hoVar
     Or:
       Move (JsonAtPath(oJsonPathObject, hoSourceJsonObject, path)) to hoVar

   To return a value at a path:
       Get ValueAtPath of oJsonPathObject hoSourceJsonObject path to sVar
     Or
       Move (ValueAtPath(oJsonPathObject, hoSourceJson, path)) to sVar

Path notation:

    A string with JSON object names, separated by dots "." and array indices
    in square brackets: "foo.bar.baz[0].bill[1][0]"

 Sample JSON:

    {
    	"foo": {
    		"bar": {
    			"baz": [
    				66.123,
    				{
    					"jim": "jack"
    				},
    				False,
    				{
    					"bob": 42
    				},
    				{
    					"kim": "possible"
    				},
    				[55, 1, 19, {
    					"Mork": [
    						[35, 67, 88, 100, [21, 33, 45, "Tim"]]
    					]
    				}]
    			]
    		}
    	}
    }

 Examples:
    
    Move (JsonAtPath(oJPath, hoJson, "foo.bar.baz[5][3].Mork[0][4][3]")) to hoObj

    Get ValueAtPath of oJPath hJson "foo.bar.baz[5][3].Mork[0][4][3]" to sVal
      (sVal = "Tim")

 In the first example the JSON object would be returned; if you then performed
 Move (JsonValue(hoObj)) to sVal you would get the same result as the second
 example - i.e. "Tim".

 NOTE: JSON is case-sensitive, so your path-strings must exactly match the
       object names ("foo" is *not* "Foo") in the JSON file.

