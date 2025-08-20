# Database Schema

## 1. General Information
- **Database Type:** [Relational / NoSQL]  
- **DBMS:** [Örn. MySQL 8, PostgreSQL 15]  
- **Connection Details:** [Opsiyonel, güvenlik nedeniyle şifreleri .env dosyasında sakla]  
- **Charset & Collation:** [Örn. utf8mb4_general_ci]  

---

## 2. Tables Overview
| Table Name | Purpose | Primary Key | Relationships | Notes |
|------------|---------|------------|---------------|-------|
| users      | Kullanıcı bilgileri | id | hasMany(posts), hasMany(orders) | Laravel default user table |
| posts      | Blog/ürün içerikleri | id | belongsTo(users) | Opsiyonel: soft deletes |
| orders     | Sipariş bilgileri | id | belongsTo(users), hasMany(order_items) | Opsiyonel: payment status column |
| order_items | Sipariş detayları | id | belongsTo(orders), belongsTo(products) | Her ürünün miktarı ve fiyatı |
| products   | Ürün/hizmet listesi | id | hasMany(order_items) | Stok bilgisi ve kategori ilişkisi |

-Not: Bu tablo örnek olarak verilmiştir. Projeye göre tablo sayısı ve ilişkiler değişebilir.  

---

## 3. Relationships
- **One-to-Many:**  
  - users → posts  
  - orders → order_items  
- **Many-to-Many:**  
  - products ↔ categories (pivot: category_product)  
- **Polymorphic Relations:** [Opsiyonel: comments, likes gibi]  

---

## 4. Columns & Data Types
| Column Name | Table | Type | Nullable | Default | Notes |
|-------------|-------|------|---------|---------|-------|
| id          | users | BIGINT / UUID | No | auto_increment | Primary key |
| name        | users | VARCHAR(255) | No | - | Kullanıcı adı |
| email       | users | VARCHAR(255) | No | unique | Kullanıcı email |
| password    | users | VARCHAR(255) | No | - | Hash’lenmiş parola |
| created_at  | all tables | TIMESTAMP | No | CURRENT_TIMESTAMP | Laravel timestamps |
| updated_at  | all tables | TIMESTAMP | No | CURRENT_TIMESTAMP | Laravel timestamps |

> Opsiyonel: Projeye özel kolonlar burada eklenebilir.  

---

## 5. Indexes & Constraints
- **Primary Keys:** Tüm tablolar için `id`  
- **Foreign Keys:** Laravel migrations ile tanımlı  
- **Indexes:**  
  - Sık sorgulanan kolonlar için (örn. email, product_name)  
- **Unique Constraints:** email, username, SKU gibi benzersiz alanlar  

---

## 6. Migrations & Seeders
- Tüm tablolar Laravel migration ile oluşturulacak  
- Örnek veriler için seeders kullanılacak  
- Migration rollback kuralları: production ortamda yalnızca forward migration  

---

## 7. Backup & Maintenance
- Günlük otomatik backup planı  
- Yedekleme dosyaları güvenli bir sunucuda saklanacak  
- Restore prosedürü test edilmeli  

---

## 8. Notes
- Projede soft delete ve timestamp kullanımına karar verilmeli  
- Pivot tablolar ve polymorphic ilişkiler ihtiyaç doğrultusunda eklenebilir  
- Proje büyüdükçe index ve query optimizasyonları gözden geçirilmeli
