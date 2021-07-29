# patika-SQL

[Ödev 1 ](#ödev-1)<br>
[Ödev 2 ](#ödev-2)<br>
[Ödev 3 ](#ödev-3) <br>
[Ödev 4 ](#ödev-4)






## Ödev 1 
**film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.**

```SQL
SELECT title,description FROM film;

```

**film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.**
```SQL 
SELECT * FROM film
WHERE length>60 and length<75;

```
**film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.**

```SQL
SELECT * FROM film
WHERE rental_rate=0.99 AND replacement_cost=12.99 OR replacement_cost=28.99;

```
**customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?**

```SQL  
SELECT first_name,last_name FROM customer
WHERE first_name ='Mary'
--last_name değeri Smith olarak çıkmaktadır.

```
**film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.**
```sql
SELECT * FROM film
WHERE length  <= 50 AND NOT( rental_rate= 2.99 OR rental_rate= 4.99)

```

## Ödev 2

**film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)**
```SQL
SELECT * FROM film
WHERE  replacement_cost BETWEEN 12.99 AND 16.98;
--Not , 16.99 küçük olma koşulu olduğu için 16.98 değerini girdim 
```
**.actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)**
```SQL
SELECT first_name,last_name FROM actor
WHERE first_name IN('Penelope','Nick','Ed');
```

**film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)**

```SQL
SELECT * FROM film
WHERE rental_rate IN(0.99, 2.99, 4.99) AND replacement_cost IN(12.99, 15.99, 28.99)
```

## Ödev 3

**country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.**

```SQL
SELECT * FROM country
WHERE country LIKE 'A%a';

```
**country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.**
```SQL
SELECT * FROM country
WHERE country LIKE '______%n';

```
**film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.**

```SQL
SELECT title FROM film
WHERE title ILIKE '%t%t%t%t%';
```

**film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.**
```SQL 
SELECT * FROM film
WHERE title LIKE 'C%' AND length>90 AND rental_rate=2.99;

```

## Ödev 4
**film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.**
```SQL
SELECT  DISTINCT replacement_cost  FROM film; 

```

**film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?**
```SQL
SELECT  COUNT(DISTINCT replacement_cost)  FROM film; 
-- cevap: 21 

```
**film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?**
```SQL
SELECT COUNT(*)  FROM film
WHERE title LIKE 'T%' AND rating ='G';
--Cevap: 9
```

**country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?**
```SQL
SELECT COUNT(country)  FROM country
WHERE country LIKE '_____' ;
--Cevap: 9
```

**city tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?**
```SQL
SELECT COUNT(city)  FROM city
WHERE city LIKE '%R' or city LIKE '%r' ;
--Cevap: 33 
```

