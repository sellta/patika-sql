# patika-sql

Sql eğitim soruları
---

## <p> Ödev 1 </p> 
#### 1- Film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
~~~sql
SELECT title, description FROM film;
~~~  
  
#### 2- Film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
~~~sql
SELECT * FROM film
WHERE length > 60 AND length < 75;
~~~

#### 3- Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
~~~sql
SELECT * FROM film
WHERE rental_rate = 0.99 
AND (replacement_cost = 12.99 OR replacement_cost = 28.99);
~~~

#### 4- Customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
~~~sql
SELECT * FROM film
WHERE first_name = 'Mary';

CEVAP : Smith
~~~

#### 5- Film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
~~~sql
SELECT * FROM film
WHERE NOT (rental_rate = 4.99 OR rental_rate = 2.99) 
AND length < 51;
~~~

---

## <p> Ödev 2 </p> 
#### 1- film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
~~~sql
SELECT title,replacement_cost FROM film
WHERE replacement_cost
BETWEEN 12.99 AND 16.99;
~~~


#### 2- .actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
~~~sql
SELECT * FROM actor
WHERE first_name 
IN ('Penelope', 'Nick', 'Ed');
~~~

#### 3- film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 					15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
~~~sql
SELECT * FROM film
WHERE (rental_rate IN (0.99, 2.99, 4.99)) 
AND (replacement_cost IN (12.99, 15.99,28.99));
~~~
---
## <p> Ödev 3 </p> 
#### 1- country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
~~~sql
SELECT * FROM country
WHERE country 
LIKE 'A%a';
~~~
#### 2- country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
~~~sql
SELECT * FROM country
WHERE country 
LIKE '_____%n';
~~~
#### 3- film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
~~~sql
SELECT title FROM film
WHERE title 
ILIKE '%t%t%t%t%';

~~~
#### 4- film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
~~~sql
SELECT * FROM film
WHERE (title LIKE 'C%') AND (length > 90) AND (rental_rate = 2.99);
~~~
---

## <p> Ödev 4 </p> 
#### 1- film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
~~~sql
SELECT DISTINCT replacement_cost FROM film;
~~~  
  
#### 2- film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
~~~sql
SELECT COUNT (DISTINCT replacement_cost) FROM film;
~~~

#### 3- film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
~~~sql
SELECT COUNT (*) FROM film
WHERE (title LIKE 'T%') AND (rating = 'G');
~~~

#### 4- country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
~~~sql
SELECT COUNT(*) FROM country
WHERE country LIKE '_____';
~~~

#### 5- city tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?
~~~sql
SELECT COUNT(*) FROM city
WHERE city ILIKE '%r';
~~~

---
## <p> Ödev 5 </p> 
#### 1- film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
~~~sql
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5;
~~~
#### 2- film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.
~~~sql
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length ASC
OFFSET 5
LIMIT 5;
~~~
#### 3- customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
~~~sql
SELECT * FROM customer
WHERE store_id = 1 
ORDER BY  last_name DESC
LIMIT 4;
~~~
---

## <p> Ödev 6 </p> 
#### 1- film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
~~~sql
SELECT ROUND(AVG(rental_rate), 2) FROM film;
~~~  
  
#### 2- film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?
~~~sql
SELECT COUNT(title) FROM film
WHERE title ILIKE 'c%';
~~~

#### 3- film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
~~~sql
SELECT MAX(length) FROM film
WHERE rental_rate = 0.99;
~~~

#### 4- film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
~~~sql
SELECT COUNT(DISTINCT replacement_cost) FROM film
WHERE length > 150;
~~~

---
## <p> Ödev 7 </p> 
#### 1- film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
~~~sql
SELECT rating, count(*) FROM film
GROUP BY rating;
~~~  
  
#### 2- film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
~~~sql
SELECT replacement_cost, COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*) > 50;
~~~

#### 3- customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayıları nelerdir?
~~~sql
SELECT store_id, COUNT(*) FROM customer
GROUP BY store_id;
~~~

#### 4- city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.
~~~sql
SELECT country_id, COUNT(*) FROM city
GROUP BY country_id
ORDER BY COUNT(*) DESC
LIMIT 1;
~~~
---
## <p> Ödev 8 </p> 
#### 1- test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
~~~sql
CREATE TABLE employee (
	id INTEGER,
	name VARCHAR(50),
	birthday DATE,
	email VARCHAR(100)
);
~~~  
  
#### 2- Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
~~~sql
insert into employee (id, name, birthday, email) values (1, 'Sydelle Shallo', '1998-11-30', 'sshallo0@house.gov');
insert into employee (id, name, birthday, email) values (2, 'Nickola Conkling', '2002-05-26', 'nconkling1@instagram.com');
insert into employee (id, name, birthday, email) values (3, 'Glenda Giorgietto', '1991-02-15', 'ggiorgietto2@shop-pro.jp');
insert into employee (id, name, birthday, email) values (4, 'Giulia Melladew', '1997-02-23', 'gmelladew3@statcounter.com');
insert into employee (id, name, birthday, email) values (5, 'Haley Spaducci', '1998-12-03', 'hspaducci4@wufoo.com');
insert into employee (id, name, birthday, email) values (6, 'Clair Luck', '1998-03-03', 'cluck5@is.gd');
insert into employee (id, name, birthday, email) values (7, 'Bard Jerdein', '1999-05-10', 'bjerdein6@state.tx.us');
insert into employee (id, name, birthday, email) values (8, 'James Hairsine', '2005-01-21', 'jhairsine7@arstechnica.com');
insert into employee (id, name, birthday, email) values (9, 'Humfrey Walkey', '1997-11-11', 'hwalkey8@vistaprint.com');
insert into employee (id, name, birthday, email) values (10, 'Redd Zywicki', '1993-03-29', 'rzywicki9@newsvine.com');
insert into employee (id, name, birthday, email) values (11, 'Inglis Stoke', '1991-02-06', 'istokea@bravesites.com');
insert into employee (id, name, birthday, email) values (12, 'Bo Killingsworth', '2002-02-08', 'bkillingsworthb@imageshack.us');
insert into employee (id, name, birthday, email) values (13, 'Ferdinanda Joutapavicius', '1994-12-21', 'fjoutapaviciusc@buzzfeed.com');
insert into employee (id, name, birthday, email) values (14, 'Vikki Gowman', '1995-07-17', 'vgowmand@utexas.edu');
insert into employee (id, name, birthday, email) values (15, 'Frazier MacGrath', '1998-04-09', 'fmacgrathe@seattletimes.com');
insert into employee (id, name, birthday, email) values (16, 'Cristine Hooks', '1991-12-27', 'chooksf@discovery.com');
insert into employee (id, name, birthday, email) values (17, 'Bary Blackney', '1991-01-02', 'bblackneyg@amazon.de');
insert into employee (id, name, birthday, email) values (18, 'Alley Khadir', '1998-01-10', 'akhadirh@altervista.org');
insert into employee (id, name, birthday, email) values (19, 'Cheslie Corington', '1995-08-18', 'ccoringtoni@ted.com');
insert into employee (id, name, birthday, email) values (20, 'Marga Britner', '1999-10-27', 'mbritnerj@uol.com.br');
insert into employee (id, name, birthday, email) values (21, 'Angeline Pablo', '1992-02-09', 'apablok@nydailynews.com');
insert into employee (id, name, birthday, email) values (22, 'Shaun Workes', '1997-05-18', 'sworkesl@webeden.co.uk');
insert into employee (id, name, birthday, email) values (23, 'Mycah Akram', '1998-09-14', 'makramm@diigo.com');
insert into employee (id, name, birthday, email) values (24, 'Jonis Draaisma', '2003-07-10', 'jdraaisman@reuters.com');
insert into employee (id, name, birthday, email) values (25, 'Tove Casterou', '1993-07-18', 'tcasterouo@addtoany.com');
insert into employee (id, name, birthday, email) values (26, 'Desdemona Behr', '1992-11-28', 'dbehrp@mtv.com');
insert into employee (id, name, birthday, email) values (27, 'Court Whistlecraft', '1998-01-11', 'cwhistlecraftq@networksolutions.com');
insert into employee (id, name, birthday, email) values (28, 'Brigitta De Bruijn', '1994-07-21', 'bder@over-blog.com');
insert into employee (id, name, birthday, email) values (29, 'Margalo Diano', '1999-09-17', 'mdianos@etsy.com');
insert into employee (id, name, birthday, email) values (30, 'My Bullingham', '2000-03-03', 'mbullinghamt@examiner.com');
insert into employee (id, name, birthday, email) values (31, 'Salvidor Comello', '2002-01-20', 'scomellou@thetimes.co.uk');
insert into employee (id, name, birthday, email) values (32, 'Keriann Royse', '2004-10-29', 'kroysev@miitbeian.gov.cn');
insert into employee (id, name, birthday, email) values (33, 'Collete Baggs', '1998-07-24', 'cbaggsw@mysql.com');
insert into employee (id, name, birthday, email) values (34, 'Vern Cavanagh', '1996-09-19', 'vcavanaghx@zimbio.com');
insert into employee (id, name, birthday, email) values (35, 'Kathy Simmell', '2005-06-10', 'ksimmelly@infoseek.co.jp');
insert into employee (id, name, birthday, email) values (36, 'Aubrie Mixon', '1998-05-25', 'amixonz@japanpost.jp');
insert into employee (id, name, birthday, email) values (37, 'Wit Winks', '2001-05-31', 'wwinks10@hhs.gov');
insert into employee (id, name, birthday, email) values (38, 'Brandice Quayle', '2001-04-27', 'bquayle11@icio.us');
insert into employee (id, name, birthday, email) values (39, 'Rodolfo Jeromson', '2002-02-16', 'rjeromson12@simplemachines.org');
insert into employee (id, name, birthday, email) values (40, 'Adlai Cornfoot', '1996-05-30', 'acornfoot13@studiopress.com');
insert into employee (id, name, birthday, email) values (41, 'Anna Cozby', '1990-09-28', 'acozby14@harvard.edu');
insert into employee (id, name, birthday, email) values (42, 'Xenia Banaszkiewicz', '1992-05-08', 'xbanaszkiewicz15@last.fm');
insert into employee (id, name, birthday, email) values (43, 'Julina Sisson', '2003-06-20', 'jsisson16@columbia.edu');
insert into employee (id, name, birthday, email) values (44, 'Tiffie Andrusyak', '1993-06-26', 'tandrusyak17@clickbank.net');
insert into employee (id, name, birthday, email) values (45, 'Magda Commuzzo', '2000-05-27', 'mcommuzzo18@google.com.hk');
insert into employee (id, name, birthday, email) values (46, 'Ninette Tudgay', '1990-12-25', 'ntudgay19@furl.net');
insert into employee (id, name, birthday, email) values (47, 'Carter Ambrozik', '1997-04-06', 'cambrozik1a@vimeo.com');
insert into employee (id, name, birthday, email) values (48, 'Donal Bettenay', '1992-05-25', 'dbettenay1b@last.fm');
insert into employee (id, name, birthday, email) values (49, 'Sasha Corzor', '2003-10-14', 'scorzor1c@naver.com');
insert into employee (id, name, birthday, email) values (50, 'Berty Fyers', '1996-08-10', 'bfyers1d@a8.net');
~~~

#### 3- Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
~~~sql
UPDATE employee SET name = 'Selçuk Tavukçu' WHERE id = 5;
UPDATE employee SET email = 'selcuk.tavukcu@outlook.com' WHERE name = 'Selçuk Tavukçu';
UPDATE employee SET birthday = '2000-10-03' WHERE email = 'selcuk.tavukcu@outlook.com';
UPDATE employee SET id = 55 WHERE birthday = '2000-10-03';
UPDATE employee SET birthday = '1998-05-13' WHERE id = 10;
~~~

#### 4- Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
~~~sql
DELETE FROM employee WHERE id = 8;
DELETE FROM employee WHERE name = 'Ninette Tudgay';
DELETE FROM employee WHERE email = 'dbettenay1b@last.fm';
DELETE FROM employee WHERE birthday = '1998-05-13';
DELETE FROM employee WHERE name = 'Berty Fyers';
~~~
