
this solutiom contains 2 independent microservices:
 - ProductService (handles product management)
 - OrderService (handles order management and communicate with ProductService for product validation and stock checks)




 what we use:
 - SQL server instance
 - POSTMAN for testing APIs
	
	


Configuration:
1. Update connection strings in:

- `ProductService/appsettings.json`
- `OrderService/appsettings.json`

2. Update HTTP client base URLs in OrderService if needed to point to the running ProductService API (ex. https://localhost:7274)

Running the services
Run the ProductService project first
Run the OrderService project next


API Endpoints:
ProductService:
GET /api/product — Get all products

GET /api/product/{id} — Get product by id

POST /api/product — Add new product

PUT /api/product/{id} — Update product

DELETE /api/product/{id} — Delete product

GET /api/product/{id}/instock — Check if product is in stock


OrderService:
GET /api/order — Get all orders

GET /api/order/{id} — Get order by id

POST /api/order — Create order (validates products and stock via ProductService)

PUT /api/order/{id} — Update order

DELETE /api/order/{id} — Delete order


Notes
Each microservice uses its own database and EF Core migrations.
OrderService communicates with ProductService via HTTP client to ensure product validity and stock availability before placing or updating orders.

