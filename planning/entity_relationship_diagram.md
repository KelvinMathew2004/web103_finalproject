# Entity Relationship Diagram (ERD)

Reference the Creating an Entity Relationship Diagram final project guide in the course portal for more information about how to complete this deliverable.

---

## Step-by-Step: How the FitForge ERD Was Created

### 1. Define the Entities

The **FitForge** app focuses on personalized fitness plans, progress tracking, and a social community.  
The main entities identified are:

- **Users** – individuals using the app  
- **WorkoutPlans** – custom plans created for users  
- **Exercises** – exercises assigned within each plan  
- **Progress** – logs of user performance over time  
- **Goals** – targets users set (e.g., weight loss, strength gain)  
- **CommunityPosts** – posts users share within the FitForge community  

---

### 2. Define the Attributes

Each entity contains specific properties needed for the app to function.

#### 🧍 Users

| Column Name | Type | Description |
|-------------|------|-------------|
| user_id | integer | Primary key |
| name | text | Full name of the user |
| email | text | Unique email address |
| password_hash | text | Encrypted password |
| age | integer | User's age |
| gender | text | User's gender |
| height | float | Height in centimeters |
| weight | float | Weight in kilograms |
| fitness_level | text | Beginner, Intermediate, or Advanced |
| created_at | datetime | Account creation date |

#### 💪 WorkoutPlans

| Column Name | Type | Description |
|-------------|------|-------------|
| plan_id | integer | Primary key |
| user_id | integer | Foreign key → Users.user_id |
| title | text | Name of the plan |
| goal_type | text | Strength, Weight Loss, Endurance, etc. |
| duration_weeks | integer | Duration in weeks |
| created_at | datetime | When plan was generated |

#### 🏋️ Exercises

| Column Name | Type | Description |
|-------------|------|-------------|
| exercise_id | integer | Primary key |
| plan_id | integer | Foreign key → WorkoutPlans.plan_id |
| name | text | Exercise name |
| muscle_group | text | Targeted muscle area |
| sets | integer | Sets per workout |
| reps | integer | Reps per set |
| rest_time | integer | Rest between sets (in seconds) |
| day_of_week | text | Assigned workout day |

#### 📈 Progress

| Column Name | Type | Description |
|-------------|------|-------------|
| progress_id | integer | Primary key |
| user_id | integer | Foreign key → Users.user_id |
| date | datetime | Log date |
| weight | float | User's current weight |
| calories_burned | integer | Total daily calories burned |
| workouts_completed | integer | Number of workouts done |
| notes | text | Optional reflections |

#### 🎯 Goals

| Column Name | Type | Description |
|-------------|------|-------------|
| goal_id | integer | Primary key |
| user_id | integer | Foreign key → Users.user_id |
| goal_type | text | Goal category |
| target_weight | float | Target body weight |
| target_date | datetime | Completion deadline |
| status | text | Ongoing, Completed, Missed |

#### 💬 CommunityPosts

| Column Name | Type | Description |
|-------------|------|-------------|
| post_id | integer | Primary key |
| user_id | integer | Foreign key → Users.user_id |
| title | text | Post title |
| content | text | Post body |
| created_at | datetime | Post creation date |
| likes | integer | Number of likes |

---

### 3. Define the Relationships

Now we map how these entities connect:

| Relationship | Type | Description |
|--------------|------|-------------|
| Users → WorkoutPlans | 1:N | One user can have multiple workout plans |
| WorkoutPlans → Exercises | 1:N | One plan includes multiple exercises |
| Users → Progress | 1:N | One user logs progress multiple times |
| Users → Goals | 1:N | One user can set multiple goals |
| Users → CommunityPosts | 1:N | One user can create multiple posts |

---

### 4. ERD Diagram (Text-Based Representation)

```
┌──────────────┐         ┌──────────────┐
│    Users     │ 1     N │ WorkoutPlans │
│──────────────│─────────│──────────────│
│ user_id (PK) │         │ plan_id (PK) │
│ name         │         │ user_id (FK) │
│ email        │         │ title        │
│ …            │         │ goal_type    │
└──────────────┘         └──────┬───────┘
       │                        │
       │                        │ 1
       │                        │
       │                        │ N
       │                        │
       │                 ┌──────┴───────────┐
       │                 │    Exercises     │
       │                 │──────────────────│
       │                 │ exercise_id (PK) │
       │                 │ plan_id (FK)     │
       │                 │ name             │
       │                 │ sets, reps, etc. │
       │                 └──────────────────┘
       │
       │ 1
       │
       │ N
       │
┌──────┴───────────┬──────────────────┬──────────────────┐
│                  │                  │                  │
┌─────────────┐ ┌──────────┐ ┌──────────────────┐
│  Progress   │ │  Goals   │ │ CommunityPosts   │
│─────────────│ │──────────│ │──────────────────│
│progress_id  │ │goal_id   │ │ post_id (PK)     │
│user_id (FK) │ │user_id   │ │ user_id (FK)     │
│date         │ │goal_type │ │ title, content   │
│weight, notes│ │status    │ │ created_at, likes│
└─────────────┘ └──────────┘ └──────────────────┘
```

---

### 5. Visual Layout (ASCII ERD Overview)

```
              ┌────────────┐
              │   Users    │
              └────┬───────┘
                   │ 1
                   │
                   │ N
      ┌────────────┼────────────┐
      │            │            │
┌─────┴──────┐     │     ┌──────┴─────────┐
│WorkoutPlans│     │     │ CommunityPosts │
└─────┬──────┘     │     └────────────────┘
      │ 1          │
      │            │
      │ N          │ N
      │            │
┌─────┴──────┐     │
│ Exercises  │     │
└────────────┘     │
            ┌──────┴──────┐
            │             │
      ┌─────┴─────┐ ┌─────┴─────┐
      │ Progress  │ │   Goals   │
      └───────────┘ └───────────┘
```

---

### 6. Summary of Relationships

- **Users** `1 → N` **WorkoutPlans**  
- **WorkoutPlans** `1 → N` **Exercises**  
- **Users** `1 → N` **Progress**  
- **Users** `1 → N` **Goals**  
- **Users** `1 → N` **CommunityPosts**

---

### Notes

- All foreign keys reference `Users.user_id` or `WorkoutPlans.plan_id` as applicable.  
- All tables are in **3NF (Third Normal Form)** — no redundant data, each field depends on the key.  
- Diagram tools such as **draw.io**, **dbdiagram.io**, or **Lucidchart** can be used to recreate this diagram visually if required.
