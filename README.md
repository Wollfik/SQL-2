# Домашнее задание к занятию "`Реляционные базы данных: SQL. Часть 1`" - `Жевлаков Анатолий`


### Задание 1

`Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a” и не содержат пробелов.`


```

select distinct address
from address
where address like '% K%a %';

```

### Задание 2

`Получите из таблицы платежей за прокат фильмов информацию по платежам, которые выполнялись в промежуток с 15 июня 2005 года по 18 июня 2005 года включительно и стоимость которых превышает 10.00.`

```

select payment_id, amount, payment_date
from payment
where amount > 10 and payment_date between '2005-06-15' and '2005-06-18';

```

### Задание 3

`Получите последние пять аренд фильмов.`

```

SELECT rental_id, rental_date
from rental
ORDER BY rental_date DESC
LIMIT 5;

```


### Задание 4

`Одним запросом получите активных покупателей, имена которых Kelly или Willie.

Сформируйте вывод в результат таким образом:

все буквы в фамилии и имени из верхнего регистра переведите в нижний регистр,
замените буквы 'll' в именах на 'pp'.`


```
select customer_id, first_name, last_name
from customer
where first_name = 'Kelly' or first_name = 'Willie';

# В нижний регистр
select customer_id, lower (first_name), lower (last_name)
from customer
where first_name = 'Kelly' or first_name = 'Willie';

# Замена букв LL на PP
select customer_id, lower (first_name), lower (last_name), replace (first_name, 'LL', 'PP')
from customer
where first_name = 'Kelly' or first_name = 'Willie';
```

