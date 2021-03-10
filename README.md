# deep-search-JSON
js utility to find all instances of a key in an object and run a function on the parent object of each (with support for async functions)

## INSTALLATION
npm install deep-search-json

## USAGE

    const deepSearch = require(deep-search-json);
    var obj = {
      a: "1"
      b: "2"
      myKey: "hello world"
      d: [
        ...,
        {
          ...
          myKey: "hello world"
        }
        ...,
        ]
    }
    
    var newObj = deepSearch(obj, "myKey", (obj) => obj.myKey = "HELLO WORLD");
    
    /* NEW OBJECT
    *  {
    *    a: "1"
    *    b: "2"
    *    myKey: "HELLO WORLD"
    *    d: [
    *      ...,
    *      {
    *        ...
    *        myKey: "HELLO WORLD"
    *      }
    *      ...,
    *      ]
    *  }
    *
    */
    
# Note
does not currently support finding keys nested into each other eg:
    {
        myKey: {
            myKey: "hello world"
        }
    }
will only find the outer level, however you can work around through the function parameter by calling this search as part of your passed in function
