# Order type

## Available operations.

1. [List orders](#list-orders)
2. [Create an order](#create-an-order)
3. [Update an order](#update-an-order)
4. [Delete an order](#delete-an-order)

### List orders

* Fetch all non-retired order types that match any specified parameters otherwise fetch all non-retired order types. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    ```console
    GET /ordertype
     ```

* #### Get a particular order type

    Retrieve a particular order.
If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    ```console
    GET /ordertype/:target_ordertype_uuid
    ```

### Create an order type

* To create an order type you need to specify below attributes in the request body. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | the name of the order type
    *description* | `String` | the description of the order type
    *javaClassName* | `Java Class` | the java class
    *parent* | `Order UUID` | the order uuid
    *conceptClasses* | `Array[] : Concept UUID` | the array of concept class

    ```console
        POST /ordertype
        {
          "name": "drug order",
          "description": "One 500mg tablet of Ciprofloxacin, twice a day",
          "parent": "070f0120-0283-4858-885d-a20d967729cf",
        }
    ```
    
### Update an order type

* Update an order type with given UUID, this method only modifies properties in the request. If the user not logged in to perform this action, a `401 Unauthorized` status returned.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | the name of the order type
    *description* | `String` | the description of the order type
    *javaClassName* | `Java Class` | the java class
    *parent* | `Order UUID` | the order uuid
    *conceptClasses* | `Array[] : Concept UUID` | the array of concept class

    ```console
        POST /ordertype/:target_ordertype_uuid
        {
          "name": "drug order",
          "description": "One 400mg tablet of Ciprofloxacin, twice a day"
        }
    ```

### Delete an order type

* Delete or void an order type by its UUID. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    ```console
        DELETE /ordertype/:target_ordertype_uuid
     ```