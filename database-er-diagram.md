erDiagram
    ADMIN {
        int admin_id PK
        varchar username UK
        varchar password
        timestamp created_at
    }

    CATEGORIES {
        int category_id PK
        varchar category_name
    }

    USERS {
        int user_id PK
        varchar username UK
        varchar password
        varchar email
        timestamp created_at
        varchar avatar
    }

    BOOKS {
        int book_id PK
        varchar title
        varchar author
        int category_id FK
        text description
        date publish_date
        varchar cover_image
        int view_count
        timestamp created_at
    }

    FAVORITES {
        int favorite_id PK
        int user_id FK
        int book_id FK
        timestamp created_at
    }

    RATINGS {
        int rating_id PK
        int user_id FK
        int book_id FK
        tinyint rating
        text review
        timestamp created_at
    }

    USER_TAG_PREFERENCES {
        int pref_id PK
        int user_id FK
        int category_id FK
        tinyint preference_level
    }

    %% Relationships
    CATEGORIES ||--o{ BOOKS : "拥有图书"
    USERS ||--o{ FAVORITES : "创建收藏"
    BOOKS ||--o{ FAVORITES : "被收藏"
    USERS ||--o{ RATINGS : "给出评分"
    BOOKS ||--o{ RATINGS : "收到评分"
    USERS ||--o{ USER_TAG_PREFERENCES : "设置偏好"
    CATEGORIES ||--o{ USER_TAG_PREFERENCES : "被偏好"
