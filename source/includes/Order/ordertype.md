# Order type

* Orders represent requests from providers for some action to care for a patient. 
Common types of orders are prescriptions (drug orders), lab tests, radiology tests, 
procedures, and referrals.

* In nearly all cases, handling different types of orders requires specific behavior of 
the application. The OpenMRS platform is designed to handle certain types of orders. 
Adding new order types will usually only happen when new features to handle the 
new order type are also being added to the system (using a module or app).

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

* Order types depend on code within the application to properly handle them, so it would be unusual to create a new order type unless some new code (e.g., a module) has been added to the system to handle the new order type.

    #### Attributes

    Parameter | Type | Description
    --- | --- | ---
    *name* | `String` | the name of the order type
    *description* | `String` | the description of the order type
    *javaClassName* | `Java Class` | the java class
    *parent* | `Order UUID` | the order uuid
    *conceptClasses* | `Array[] : Concept UUID` | classes of concepts that can be used to generate an order of this type

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
    *conceptClasses* | `Array[] : Concept UUID` | classes of concepts that can be used to generate an order of this type

    ```console
        POST /ordertype/:target_ordertype_uuid
        {
          "name": "drug order",
          "description": "One 400mg tablet of Ciprofloxacin, twice a day"
        }
    ```

### Delete an order type

* Delete or retire an order type by its UUID. If not authenticated or authenticated user does not have sufficient privileges, a `401 Unauthorized` status is returned.

    ```console
        DELETE /ordertype/:target_ordertype_uuid
     ```