# Math-Web

This web app provides dashboards for teachers, administrators, and parents to monitor student performance and manage math assessment tests within the Mathoria game. It allows educators to register students, track progress, and adjust assessment tasks for an enhanced learning experience.

## 🚀 Features

- **Student Registration:** Teachers can create student accounts.
- **Real-Time Sync:** Seamlessly integrates with Mathoria's Firebase Realtime Database for live updates.
- **Performance Monitoring:** Enables tracking of student progress, scores, and performance reports.
- **Role-Based Access:** Custom dashboards for principals, administrators, teachers, and parents, with Firebase Authentication.
- **User Role Management:** Principals can assign roles, and administrators can assign teacher or parent roles to users.
- **Classroom Insights (Administrators and Principals):** View school and classroom performance averages and indicators, with drill-down options for detailed student insights.
- **Parental Access:** Parents can track their child's academic progress and performance.
- **Adaptive Quests:** Teachers can adjust assessment tasks based on each student’s performance and learning progress.

## 📦 Tech Stack

- **Frontend:** Angular.
- **Backend:** Firebase Realtime Database & Firebase Authentication.

## ⚙️ How It Works

1. **User Authentication:** Users create an account through Firebase authentication. Principals can assign any role, and administrators can assign teacher and parent roles.
2. **Student Registration:** Teachers create student accounts and generate QR codes that students can use to authenticate in Mathoria game.
3. **Profile Sync:** Student profiles sync with Mathoria, enabling test access.
4. **Monitoring:** Principals, administrators, teachers, and parents can view tailored performance data and analytics based on their assigned roles.
5. **Automatic User IDs:** The `Principal`, `Teacher`, `Parent`, `Administrator`, and `Student` classes inherit the `uid` field from the parent abstract Firebase class `User`. This ensures that each user is uniquely identified.

## 🔑 Registration Flow

1. **Add a Student:** Fill in the student's first name, last name, birthday, grade, gender, email and password.
2. **QR code is generated:** Once the account is created, a QR code is generated and saved as a PDF.
3. **Log into the game:** The student can scan the QR code to log into the game.

## 🔒 Rules & Policies

- Students leaving the game multiple times during a test may automatically fail. If they are disconnected, they will receive a warning, and if disconnected again, the test is considered incomplete.
- Photo URL is used for unique identification (via face recognition).
- User roles (principal, teacher, parent, admin) are linked to their corresponding `uid` from Firebase Authentication.

## 🧑‍💻 Class Diagram

The **Math-Web** app is designed with a clear class structure to manage user roles, student registrations, and data synchronization. Below is the class diagram representing the core components and their relationships:

![Class Diagram](images/class-diagram.png)

### Key Classes:
- **User (Abstract Class):** All user roles (Principal, Teacher, Parent, Administrator, Student) inherit from this class, which includes the `uid` field for unique identification and methods for authentication.
- **Principal:** Can assign roles to other users (administrators, teachers and parents) and has access to school-wide performance data.
- **Teacher:** Responsible for creating student accounts and configuring test mini-games.
- **Administrator:** Has access to performance data at both the classroom and school levels, and can assign teacher and parent roles to users.
- **Parent:** Can monitor their children's academic progress and performance.
- **Student:** Represents the students registered to take the assessment tests, with personalized profiles synced with the Mathoria game.
- **TestConfig:** Represents a test created by a teacher, including duration, grade, default/custom mini-game order, and a map of game configurations (`MiniGameConfig`). Also tracks creation and update timestamps.
- **MiniGameConfig:** Contains mini-game settings for a specific grade, including the teacher’s default config and optional group-specific overrides (`GroupConfig`).
- **GroupConfig:** Associates a set of students with a custom game configuration (`GameConfig`) for more targeted assessment.
- **GameConfig:** Defines detailed settings for each mini-game such as `numQuestions`, `operation`, `displayTime`, `uploadedNumbersAudioLinks`, and more.
- **MiniGame:** Describes the available games with multilingual `title`, `description`, `version`, and default configurations per grade.
- **TestResult:** Stores student scores and timestamps, linking the result to its associated test and student.
- **UserRole (enum):** Defines the possible user roles in the system: `Principal`, `Teacher`, `Parent`, `Administrator`, and `Student`.
- **Language (enum):** Specifies supported languages: `ar`, `fr`, and `en`.
- **TestStatus (enum):** Represents the publication status of a test: `DRAFT`, `PUBLISHED`, `ARCHIVED`, or `DELETED`.
- **GradeLevel (enum):** Represents the academic levels targeted by the system: `One`, `Two`, `Three`, `Four`, `Five`, and `Six`.

---

## 📁 JSON Structure

For real data examples and templates, check the `/JSON_DB` directory:
- `test_config.json` – Full test configuration linked to teacher roles and mini-games.
- `miniGames.json` – Definitions of all available mini-games with multilingual metadata and default configs.
- `users.json` – Sample users from each role (`Principal`, `Administrator`, `Teacher`, `Parent`, and `Student`) linked by `uid` and school.
- `/mini-games-data/` – Individual JSON files with real game content (e.g., choice questions, number-to-letters mappings, math problems, and matching pairs).

---

## 🗂 Sample Project

Check out the sample React project here: [Math Dashboard React](https://github.com/najlae01/math-dashboard-react)

## 📥 Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/najlae01/math-web.git
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Run the app:
   ```bash
   ng serve
   ```

## 🤝 Contributing

1. Fork the repository.
2. Create a new branch (`git checkout -b group-one`).
3. Commit changes (`git commit -m 'Add the group number one'`).
4. Push to the branch (`git push origin group-one`).
5. Open a pull request.

## 📧 Contact

For support, contact [Najlae](mailto:najlae.abarghache@etu.uae.ac.ma).
