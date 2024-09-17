[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/r-tQZu0l)
# BBT3104-Lab1of6-DatabaseTransactions


| **Key**                                                               | Value                                                                                                                                                                              |
|---------------|---------------------------------------------------------|
<<<<<<< HEAD
| **Group Name**                                                               |C4|
=======
| **Group Name**                                                               | C4 |
>>>>>>> e45aa08888e8009f4da761af217e91013ef9bf84
| **Semester Duration**                                                 | 19<sup>th</sup> August - 25<sup>th</sup> November 2024                                                                                                                       |

## Flowchart
![image](https://github.com/user-attachments/assets/79756286-4649-4ef4-9f58-da89d17698f3)


## Pseudocode
Begin
START MySQL Docker container.
Connect to MySQL and SET autocommit = OFF.
SET transaction isolation level, serializable.
START transaction.
SET orderNumber = (select max(orderNumber) + 1 from orders).
INSERT INTO orders(orderNumbers, orderDate, requiredDate, shippedDate, status, customerNumber)
VALUES (orderNumber, CURRENRT_DATE + 3, CURRENT_DATE + 2, 'Inprocess', 145).
SAVEPOINT before_product_1.
INSERT INTO orderdetails(orderNumber, productCode, quantityOrdered, priceEach, orderLineNumber)
    VALUES (orderNumber, 'S18_1749', 2724, 136, 1)
SET quantityIn Stock = (quantityInStock FROM products WHERE productCode = 'S18_1749')
UPDATE products SET quantityInStock = quantityInStock - 2724 WHERE productCode = 'S18_1749'.
IF more_products_needed THEN.
SAVEPOINT before_product_2.
INSERT INTO orderdetails(orderNumber, productCode, quantityOrdered, priceEach, orderLineNumber)
    VALUES (orderNumber, 'S18_2248', 540, 55.09, 2).
SET quantityInStock = (SELECT quantityInStock FROM products WHERE productCode = 'S18_2248')
UPDATE products SET quantityInStock = quantityInStock - 540 WHERE productCode = 'S18_2248'
  END IF.
IF error_in_product_2 THEN
ROLLBACK TO SAVEPOINT before_product_2
  END IF.
IF more_products THEN
INSERT the remaining products and update stock
  END IF.
Commit transaction.
SELECT * FROM orderdetails WHERE orderNumber = orderNumber.
End.



## Support for the Sales Departments' Report
