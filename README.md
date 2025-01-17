# patika-SQL
Patika SQL eğitiminde verilen ödevleri içermektedir.

## ÖDEV1
### 1-film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
SELECT title, description FROM film;
### 2-film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
SELECT title, length FROM film
WHERE  length > 60 AND length < 75;
### 3-film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
SELECT * FROM film
WHERE rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99);'''
### 4-customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
SELECT first_name, last_name FROM customer
WHERE first_name = 'Mary';
### 5-film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
SELECT * FROM film
WHERE length < 50 AND NOT(rental_rate = 2.99 OR rental_rate = 2.99 );





## ÖDEV2
### 1-film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız
  SELECT * FROM film
  WHERE replacement_cost BETWEEN 12.99 AND 16.99;  
### 2-actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız.
  SELECT first_name, last_name FROM actor
  WHERE first_name IN ('Penelope', 'Nick', 'Ed');
### 3-film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız.
  SELECT * FROM film
  WHERE rental_rate IN (0.99, 2.99, 4.99) AND replacement_cost IN (12.99, 15.99, 28.99);

  

## ÖDEV3
### 1-country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
  SELECT * FROM country
  WHERE country LIKE 'A%a';
### 2-country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
  SELECT * FROM country
  WHERE country LIKE '%_____n';
### 3-film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
  SELECT * FROM film
  WHERE title ILIKE '%t%t%t%t%';
### 4-film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
  SELECT * FROM film
  WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99;




  ## ÖDEV4
  ### 1-film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
    SELECT DISTINCT replacement_cost FROM film;
  ### 2-film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
    SELECT COUNT(DISTINCT replacement_cost) FROM film;
  ### 3-film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
    SELECT COUNT(*) FROM film
  WHERE title LIKE 'T%' AND rating = 'G';
  ### 4-country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
    SELECT COUNT(*) FROM country
  WHERE country LIKE '_____';
  ### 5-city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?
    SELECT COUNT(*) from city
  WHERE city ILIKE '%r';




   ## ÖDEV5
   ### 1-film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
     SELECT * FROM film
  WHERE title LIKE '%n'
  ORDER BY length DESC
  LIMIT 5;
   ### 2-film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.
     SELECT film_id, title, length FROM film
  WHERE title LIKE '%n'
  ORDER BY length ASC
  OFFSET 5
  LIMIT 5;
   ### 3-customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
     SELECT * FROM customer
  WHERE store_id = 1
  ORDER BY last_name DESC
  LIMIT 4;



  
## ÖDEV6
  ### 1-film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
    SELECT ROUND(AVG(rental_rate),4) AS avarage_rental_rate FROM film;
  ### 2-film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?
    SELECT COUNT(*) AS start_with_c FROM film
  WHERE title LIKE 'C%';
  ### 3-film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
    SELECT MAX(length) FROM film
  WHERE rental_rate = 0.99;
  ### 4-film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
    SELECT COUNT(DISTINCT(replacement_cost)) FROM film
  WHERE length > 150




  ## ÖDEV7
   ### 1-film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
     SELECT rating, COUNT(*) FROM film
  GROUP BY rating;
   ### 2-film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
     SELECT replacement_cost, COUNT(*) FROM film
  GROUP BY replacement_cost
  HAVING COUNT(*) > 50;
   ### 3-customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
     SELECT store_id, COUNT(*) FROM customer
  GROUP BY store_id
   ### 4-city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.
  SELECT country_id, COUNT(country_id) as adet FROM city  
  GROUP BY country_id
  ORDER BY COUNT(country_id) DESC
  FETCH FIRST 1 ROW ONLY;




   ## ÖDEV8
   ### 1-test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
     CREATE TABLE employee (
    id SERIAL PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    birthday DATE DEFAULT CURRENT_DATE,
    email VARCHAR(100);
   ### 2-Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
   insert into employee (name, birthday, email) values ('Maurits', '1994-02-27', 'mhartwell0@cdc.gov');
insert into employee (name, birthday, email) values ('Taite', '1963-06-04', 'tpipkin1@ebay.com');
...
insert into employee (name, birthday, email) values ('Catlin', null, 'cwythill1d@samsung.com');
   ### 3-Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
   UPDATE employee
SET name = 'updated',
    birthday = '1555-05-15',
    email = 'updated@email.com
WHERE id = 1;

UPDATE employee
SET name = 'updated1',
    birthday = '1555-05-15',
    email = 'updated1@email.com
WHERE name LIKE '%a';

UPDATE employee
SET name = 'updated2',
    birthday = '1555-05-15',
    email = 'updated2@email.com
WHERE email IS NULL;

UPDATE employee
SET name = 'updated3',
    birthday = '1555-05-15',
    email = 'updated3@email.com
WHERE id > 30;

UPDATE employee
SET name = 'updated4',
    birthday = '1555-05-15',
    email = 'updated4@email.com
WHERE name ILIKE '%__a%' AND email IS NOT NULL;
   ### 4-Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
   DELETE FROM employee
WHERE id = 1;

DELETE FROM employee
WHERE name LIKE '%a';

DELETE FROM employee
WHERE email IS NULL;

DELETE FROM employee
WHERE id > 30;

DELETE FROM employee
WHERE name ILIKE '%__a%' AND email IS NOT NULL;




 ## ÖDEV9
 ### 1-city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
   SELECT city.city, country.country FROM city
  INNER JOIN country
  ON city.country_id = country.country_id;
 ### 2-customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız
 SELECT payment.payment_id, customer.first_name, customer.last_name FROM payment
INNER JOIN customer
ON payment.customer_id = customer.customer_id;
 ### 3-customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
 SELECT rental.rental_id, customer.first_name, customer.last_name FROM rental
INNER JOIN customer
ON rental.customer_id = customer.customer_id;



## ÖDEV10
### 1-city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
SELECT city, country FROM city
LEFT JOIN country
ON city.country_id = country.country_id;
### 2-customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
SELECT first_name, last_name, payment_id FROM customer
RIGHT JOIN payment
ON payment.customer_id = customer.customer_id;
### 3-customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.
SELECT rental_id, first_name, last_name FROM rental
FULL JOIN customer
ON rental.customer_id = customer.customer_id;



## ÖDEV11
### 1 - actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım. 2 - actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım. 3 - actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım. 4 - İlk 3 sorguyu tekrar eden veriler için de yapalım.

  -- 1
  (SELECT first_name FROM actor)
  UNION
  (SELECT first_name FROM customer);

  --2
  (SELECT first_name FROM actor)
  INTERSECT 
  (SELECT first_name FROM customer);
  
  --3
  (SELECT first_name FROM actor)
  EXCEPT
  (SELECT first_name FROM customer);

  --4
  (SELECT first_name FROM actor)
  UNION ALL
  (SELECT first_name FROM customer);

  (SELECT first_name FROM actor)
  INTERSECT ALL
  (SELECT first_name FROM customer);

  (SELECT first_name FROM actor)
  EXCEPT ALL
  (SELECT first_name FROM customer);




## ÖDEV12
### 1 - film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır? 2 - film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır? 3 - film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız. 4 - payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
--1
SELECT COUNT(*) FROM film
WHERE length > (
	SELECT AVG(length) FROM film
);

--2
SELECT COUNT(*) FROM film
WHERE rental_rate = (
	SELECT MAX(rental_rate) FROM film
);

--3
SELECT * FROM film
WHERE rental_rate = ALL 
(
	SELECT MIN(rental_rate) FROM film
)
AND replacement_cost = ALL 
(
	SELECT MIN(replacement_cost) FROM film
); 

--4
SELECT payment.customer_id, customer.first_name, customer.last_name, count(payment.customer_id)  
FROM payment
INNER JOIN customer
ON customer.customer_id = payment.customer_id
GROUP BY payment.customer_id, customer.first_name, customer.last_name
ORDER BY COUNT(payment.customer_id) DESC;

 

   
  





