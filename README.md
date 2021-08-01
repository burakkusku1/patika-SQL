# patika-SQL

[Ödev 1 ](#ödev-1)<br>
[Ödev 2 ](#ödev-2)<br>
[Ödev 3 ](#ödev-3) <br>
[Ödev 4 ](#ödev-4)<br>
[Ödev 5 ](#ödev-5)<br>
[Ödev 6 ](#ödev-6)<br>
[Ödev 7 ](#ödev-7)<br>
[Ödev 8 ](#ödev-8)



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

## Ödev 5

**film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.**
```SQL
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5;

```
**film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.**
```SQL
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length 
OFFSET 5
LIMIT 5;
```

**customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.**
```SQL
SELECT * FROM customer
WHERE store_id =1
ORDER BY last_name DESC
LIMIT 4;
```

## Ödev 6

**film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?**
```SQL
SELECT ROUND(AVG(rental_rate),3) FROM film;
--2.980
```

**film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?**
```SQL
SELECT COUNT(*) FROM film
WHERE title LIKE 'C%';
-- Cevap : 92 

```
**film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?**
```sql
SELECT MAX(length) FROM film
WHERE rental_rate= 0.99;
--184
```
**film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?**
```SQL
SELECT COUNT(DISTINCT(replacement_cost)) from film 
WHERE length >150;
-- 21
```

## Ödev 7

**film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.**

```SQL
SELECT rating FROM film
GROUP BY rating;

```

**film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.**

```sql
SELECT replacement_cost,COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*)>50;
```

**3. customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir**

```SQL
SELECT store_id,COUNT(customer_id) FROM customer
GROUP BY store_id;

```

**4. city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.**

```SQL
SELECT country_id,COUNT(city) FROM city
GROUP BY country_id
ORDER BY COUNT(city) DESC
LIMIT 1;
--country id:44 , count:60 
```

## Ödev 8
**test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.**

```sql
CREATE TABLE employee(
	
	id SERIAL PRIMARY KEY,
	name VARCHAR(50),
	birthday DATE,
	email VARCHAR(50)
)
```

***Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.***

```sql
insert into employee (name, birthday, email) values ('Gilbert Readhead', '1966-04-25', 'greadhead0@clickbank.net');
insert into employee (name, birthday, email) values ('Caryl Ogilby', '1989-11-15', 'cogilby1@fema.gov');
insert into employee (name, birthday, email) values ('Anton Bourchier', '1983-01-29', 'abourchier2@cafepress.com');
insert into employee (name, birthday, email) values ('Mace Yearnsley', '1922-10-03', 'myearnsley3@wunderground.com');
insert into employee (name, birthday, email) values ('Roddy Anthony', '1921-01-03', 'ranthony4@marketwatch.com');
insert into employee (name, birthday, email) values ('Immanuel Iglesias', '1939-03-03', 'iiglesias5@freewebs.com');
insert into employee (name, birthday, email) values ('Simone Armfield', '1969-02-21', 'sarmfield6@diigo.com');
insert into employee (name, birthday, email) values ('Em Womack', '2020-11-21', 'ewomack7@phpbb.com');
insert into employee (name, birthday, email) values ('Nicolle Parsand', '1961-02-24', 'nparsand8@freewebs.com');
insert into employee (name, birthday, email) values ('Haydon Turford', '1924-06-21', 'hturford9@lulu.com');
insert into employee (name, birthday, email) values ('Roderic Androsik', '1929-12-05', 'randrosika@unc.edu');
insert into employee (name, birthday, email) values ('Marlena Stener', '1913-12-03', 'mstenerb@indiatimes.com');
insert into employee (name, birthday, email) values ('Dredi Lucio', '1970-04-07', 'dlucioc@cbc.ca');
insert into employee (name, birthday, email) values ('Adrian Ainger', '1958-06-05', 'aaingerd@altervista.org');
insert into employee (name, birthday, email) values ('Chandler Behnecke', '1935-10-11', 'cbehneckee@trellian.com');
insert into employee (name, birthday, email) values ('Ame Jagson', '1973-08-23', 'ajagsonf@ebay.com');
insert into employee (name, birthday, email) values ('Ronnica Artinstall', '1984-04-12', 'rartinstallg@dropbox.com');
insert into employee (name, birthday, email) values ('Celinka Burgh', '1959-10-18', 'cburghh@histats.com');
insert into employee (name, birthday, email) values ('Arlana Ilchenko', '1939-09-26', 'ailchenkoi@squarespace.com');
insert into employee (name, birthday, email) values ('Rockwell Furlow', '1963-03-23', 'rfurlowj@ow.ly');
insert into employee (name, birthday, email) values ('Aurilia La Padula', '1943-07-04', 'alak@storify.com');
insert into employee (name, birthday, email) values ('Darrelle Braiden', '1978-11-09', 'dbraidenl@free.fr');
insert into employee (name, birthday, email) values ('Brynn Trengove', '2013-09-16', 'btrengovem@rediff.com');
insert into employee (name, birthday, email) values ('Celka Larver', '1955-10-28', 'clarvern@flickr.com');
insert into employee (name, birthday, email) values ('Lorna Sellar', '2012-03-02', 'lsellaro@constantcontact.com');
insert into employee (name, birthday, email) values ('Diane-marie Barbara', '1911-03-13', 'dbarbarap@parallels.com');
insert into employee (name, birthday, email) values ('Alvinia Flather', '1957-12-17', 'aflatherq@odnoklassniki.ru');
insert into employee (name, birthday, email) values ('Dre Cockings', '1964-06-30', 'dcockingsr@mit.edu');
insert into employee (name, birthday, email) values ('Davida Ginner', '1972-12-26', 'dginners@marriott.com');
insert into employee (name, birthday, email) values ('Maurita Bouchier', '1913-11-03', 'mbouchiert@princeton.edu');
insert into employee (name, birthday, email) values ('Charline McFadyen', '1976-05-17', 'cmcfadyenu@indiatimes.com');
insert into employee (name, birthday, email) values ('Suzanna Dunbleton', '2016-07-15', 'sdunbletonv@forbes.com');
insert into employee (name, birthday, email) values ('Maurizio Polet', '1994-12-28', 'mpoletw@amazon.com');
insert into employee (name, birthday, email) values ('Ynes Maffioletti', '1930-04-11', 'ymaffiolettix@wix.com');
insert into employee (name, birthday, email) values ('Jay Rawlence', '1956-09-06', 'jrawlencey@discovery.com');
insert into employee (name, birthday, email) values ('Marsiella Spight', '1958-05-29', 'mspightz@rakuten.co.jp');
insert into employee (name, birthday, email) values ('Desiree Healey', '2018-04-24', 'dhealey10@biblegateway.com');
insert into employee (name, birthday, email) values ('Brad Pattrick', '1920-04-06', 'bpattrick11@gov.uk');
insert into employee (name, birthday, email) values ('Caren Stibbs', '1964-06-10', 'cstibbs12@time.com');
insert into employee (name, birthday, email) values ('Regan Walsom', '1998-06-29', 'rwalsom13@people.com.cn');
insert into employee (name, birthday, email) values ('Lanna O'' Flaherty', '1991-06-02', 'lo14@nbcnews.com');
insert into employee (name, birthday, email) values ('Philomena Flippelli', '1999-01-11', 'pflippelli15@comcast.net');
insert into employee (name, birthday, email) values ('Vanny De Paoli', '2006-09-30', 'vde16@dyndns.org');
insert into employee (name, birthday, email) values ('Sindee Nisuis', '1952-12-03', 'snisuis17@goo.ne.jp');
insert into employee (name, birthday, email) values ('Julee Caulliere', '2018-03-09', 'jcaulliere18@cbslocal.com');
insert into employee (name, birthday, email) values ('Miguelita Paolino', '2014-03-19', 'mpaolino19@networkadvertising.org');
insert into employee (name, birthday, email) values ('Clarke Cotton', '1914-08-21', 'ccotton1a@mozilla.org');
insert into employee (name, birthday, email) values ('Merrill McMechan', '1915-02-12', 'mmcmechan1b@state.tx.us');
insert into employee (name, birthday, email) values ('Brander Rattry', '2007-07-08', 'brattry1c@craigslist.org');
insert into employee (name, birthday, email) values ('Donni Scholte', '1912-08-08', 'dscholte1d@de.vu');

```

**Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.**

```SQL 
   UPDATE  employee  SET name ='Burak Küskü' WHERE id=1;
   UPDATE  employee SET birthday ='22-12-1900' WHERE id=2;
   UPDATE  employee SET email ='bilmiyorum@fikrimyok.com' WHERE id=3;
   UPDATE  employee SET email ='fikri@fikrimyok.com', name='Fikri Gül' WHERE id=4;
   UPDATE  employee SET email ='Can@ker.com',name='Kerim Can', birthday='01-01-1950' WHERE id=49;
   
```
**Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.**
```sql
DELETE FROM  employee WHERE id=2;
DELETE FROM  employee WHERE name ='Burak Küskü'; 
DELETE FROM  employee WHERE birthday ='1950-01-01'; 
DELETE FROM  employee WHERE email ='sarmfield6@diigo.com'; 
DELETE FROM  employee WHERE name ='Roddy Anthony'; 


```


