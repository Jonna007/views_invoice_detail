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

![Captura de pantalla 2024-06-24 232928](https://github.com/Jonna007/views_invoice_detail/assets/146044709/2979d550-890a-43bd-8869-f51ba658b136)


### Ejemplo de Uso:
```sql
SELECT * FROM invoice_view;
```
![Captura de pantalla 2024-06-24 235930](https://github.com/Jonna007/views_invoice_detail/assets/146044709/95faa36d-2585-4bb6-a746-a7d344c3e31b)


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
![Captura de pantalla 2024-06-24 233029](https://github.com/Jonna007/views_invoice_detail/assets/146044709/56c5befa-edc8-4918-a60b-d7b0b15b2560)

### Ejemplo de Uso:
```sql
SELECT * FROM detail_view;
```
![Captura de pantalla 2024-06-25 000010](https://github.com/Jonna007/views_invoice_detail/assets/146044709/b5c7117a-e838-497c-b92a-97c1214b0f0a)


