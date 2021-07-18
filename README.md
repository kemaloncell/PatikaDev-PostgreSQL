[Ödev1](#Ödev1)
<a name="Ödev1"></a><br>
[Ödev2](#Ödev2)
<a name="Ödev2"></a><br>
[Ödev3](#Ödev3)
<a name="Ödev3"></a> <br>
[Ödev4](#Ödev4)
<a name="Ödev4"></a><br>
[Ödev5](#Ödev5)
<a name="Ödev5"></a>

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

