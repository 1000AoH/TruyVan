# TruyVan

**1. Lấy ra thông tin các bộ phim gồm: Tiêu đề, mô tả, thời lượng, special feature, rating. Có rating là PG, special feature là Deleted Scenes, rental_rate nhỏ hơn 2.99:**

    SELECT title, description, rental_duration, special_features, rating FROM film
    WHERE rating = 'PG'
    AND special_features = 'Deleted Scenes'
    AND rental_rate < 2.99

**2. Lấy ra thông tin các bộ phim gồm: Tiêu đề, mô tả, thời lượng, special feature, rating tại các bộ phim có rental rate > trung bình cộng của rental rate có rating là G:**

    SELECT title, description, rental_duration, special_features, rating FROM film
    WHERE rental_rate > (SELECT AVG(rental_rate) FROM film WHERE rating = 'G')

**3. Lấy ra các phim có special feature khác Deleted Scenes:**
    
    SELECT * FROM film
    WHERE special_features # 'Deleted Scenes'
    
# ThucHienTruyVan

**1 Lấy ra thông tin các diễn viễn đóng phim ACADEMY DINOSAUR

    SELECT actor.actor_id,actor.first_name, actor.last_name
    FROM sakila.film
    INNER JOIN sakila.film_actor ON film.film_id = film_actor.film_id 
    INNER JOIN sakila.actor ON film_actor.actor_id = actor.actor_id
    WHERE title = 'ACADEMY DINOSAUR';
    
**2 Lấy ra title, description, release_year, length, rating của các bộ phim có rating là G, đếm xem mỗi phim có bao nhiêu diễn viên tham gia

    SELECT  title, description, release_year, length, rating, count(actor.actor_id) 
    from sakila.film 
    INNER JOIN sakila.film_actor ON film.film_id = film_actor.film_id 
    INNER JOIN sakila.actor ON film_actor.actor_id = actor.actor_id
    where rating = 'G'
    group by film.film_id;

**3 Tính trung bình cộng rental_rate của các phim có CHRISTIAN GABLE tham gia

    SELECT  avg(rental_rate)
    from sakila.film
    INNER JOIN sakila.film_actor ON film.film_id = film_actor.film_id 
    where film_actor.actor_id = (select actor.actor_id from sakila.actor where actor.first_name = 'CHRISTIAN' and actor.last_name = 'GABLE')    
