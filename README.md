[Ödev1](#Ödev1)
<a name="Ödev1">&nbsp;&nbsp;
[Ödev2](#Ödev2)
<a name="Ödev2"></a>&nbsp;&nbsp;
[Ödev3](#Ödev3)
<a name="Ödev3"></a>&nbsp;&nbsp;
[Ödev4](#Ödev4)
<a name="Ödev4"></a>&nbsp;&nbsp;
[Ödev5](#Ödev5)
<a name="Ödev5"></a>&nbsp;&nbsp;
[Ödev6](#Ödev6)
<a name="Ödev6"></a>&nbsp;&nbsp;
[Ödev7](#Ödev7)
<a name="Ödev7"></a>&nbsp;&nbsp;
[Ödev8](#Ödev8)
<a name="Ödev8"></a>&nbsp;&nbsp;
[Ödev9](#Ödev9)
<a name="Ödev9"></a>&nbsp;&nbsp;
  
  
# Ödev1

* film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

```sql
select title, description from film 
```

- film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.


```sql
select *  from film where length>60 and length<75
```

- film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.


```sql
select *  from film where rental_rate=0.99 and replacement_cost= 12.99 or replacement_cost=28.99
```


- customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?.

```sql
select first_name , last_name  from customer where first_name='Mary'
```

- film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız. 

```sql
select *  from film where length<50 and not(rental_rate=2.99 or rental_rate=4.99)
```
-------------------------------------------------------------------------------------------


# Ödev2

* film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla

```sql
select * from film where replacement_cost between  12.99 and 16.99
```

*  actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

```sql
select first_name, last_name from actor where first_name in('Penelope','Nick','Ed')
```

*   film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız.

```sql
select * from film
where rental_rate in(0.99, 2.99, 4.99)and replacement_cost in (12.99, 15.99, 28.99)
```
-------------------------------------------------------------------------------------------


# Ödev3

* country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

```sql
select * from country where country ~~* 'a%a';
```

* country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

```sql
select * from country where country ~~ '_____n';
```

*  Film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

```sql
select title from film where  
title ~~* '%t%t%t%t%'
```


* film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99
olan verileri sıralayınız.

```sql
select * from film where  
title ~~ 'C%' and length>90 and rental_rate =2.99

```

-------------------------------------------------------------------------------------------


# Ödev4

* film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

```sql
select distinct replacement_cost from film 
```

* film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır

```sql
select count (distinct replacement_cost) from film 
```

*  film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

```sql
select title , rating from film  where title  like 'T%' and rating = 'G'
```


* country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

```sql
select count(*) from country  where country like '_____' 

```


* city tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?

```sql
select count(*) from city  where city Ilike '%r' 

```

-------------------------------------------------------------------------------------------


# Ödev5

* film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

```sql
select title , length from film where title like '%n' order by length desc limit 5
```

* film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.

```sql
select title , length from film where title like '%n' order by length asc limit 5
```

*  customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

```sql
select * from customer where store_id=1 order by last_name asc  limit 4
```

  -------------------------------------------------------------------------------------------
  
  # Ödev6

* film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

```sql
select avg(rental_rate) from film

```

* film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?

```sql
select count(title) from film where title Ilike 'c%';
```

*  film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

```sql
select max(length) from film where rental_rate= 0.99
```
  
  *  film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

```sql
select  count(distinct replacement_cost) from film where length>150

```

-------------------------------------------------------------------------------------------  
 
# Ödev7

* film tablosunda bulunan filmleri rating değerlerine göre gruplayınız

```sql
select rating ,count(*) from film group by rating
```

*  film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

```sql
select replacement_cost ,count(*)as film_sayısı from film group by replacement_cost having count(*)>50
```
 
  
* customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?

```sql
select store_id ,count(*)as musteri_sayisi from customer group by store_id
```
  
  
 * city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.

```sql
select country_id ,count(*)as sehir_sayisi from city group by country_id order by count(*) desc limit 1
```

-------------------------------------------------------------------------------------------
  
  # Ödev8

* test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

```sql
create table employee(
id serial primary key,
name varchar(50),
birthday date,
email varchar(100)
)
```

*  Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim..

```sql
insert into employee (name, birthday, email) values ('Jeno', '1969-03-26', 'jmatzke0@behance.net');
insert into employee (name, birthday, email) values ('Slade', '1963-06-15', null);
insert into employee (name, birthday, email) values ('Willabella', null, 'wmatuszinski2@ted.com');
insert into employee (name, birthday, email) values ('Zelig', '1918-10-21', 'zwaterhouse3@tripod.com');
insert into employee (name, birthday, email) values ('Sayre', '1945-06-22', null);
insert into employee (name, birthday, email) values ('Adena', '1923-02-18', 'adowdeswell5@craigslist.org');
insert into employee (name, birthday, email) values ('Karisa', '1947-10-01', 'kdewer6@ehow.com');
insert into employee (name, birthday, email) values ('Luciano', '1985-04-09', 'lmackstead7@ask.com');
insert into employee (name, birthday, email) values ('Leigh', '1947-10-04', 'lwaberer8@tmall.com');
insert into employee (name, birthday, email) values ('Bert', '1902-08-05', 'bhumburton9@businesswire.com');
insert into employee (name, birthday, email) values ('Vivyanne', '1922-05-07', 'vseagooda@t.co');
insert into employee (name, birthday, email) values ('Had', '1935-05-09', 'hkorbb@hugedomains.com');
insert into employee (name, birthday, email) values ('Lacey', '1951-10-20', null);
insert into employee (name, birthday, email) values ('Lorene', '1982-07-18', 'lhouchind@cocolog-nifty.com');
insert into employee (name, birthday, email) values ('Jacquelynn', null, 'jferniee@state.gov');
insert into employee (name, birthday, email) values ('Reynold', '1925-08-26', 'remenyf@kickstarter.com');
insert into employee (name, birthday, email) values ('Hartwell', '1979-10-21', 'hpercyg@ebay.co.uk');
insert into employee (name, birthday, email) values ('Maison', '1917-09-30', 'mmcgeaneyh@odnoklassniki.ru');
insert into employee (name, birthday, email) values ('Gavin', '1958-05-21', 'godriscolei@theguardian.com');
insert into employee (name, birthday, email) values ('Tedie', null, 'traingerj@skyrock.com');
insert into employee (name, birthday, email) values ('Crissie', '1933-10-05', null);
insert into employee (name, birthday, email) values ('Skell', null, 'sashbeel@nationalgeographic.com');
insert into employee (name, birthday, email) values ('Issy', '1972-03-08', 'iandreuttim@auda.org.au');
insert into employee (name, birthday, email) values ('Boycey', '1901-10-23', 'bblincon@globo.com');
insert into employee (name, birthday, email) values ('Chad', '1929-07-08', 'cgarahano@engadget.com');
insert into employee (name, birthday, email) values ('Riordan', '1960-11-04', null);
insert into employee (name, birthday, email) values ('Diane', '1967-09-18', 'dheinrichq@reverbnation.com');
insert into employee (name, birthday, email) values ('Leta', '1942-10-05', 'lwilldenr@rambler.ru');
insert into employee (name, birthday, email) values ('Laetitia', '1976-11-09', null);
insert into employee (name, birthday, email) values ('Delcine', null, 'ddimelowt@illinois.edu');
insert into employee (name, birthday, email) values ('Marty', '1951-09-18', 'mortigau@fotki.com');
insert into employee (name, birthday, email) values ('Artemas', '1936-03-04', 'askewsv@macromedia.com');
insert into employee (name, birthday, email) values ('Duffie', '1986-11-01', 'dgibbenw@people.com.cn');
insert into employee (name, birthday, email) values ('Nikolos', '1980-02-13', 'ngouldsmithx@issuu.com');
insert into employee (name, birthday, email) values ('Lorrie', '1934-08-12', 'lbonhamy@hhs.gov');
insert into employee (name, birthday, email) values ('Lilith', '1933-06-12', 'lflukesz@ocn.ne.jp');
insert into employee (name, birthday, email) values ('Jojo', '1904-12-31', 'jbumpass10@google.nl');
insert into employee (name, birthday, email) values ('Christabel', '1988-06-07', 'cgrigorkin11@dedecms.com');
insert into employee (name, birthday, email) values ('Paulie', '1956-11-25', 'pbodicam12@cpanel.net');
insert into employee (name, birthday, email) values ('Jolie', null, 'jornils13@google.it');
insert into employee (name, birthday, email) values ('Diann', '1965-02-26', 'dtugwell14@mapquest.com');
insert into employee (name, birthday, email) values ('Tedda', null, 'tmccrillis15@icq.com');
insert into employee (name, birthday, email) values ('Feliks', '1987-07-27', 'fbeamson16@google.com.br');
insert into employee (name, birthday, email) values ('Marguerite', null, 'mspaughton17@businessinsider.com');
insert into employee (name, birthday, email) values ('Cherianne', '1965-04-29', 'ckelshaw18@utexas.edu');
insert into employee (name, birthday, email) values ('Franciskus', '1996-04-01', 'flindenbaum19@huffingtonpost.com');
insert into employee (name, birthday, email) values ('Thorn', '1920-10-27', 'tsellner1a@ehow.com');
insert into employee (name, birthday, email) values ('Pate', '1957-09-09', 'pladewig1b@xinhuanet.com');
insert into employee (name, birthday, email) values ('Anson', null, 'ajehan1c@ucoz.ru');
insert into employee (name, birthday, email) values ('Marlena', '1982-01-14', 'mmcgaugie1d@who.int');
```
 
  
* Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım

```sql
UPDATE Employee SET name = 'Barbaros' WHERE id = 1;
UPDATE Employee SET email = 'rtb.barbaros@gmail.com' WHERE name = 'Barbaros';
UPDATE Employee SET birthday = '2021/05/29' WHERE email = '123@gmail.com';
UPDATE Employee SET birthday = '2021/05/29',name = 'Revaha' WHERE email = '123@gmail.com';
UPDATE Employee SET name = 'Barbaros',birthday = '2021/05/29' WHERE id = 1;
```
  
  
 * Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

```sql
DELETE FROM Employee WHERE name = 'Revaha';
DELETE FROM Employee WHERE email = 'rtb.barbaros@gmail.com';
DELETE FROM Employee WHERE birthday = '2021/05/29';
DELETE FROM Employee WHERE name = 'Tayyip';
DELETE FROM Employee WHERE id = '1';
```

  
  -------------------------------------------------------------------------------------------  
 
# Ödev9

* city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```sql
select country, city from country inner join city on country.country_id = city.country_id
```

*  customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```sql
select payment_id,first_name, last_name from customer inner join payment on customer.customer_id = payment.customer_id
```
 
  
* customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```sql
select rental_id, first_name, last_name from customer inner join rental on customer.customer_id = rental.customer_id

```
  

-------------------------------------------------------------------------------------------
