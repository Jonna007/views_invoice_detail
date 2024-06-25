# Proyecto Invoice - Views Creation

## 1. `invoice_view`

### Descripción:
Esta vista muestra los detalles de las facturas incluyendo el código, fecha de creación, total y el nombre completo del cliente.

### SQL para crear la vista:
```sql
CREATE VIEW invoice_view AS
SELECT 
    i.id AS code,
    i.create_at,
    i.total,
    c.fullname
FROM invoice i
JOIN client c ON i.client_id = c.id;
```
![Creacion invoice_view]("C:\Users\windows\OneDrive\Imágenes\Screenshots\Captura de pantalla 2024-06-24 233029.png")


### Ejemplo de Uso:
```sql
SELECT * FROM invoice_view;
```


## 2. `detail_view`
### Descripción:
Esta vista muestra los detalles de los productos en las facturas, incluyendo la cantidad, descripción del producto, precio y subtotal calculado.

### SQL para crear la vista:
```sql
CREATE VIEW detail_view AS
SELECT 
    d.id,
    d.quantity,
    p.description,
    d.price,
    (d.quantity * d.price) AS subtotal
FROM detail d
JOIN product p ON d.product_id = p.id;
```

### Ejemplo de Uso:
```sql
SELECT * FROM detail_view;
```


