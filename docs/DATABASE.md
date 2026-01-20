# Database Documentation

StudySmart uses an Oracle database to store user information and generated study materials.

## Connection
The application connects to the Oracle database using the `oracledb` node driver.
Connection details are managed via environment variables:
- `DB_USER`
- `DB_PASSWORD`
- `DB_CONNECTION_STRING` (e.g., `oracle.cise.ufl.edu:1521/orcl`)

**Note:** Connecting to the UF CISE Oracle database usually requires being on the UF VPN or network.

## Schema

### 1. `studysmart_user`
Stores user information.

| Column | Type | Description |
|---|---|---|
| `id` | VARCHAR(100) | Unique user ID (from Clerk) |
| `created_at` | DATE | Account creation date |

### 2. `studysmart_summary`
Stores generated summaries.

| Column | Type | Description |
|---|---|---|
| `id` | NUMBER | Unique ID (Auto-generated) |
| `title` | VARCHAR | Title of the summary |
| `owner` | VARCHAR(100) | Foreign key to `studysmart_user.id` |
| `content` | CLOB | Text content of the summary |
| `created_at` | DATE | Creation timestamp |

### 3. `studysmart_flashcard_deck`
Stores generated flashcard decks.

| Column | Type | Description |
|---|---|---|
| `id` | NUMBER | Unique ID (Auto-generated) |
| `title` | VARCHAR | Title of the deck |
| `owner` | VARCHAR(100) | Foreign key to `studysmart_user.id` |
| `content` | CLOB | JSON string of flashcards array |
| `created_at` | DATE | Creation timestamp |

### 4. `studysmart_quiz`
Stores generated quizzes.

| Column | Type | Description |
|---|---|---|
| `id` | NUMBER | Unique ID (Auto-generated) |
| `title` | VARCHAR | Title of the quiz |
| `owner` | VARCHAR(100) | Foreign key to `studysmart_user.id` |
| `content` | CLOB | JSON string of quiz questions array |
| `created_at` | DATE | Creation timestamp |

## Data Access Layer (`server/db.js`)
The `db.js` file provides helper functions to interact with the database:
- `createUser(userId)`
- `createSummary(title, owner, content)`
- `createFlashcardDeck(title, owner, content)`
- `createQuiz(title, owner, content)`
- `getUserData(userId)`: Fetches all materials for a user.
