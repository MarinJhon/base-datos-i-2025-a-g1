SCRIPT dml join 

-- 1 Listar nombres de clientes con su correo
SELECT c.codigo AS cliente_codigo, p.nombre, p.correo
FROM cliente c
INNER JOIN persona p ON c.persona_id = p.id;

-- 2 Listar empleados con tipo de contrato y salario
SELECT e.codigo AS empleado_codigo, p.nombre, e.tipo_contrato, e.salario
FROM empleado e
INNER JOIN persona p ON e.persona_id = p.id;

-- 3 Mostrar productos junto con el nombre de su categoría
SELECT pr.nombre AS producto, c.nombre AS categoria
FROM producto pr
INNER JOIN categoria c ON pr.categoria_id = c.id;

-- 4. Mostrar detalles de factura con nombre de producto y subtotal
SELECT df.id, p.nombre AS producto, df.cantidad, df.subtotal
FROM detalle_factura df
INNER JOIN producto p ON df.producto_id = p.id;

-- 5 Facturas con el nombre del cliente y el valor neto
SELECT f.codigo AS factura, p.nombre AS cliente, f.valor_neto
FROM factura f
INNER JOIN cliente c ON f.cliente_id = c.id
INNER JOIN persona p ON c.persona_id = p.id;

-- 6 Productos con su stock actual
SELECT p.nombre AS producto, i.stock
FROM producto p
INNER JOIN inventario i ON p.id = i.producto_id;

-- 7 Factura con su método de pago
SELECT f.codigo AS factura, m.nombre AS metodo_pago
FROM factura f
INNER JOIN metodo_pago m ON f.medio_pago_id = m.id;

-- 8 Nombre del producto vendido y código de factura
SELECT p.nombre AS producto, f.codigo AS factura
FROM detalle_factura df
INNER JOIN producto p ON df.producto_id = p.id
INNER JOIN factura f ON df.factura_id = f.id;

-- 9 Clientes con las facturas que han generado y su total
SELECT p.nombre AS cliente, f.codigo AS factura, f.valor_neto
FROM cliente c
INNER JOIN persona p ON c.persona_id = p.id
INNER JOIN factura f ON f.cliente_id = c.id;

-- 10 Mostrar inventario con precio, producto y categoría
SELECT i.nombre AS inventario, i.precio, p.nombre AS producto, c.nombre AS categoria
FROM inventario i
INNER JOIN producto p ON i.producto_id = p.id
INNER JOIN categoria c ON p.categoria_id = c.id;
