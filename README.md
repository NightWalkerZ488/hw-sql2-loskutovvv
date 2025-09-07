<img width="405" height="251" alt="изображение" src="https://github.com/user-attachments/assets/fb4cf61f-360a-4f35-b06b-20330e289c6e" /># Домашнее задание к занятию "`SQL. Часть 2`" - `Лоскутов В.В.`

---
### Задание 1

Одним запросом получите информацию о магазине, в котором обслуживается более 300 покупателей, и выведите в результат следующую информацию: 
- фамилия и имя сотрудника из этого магазина;
- город нахождения магазина;
- количество пользователей, закреплённых в этом магазине.

## Ответ:

Запрос будет выглядеть следующим образом:
```
SELECT 
    s.first_name AS staff_first_name,
    s.last_name AS staff_last_name,
    c.city AS store_city,
    COUNT(cust.customer_id) AS customer_count
FROM store st
JOIN staff s ON st.manager_staff_id = s.staff_id
JOIN address a ON st.address_id = a.address_id
JOIN city c ON a.city_id = c.city_id
JOIN customer cust ON st.store_id = cust.store_id
GROUP BY st.store_id, s.first_name, s.last_name, c.city
HAVING COUNT(cust.customer_id) > 300;
```

Результат выполнения такого запроса:
!(shop)[https://github.com/NightWalkerZ488/hw-sql2-loskutovvv/blob/main/w1.PNG]

### Задание 2

Получите количество фильмов, продолжительность которых больше средней продолжительности всех фильмов.

### Ответ:

Запрос будет такой:

```
SELECT COUNT(*) AS films_above_avg_length
FROM film
WHERE length > (
    SELECT AVG(length)
    FROM film
);

```

Результат выполнения:

!(shop)[https://github.com/NightWalkerZ488/hw-sql2-loskutovvv/blob/main/w2.PNG]


### Задание 3

Получите информацию, за какой месяц была получена наибольшая сумма платежей, и добавьте информацию по количеству аренд за этот месяц.

Ответ:

Текст запроса:

```

```
