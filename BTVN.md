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
