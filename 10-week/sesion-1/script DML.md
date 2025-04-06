script DML

USE carrito_compra;

--Insertar personas (5)
INSERT INTO persona (nombre, apellido, fecha_nacimiento, correo, direccion, telefono) VALUES
('Ana', 'Pérez', '1990-05-10', 'ana.perez@mail.com', 'Cra 10 #20-30', '3012345678'),
('Carlos', 'Gómez', '1985-08-22', 'carlos.gomez@mail.com', 'Calle 5 #10-15', '3023456789'),
('Lucía', 'Ramírez', '1992-03-15', 'lucia.ramirez@mail.com', 'Av 3 #6-20', '3034567890'),
('Mateo', 'López', '1999-07-01', 'mateo.lopez@mail.com', 'Cl 8 #12-33', '3045678901'),
('Valentina', 'Torres', '1994-11-11', 'valentina.torres@mail.com', 'Transv 4 #44-21', '3056789012');

-- Insertar clientes (2)
INSERT INTO cliente (codigo, fecha_vinculacion, persona_id) VALUES
('CL001', '2022-01-10', 1),
('CL002', '2023-04-15', 2);

-- Insertar empleados (2)
INSERT INTO empleado (codigo, fecha_vinculacion, salario, tipo_contrato, persona_id) VALUES
('EMP001', '2021-02-20', 2500000, 'Término fijo', 3),
('EMP002', '2023-06-01', 3200000, 'Indefinido', 4);

-- Insertar categorías (3)
INSERT INTO categoria (nombre, descripcion) VALUES
('Tecnología', 'Productos tecnológicos'),
('Hogar', 'Productos para el hogar'),
('Alimentos', 'Productos alimenticios');

-- Insertar métodos de pago (3)
INSERT INTO metodo_pago (nombre, descripcion) VALUES
('Efectivo', 'Pago en efectivo'),
('Tarjeta', 'Pago con tarjeta de crédito'),
('Transferencia', 'Pago vía transferencia bancaria');

-- Insertar productos (6)
INSERT INTO producto (codigo, nombre, descripcion, categoria_id) VALUES
('P001', 'Laptop Lenovo', '16GB RAM, 512 SSD', 1),
('P002', 'Aspiradora', 'Aspiradora automática', 2),
('P003', 'Pan', 'Pan artesanal', 3),
('P004', 'Smartphone', 'Gama media', 1),
('P005', 'Silla Gamer', 'Ergonómica', 2),
('P006', 'Galletas', 'De chocolate', 3);

-- Insertar inventario (6)
INSERT INTO inventario (nombre, fecha, precio, stock, fecha_lote, fecha_vencimiento, producto_id) VALUES
('Inventario Laptop', '2024-01-01', 3200000, 10, '2023-12-20', '2026-12-20', 1),
('Inventario Aspiradora', '2024-01-01', 850000, 8, '2023-12-10', '2025-12-10', 2),
('Inventario Pan', '2024-01-01', 4500, 100, '2024-03-01', '2024-03-07', 3),
('Inventario Smartphone', '2024-02-01', 1200000, 15, '2024-01-15', '2026-01-15', 4),
('Inventario Silla', '2024-02-01', 700000, 5, '2024-01-10', '2025-01-10', 5),
('Inventario Galletas', '2024-02-01', 3500, 200, '2024-03-10', '2024-09-10', 6);

-- Insertar facturas (2)
INSERT INTO factura (codigo, fecha, valor_bruto, valor_descuento, valor_incremento, valor_neto, cliente_id, medio_pago_id) VALUES
('F001', '2024-03-10', 100000, 5000, 3000, 98000, 1, 1),
('F002', '2024-03-12', 75000, 0, 1500, 76500, 2, 2);

-- Insertar detalle_factura (4)
INSERT INTO detalle_factura (cantidad, porcentaje_descuento, porcentaje_incremento, subtotal, producto_id, factura_id) VALUES
(1, 5.00, 3.00, 98000, 1, 1),
(2, 0.00, 2.00, 71600, 2, 2),
(5, 0.00, 0.00, 22500, 3, 1),
(3, 0.00, 0.00, 10500, 6, 2);

-- UPDATE (5)
UPDATE persona SET direccion = 'Calle 9 #22-11' WHERE id = 1;
UPDATE producto SET nombre = 'Laptop Lenovo IdeaPad' WHERE id = 1;
UPDATE inventario SET stock = 12 WHERE id = 1;
UPDATE factura SET valor_descuento = 10000 WHERE id = 1;
UPDATE detalle_factura SET cantidad = 6 WHERE id = 3;

-- DELETE (5)
DELETE FROM metodo_pago WHERE id = 3;
DELETE FROM detalle_factura WHERE id = 4;
DELETE FROM inventario WHERE id = 6;
DELETE FROM cliente WHERE id = 2;
DELETE FROM empleado WHERE id = 1;

-- SELECT (5)
SELECT * FROM persona;
SELECT nombre, correo FROM persona WHERE nombre LIKE 'A%';
SELECT * FROM producto WHERE categoria_id = 1;
SELECT * FROM factura WHERE fecha BETWEEN '2024-01-01' AND '2024-12-31';
SELECT producto.nombre, inventario.stock
FROM inventario
JOIN producto ON inventario.producto_id = producto.id;
