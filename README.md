# Fitness App

This is a fitness app built using Kivy and KivyMD frameworks in Python for a school project. The app provides various features to help users manage their fitness journey, including workout planning, exercise tracking, nutrition monitoring, and more.

## Features

- User registration and login
- User profile management
- Workout plan generation based on user preferences
- Exercise library with detailed information and techniques
- Workout logging and tracking
- Nutrition tracking and calorie monitoring
- Chatbot for personalized fitness advice
- Progress visualization through graphs and charts
- Integration with OpenAI API for intelligent responses

## Installation

1. Clone the repository:
   ```
   git clone https://github.com/your-username/fitness-app.git
   ```

2. Install the required dependencies:
   ```
   pip install -r requirements.txt
   ```

3. Set up the database:
   - Update the database configuration in `db_config.json` with your database credentials
   - Create a MySQL database for the app with this sql command:
  ```
    CREATE TABLE userdata (
    id CHAR(36) PRIMARY KEY,
    username VARCHAR(255),
    email VARCHAR(255),
    password VARCHAR(255),
    gender VARCHAR(6),
    age INT,
    height DECIMAL(5,2),
    weight DECIMAL(5,2),
    experience_level VARCHAR(50),
    bodyfat DECIMAL(4,2),
    activity_level VARCHAR(255),
    goal VARCHAR(100),
    calories INT,
    equipment VARCHAR(255),
    training_style VARCHAR(100),
    training_frequency VARCHAR(100),
    timestamp DATETIME,
    prioritized_muscle_groups VARCHAR(255)
);

CREATE TABLE food_items (
    user_id CHAR(36),
    label VARCHAR(255),
    kcal INT,
    protein DECIMAL(5,2),
    carbs DECIMAL(5,2),
    fats DECIMAL(5,2),
    fiber DECIMAL(5,2),
    portion_size DECIMAL(5,2),
    weight DECIMAL(6,2),
    unit VARCHAR(10),
    timestamp DATETIME,
    FOREIGN KEY (user_id) REFERENCES userdata(id)
);

CREATE TABLE daily_totals (
    user_id CHAR(36),
    total_calories INT,
    total_protein INT,
    total_fats INT,
    total_carbs INT,
    date DATE,
    daily_target VARCHAR(20),
    FOREIGN KEY (user_id) REFERENCES userdata(id)
);
CREATE TABLE day_exercises (
    day_exercise_id INT AUTO_INCREMENT PRIMARY KEY,
    day_id INT,
    ExerciseID INT,
    sets INT,
    reps INT,
    FOREIGN KEY (day_id) REFERENCES workout_days(day_id),
    FOREIGN KEY (ExerciseID) REFERENCES exercises(ExerciseID)
);

CREATE TABLE exercises (
    ExerciseID INT AUTO_INCREMENT PRIMARY KEY,
    Name VARCHAR(255) NOT NULL
);

CREATE TABLE workout_days (
    day_id INT AUTO_INCREMENT PRIMARY KEY,
    plan_id INT,
    day_number INT,
    FOREIGN KEY (plan_id) REFERENCES workout_plans(plan_id)
);

CREATE TABLE workout_plans (
    plan_id INT AUTO_INCREMENT PRIMARY KEY,
    user_id CHAR(36),
    plan_name VARCHAR(255),
    FOREIGN KEY (user_id) REFERENCES userdata(id)
);

CREATE TABLE chats (
    chat_id INT AUTO_INCREMENT PRIMARY KEY,
    user_id CHAR(36),
    AI VARCHAR(255) NOT NULL,
    timestamp DATETIME,
    sender TEXT,
    FOREIGN KEY (user_id) REFERENCES userdata(id)
);
```
4. Extract assets
    -Extract the assets file and put the files in the same directory as the `fitness app.py` and `fitness_app.kv` files
   
6. Add OpenAI API key:
   -Add your Openai API key in the `.env` file for the chatbot feature to work (optional)
   
8. Run the app:
   ```
   python "fitness app.py"
   ```

## Technologies Used

- Python
- Kivy
- KivyMD
- MySQL
- OpenAI API


## Acknowledgements

- [Kivy](https://kivy.org/)
- [KivyMD](https://kivymd.readthedocs.io/)
- [OpenAI](https://openai.com/)

## Full Breakdown, Design, Analysis, Screenshots and Testing of the final app

- [Project Breakdown](https://github.com/Silmoon18/FitnessApp/blob/main/Silmoon%20Hossain_NEA%20Project%20(1).pdf))
