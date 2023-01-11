# Домашнее задание к занятию "`12.4. «Реляционные базы данных: SQL. Часть 2»`" - `Жевлаков Анатолий`


### Задание 1

`Одним запросом получите информацию о магазине, в котором обслуживается более 300 покупателей, и выведите в результат следующую информацию:

фамилия и имя сотрудника из этого магазина;
город нахождения магазина;
количество пользователей, закреплённых в этом магазине.`


```
SELECT CONCAT_WS(' ', s2.first_name, s2.last_name), s.store_id, c.city, COUNT(c2.customer_id) FROM store s 
JOIN (staff s2, address a, store s3, city c, customer c2)
ON (s2.staff_id=s.manager_staff_id AND s.address_id=a.address_id AND s.store_id=s3.store_id AND c.city_id=a.city_id AND c2.store_id=s3.store_id)
GROUP BY s.store_id
HAVING COUNT(c2.customer_id) >= 300;

```

### Задание 2

`Получите количество фильмов, продолжительность которых больше средней продолжительности всех фильмов.`

```
SELECT count(film_id)
FROM film f 
WHERE `length` > (SELECT AVG(`length`) from film);

```

### Задание 3

`Получите информацию, за какой месяц была получена наибольшая сумма платежей, и добавьте информацию по количеству аренд за этот месяц.`

```
SELECT DATE_FORMAT(payment_date, "%Y-%m") as дата, SUM(amount) as сумма, COUNT(rental_id) as количество_аренд FROM payment p 
GROUP BY DATE_FORMAT(payment_date, "%Y-%m")
ORDER BY сумма DESC
LIMIT 1;

```


