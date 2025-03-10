2025-ADVDBMS-WK02S02E02
Week 02 - Review on Database Concepts

Exercise # 02 - Guided Coding Exercise: Creating and Modifying a Table

## **Instructions**

### **Step 1.1: Accept the Assignment**

   1. Click on the assignment link provided by your instructor.
   2. GitHub Classroom will create a **private repository** under your GitHub account.
   3. After the repository is created, click **"Go to Repository"** to view your assignment.

---

### **Step 1.2: Setup your Git Environment**
Only perform this if this is the first time you will setup your Git Environment

   1. Create a GitHub Account:
   ```bash
   https://github.com/signup?source=login
   ```
      
   2. Download and Install Git on your Laptop/Desktop:
   ```bash
   https://git-scm.com/downloads
   ```
   
   3. Create a Folder in your Laptop/Desktop
   4. Right-click anywhere in the created folder and select "Open Git Bash Here".
   5. In the Git Bash Terminal, set your git name, perform command:
   ```bash
   git config --global user.name "Your Name"
   ```
   
   6. In the Git Bash Terminal, set your git email, perform command:
   ```bash
   git config --global user.email "your.email@example.com"
   ```
   
   7. Create your SSH Key, just follow the instructions, no need to provide filename and passphrase. In the Git Bash Terminal, perform command:
   ```bash
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```
   
   8. Copy your SSH Keys into clipboard. In the Git Bash Terminal, perform command:
   ```bash
   clip < ~/.ssh/id_rsa.pub
   ```
   
   9. Log in to your GitHub account.
   10. In the upper-right corner of GitHub, click your profile picture and select Settings.
   11. In the left sidebar, click on SSH and GPG keys.
   12. Click the New SSH key button.
   13. In the Title field, give the key a recognizable name (e.g., "My Windows Laptop").
   14. In the Key field, CTRL + V or paste the keys copied into your clipboard. Save the key.
   15. Go Back to terminal, use command:
   ```bash
   ssh -T git@github.com
   ```

### **Step 2: Clone the Repository to Your Local Machine**

   1. On your repository page, click the green **"Code"** button.
   2. Copy the repository URL (choose HTTPS for simplicity).
   3. Open your terminal (or Git Bash, Command Prompt, or PowerShell) and run:
   
   ```bash
   git clone <git_repo_url>
   ```
   
   4. Navigate into the cloned folder:
   
   ```bash
   cd <git_cloned_folder>
   ```

### **Step 3: Complete the Assignment**

**Exercise # 02 - Guided Coding Exercise: Creating and Modifying a Table**

   **Objective:**
   Practice creating a table with various SQL data types and constraints, then altering its structure by adding a new column. This exercise reinforces SQL DDL (Data Definition Language) commands.

   **Folder Structure:**
   ```
   university_db/
   ├── create_students_table.sql
   └── alter_students_table.sql
   ```

   **File Naming Convention:**
   - `create_students_table.sql`: Contains the SQL statement for creating the `Students` table.
   - `alter_students_table.sql`: Contains the SQL statement for altering the `Students` table.

   **Notable Observations (to be discussed after completing the exercise):**
   - Data Types: This exercise uses `INT`, `VARCHAR`, and `DATE` data types. Explore other data types available in your SQL system (e.g., `TEXT`, `BOOLEAN`, `DATETIME`, `DECIMAL`).
   - Constraints: The `PRIMARY KEY` and `NOT NULL` constraints are used. Investigate other constraints like `UNIQUE`, `CHECK`, and `FOREIGN KEY`.
   - AUTO_INCREMENT/SERIAL/IDENTITY: Pay close attention to the syntax for auto-incrementing primary keys as it varies between database systems.
   - `ALTER TABLE`: The `ALTER TABLE` command is powerful and can be used to add, modify, or drop columns, constraints, and even the table itself.
   - Database Design: After creating the table, the next step would be to insert data into it using the `INSERT` statement. You can then practice querying the data using `SELECT` statements.
   - SQL Syntax: Always refer to the documentation for your specific database management system for the most accurate and up-to-date syntax.
   - Idempotency: It's good practice to make your scripts idempotent where possible. For example, you could add a check in the alter_students_table.sql script to see if the Email column already exists before adding it. This prevents errors if the script is run multiple times. (Example: IF NOT EXISTS (SELECT 1 FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME = 'Students' AND COLUMN_NAME = 'Email') THEN ALTER TABLE Students ADD Email VARCHAR(100); END IF; - This example is MySQL specific and you will need to change it based on your database system.)
      
   **Step-by-Step Instructions:**

   1. Setting up the Environment
      - Ensure you have a SQL database management system installed (e.g., MySQL, PostgreSQL, SQL Server). This exercise will use generic SQL syntax, but you might need to adjust slightly depending on your specific DBMS.
      - If you haven't already, execute the `create_and_use_db.sql` script from the previous exercise to create and select the `UniversityDB` database. This ensures your new table is created in the correct database.
      - Create the two SQL files as shown in the folder structure above within the `university_db` directory.
      
   2. `create_students_table.sql` (Create Students Table):
      - Open `create_students_table`.sql in a text editor.
      - Create the Database:
      ```SQL
      Use `UniversityDB`;

      -- Step 1: Create the Students table with constraints
      CREATE TABLE `Students` (
         `StudentID` INT PRIMARY KEY AUTO_INCREMENT,  -- MySQL Example: AUTO_INCREMENT
         -- For other databases (e.g., PostgreSQL, SQL Server) you might use SERIAL or IDENTITY
         `FirstName` VARCHAR(50) NOT NULL,
         `LastName` VARCHAR(50) NOT NULL,
         `EnrollmentDate` DATE
      );

      ```
      
      - Important Note: The `AUTO_INCREMENT` keyword is specific to MySQL. Other database systems have different ways of handling auto-incrementing primary keys:
         - PostgreSQL: `SERIAL` or `BIGSERIAL` data types. Example: `StudentID SERIAL PRIMARY KEY`
         - SQL Server: IDENTITY(1,1) Example: StudentID INT IDENTITY(1,1) PRIMARY KEY
         - Consult the documentation for your specific database for the correct syntax.
      
   3. `alter_students_table.sql` (Alter Students Table):
      - Open `alter_students_table.sql` in a text editor.
      - Alter the table:
      ```SQL
      Use `UniversityDB`;

      -- Step 2: Alter the table to add an Email column
      ALTER TABLE `Students`
      ADD `Email` VARCHAR(100);

      ```
      - Save the `alter_students_table.sql` file.

   4. Executing the SQL Scripts:
      - Open your SQL client and connect to the `UniversityDB` database.
      - Create Table: Execute the `create_students_table.sql` script. This will create the `Students` table.
      - Alter Table: Execute the `alter_students_table.sql` script. This will add the `Email` column to the `Students` table.

### **Step 4: Push Changes to GitHub**
Once you've completed your changes, follow these steps to upload your work to your GitHub repository.

1. Check the status of your changes:
   Open the terminal and run:
   
   ```bash
   git status
   ```
   This command shows any modified or new files.
   
2. Stage the changes:
   Add all modified files to staging:
   
   ```bash
   git add .
   ```
   
3. Commit your changes:
   Write a meaningful commit message:
   
   ```bash
   git commit -m "Submitting ADVDBMS Week 02 - Session 01 - Exercise 02"
   ```
   
4. Push your changes to GitHub:
   Upload your changes to your remote repository:
   
   ```bash
   git push origin main
   ```
