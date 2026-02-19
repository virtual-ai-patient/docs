## Project Overview: AI Medical Simulation Bot

**Goal:** A Telegram bot where doctors can practice clinical reasoning by interacting with virtual AI patients.
### Roles

- **Administrator:** Manages cases, users, and system settings.
- **Doctor:** The end-user who diagnoses and treats virtual patients.
- **AI Patient:** The virtual persona generated based on case details.
### Use Cases

- **Initiating a Case:** The Doctor selects a case category and sub-category; the bot initializes a dedicated chat session with the AI Patient.
- **Ordering Diagnostics:** The Doctor can order specific laboratory tests or investigations.
- **Communication:** The Doctor interacts with the AI Patient via natural language to gather history.
- **Case Conclusion:** The Doctor can end the session to receive feedback or a final evaluation.

---

## Database Schema

### User & Permissions

- **User**
    - First Name
    - Last Name
    - Login
    - Password Hash
- **Role**
    - Name (e.g., Administrator, Doctor)
- **Permission**
    - Name (e.g., "Work with cases", "CRUD operations on cases")
- **Role_Permission** (Join table)
- **User_Role** (Join table)
### Clinical Cases

- **Case**
    - Title
    - Description
    - Estimated Duration
    - Difficulty Level (Easy, Medium, Hard)
    - Status (Not Started, In Progress, Completed)
- **Case Details**
    - Pain Character (e.g., sharp, dull, throbbing)
    - Pain Intensity (Scale 1–10)
    - Localization (Enum/List)
    - Associated Symptoms
- **Message**
    - Text Content
    - Sender Type (AI Patient or Doctor)
    - Timestamp
### Diagnostics & Results

- **Lab Test**
    - Name
    - Description
    - Cost (USD)
    - Turnaround Time (Processing time)
- **Case_LabTest** (Join table linking available tests to specific cases)
    
- **Lab Test Result**
    - Reference to `Case_LabTest`
    - Value
    - Unit Reference (Link to Units table)
    - Reference Range Min
    - Reference Range Max
    - Notes/Comments
- **Measurement Units**
    - Unit Name (e.g., mmol/L, mg/dL, g/L)