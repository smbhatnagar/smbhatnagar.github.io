## ERD of Nike store using Mermaid and Markdown language
'''mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    CUSTOMER{
        String cust_id PK
        String cust_name "Only 30 characters allowed"
        Integer cust_phone_no "Only 10 numeric characters allowed"
        String cust_address "Only 99 characters allowed"
    }
    SALES ||--o{ ORDER_PRODUCT : "is generated"
    SALES{
        String sales_id PK
        String order_prod_id FK
        String invoice_details
        Date date "mm-dd-yyy format"
        String total_price "USD"
         }
    ORDER ||--|{ ORDER_PRODUCT : "customer orders"
    ORDER{
        String order_id PK
        String cust_id FK
    }
    PRODUCTS ||--o{ ORDER_PRODUCT : "ordered"
    PRODUCTS{
        String prod_id PK
        String prod_name 
        String prod_description 
        String unit_price
    }
    ORDER_PRODUCT{
        String order_prod_id PK
        String order_id FK
        String prod_id FK
    }
    INVENTORY ||--o{ PRODUCTS : has
    INVENTORY{
        String inv_id PK
        String prod_id FK
        Integer stock_level
    }
'''
#### Customer Entity
   > It contains customer details.
     Customer can place _Zero or Many_ orders.
#### Products Entity
   > It contains product details.
     One product can have _Zero or Many_ orders.
#### Order Entity
   > It contains order details.
     One order can have _One or Many_ products.
#### Order Product Entity
   > Corresponds to order related to products
     Since Products to Order is _Many to Many_ relationship so breaking down into a sub entity Order Product to map one to many relationship
#### Inventory
   > Contains products and their quantity details
     Each inventory has _One to One_ mapping with Product







