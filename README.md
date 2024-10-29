# DBA-Challenge-20240802
Teste Técnico Code Group

Clientes sem compras:
SELECT c.*
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;

Produtos não comprados:
SELECT p.*
FROM products p
LEFT JOIN order_items oi ON p.product_id = oi.product_id
WHERE oi.order_id IS NULL;

Produtos sem estoque:
SELECT p.*
FROM products p
JOIN stocks s ON p.product_id = s.product_id
WHERE s.quantity = 0;

Quantidade de vendas por marca e loja:
SELECT b.brand_name, s.store_name, SUM(oi.quantity) AS total_sales
FROM order_items oi
JOIN products p ON oi.product_id = p.product_id
JOIN brands b ON p.brand_id = b.brand_id
JOIN orders o ON oi.order_id = o.order_id
JOIN stores s ON o.store_id = s.store_id
GROUP BY b.brand_name, s.store_name;

Funcionários sem pedidos:
SELECT s.*
FROM staffs s
LEFT JOIN orders o ON s.staff_id = o.staff_id
WHERE o.order_id IS NULL;
