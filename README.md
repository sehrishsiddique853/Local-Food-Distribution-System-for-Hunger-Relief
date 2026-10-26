# FoodBridge

**FoodBridge** is a full-stack food donation coordination platform that connects food donors with verified NGOs and helps administrators manage users, donations, requests, and collection status. It aims to improve the coordination of surplus-food redistribution and make donation workflows easier to manage.

The application provides separate role-based workflows for **Donors, NGOs, and Administrators**, covering donation posting, NGO verification, donation requests, collection updates, and notifications.

## Project Links

- **Live Application:** https://www.foodbridge.tech
- **GitHub Repository:** https://github.com/sehrishsiddique853/local-food-charity-system
- **Project Report and Documentation:** Add your publicly accessible report PDF link here.

## Key Features

- **Donor management:** Registration, login, profile management, and surplus-food donation posting.
- **NGO verification:** NGO registration, document uploads, and administrator approval.
- **Donation requests:** NGOs can browse available donations and submit requests.
- **Donation lifecycle management:** Tracking for available, requested, booked, collected, expired, and cancelled donations.
- **Admin dashboard:** Management of users, NGOs, donations, requests, reports, and notifications.
- **Email OTP verification:** Email-based one-time-password verification during registration.
- **Role-based access control:** Protected API routes for donors, NGOs, and administrators.
- **File uploads:** Cloudinary integration for NGO documents and donation images.
- **Notifications:** Notifications for important donation and request events.
- **Responsive interface:** React-based pages and dashboards for different user roles.

## Technology Stack

### Frontend
- React
- Vite
- React Router
- CSS

### Backend
- Node.js
- Express.js
- MongoDB
- Mongoose
- JWT authentication with HTTP-only cookies
- Multer and Cloudinary for file uploads
- Nodemailer for email delivery
- bcrypt for password hashing

## Architecture and Project Structure

The project separates the frontend interface from the backend API, business logic, and database models.

\`\`\`text
local-food-charity-system/
├── backend/
│   ├── config/
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   ├── services/
│   ├── scripts/
│   └── server.js
└── frontend/
    ├── public/
    └── src/
        ├── components/
        ├── context/
        ├── hooks/
        ├── pages/
        ├── sections/
        ├── services/
        └── styles/
\`\`\`

## User Roles and Workflows

### Donor
- Creates an account and manages profile information.
- Posts surplus-food donations.
- Tracks donation status and donation history.
- Maintains pickup address details.

### NGO
- Registers and submits verification details.
- Waits for administrator approval where required.
- Views and requests available donations.
- Views booked donations and updates collection status according to the application workflow.

### Administrator
- Reviews and approves NGO registrations.
- Manages user accounts.
- Reviews donation requests.
- Monitors donation and request reports.
- Manages administrative workflows and notifications.

## API Overview

The backend API is organized into route groups for different responsibilities.

| Route Prefix | Purpose |
|---|---|
| \`/api/auth\` | Authentication, registration, profile, token refresh, and logout |
| \`/api/donations\` | Donation-related endpoints |
| \`/api/ngo\` | NGO donation-request workflows |
| \`/api/admin\` | Administrative management and reporting |
| \`/api/notifications\` | Notifications for authenticated users |
| \`/api/contact\` | Public contact form |

Specific endpoints and permissions are defined in the backend routes and authorization middleware.

## Run Locally

### Prerequisites

Install Node.js and npm. You will also need access to a MongoDB database and credentials for the external services used by your local setup, such as Cloudinary and SMTP email.

### 1. Clone the repository

\`\`\`bash
git clone https://github.com/sehrishsiddique853/local-food-charity-system.git
cd local-food-charity-system
\`\`\`

### 2. Install dependencies

Install backend dependencies:

\`\`\`bash
cd backend
npm install
\`\`\`

Open a second terminal from the repository root and install frontend dependencies:

\`\`\`bash
cd local-food-charity-system/frontend
npm install
\`\`\`

If your second terminal is already inside the repository directory, run \`cd frontend\` instead.

### 3. Configure environment variables

Create a \`.env\` file inside the \`backend/\` directory. The following values are examples; replace the placeholders with your own development credentials.

\`\`\`env
PORT=5000
NODE_ENV=development
MONGO_URI=your_mongodb_connection_string

JWT_SECRET=your_access_token_secret
JWT_REFRESH_SECRET=your_refresh_token_secret

CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret

SMTP_SERVICE=gmail
SMTP_USER=your_email@example.com
SMTP_PASS=your_email_app_password
SMTP_FROM=FoodBridge <your_email@example.com>
SMTP_SECURE=false

ADMIN_EMAIL=admin@example.com
ADMIN_PASSWORD=replace_with_a_strong_local_password
ADMIN_PHONE=your_admin_phone
ADMIN_ADDRESS=Admin Office

EMAIL_DEBUG_OTP=false
DONATION_EXPIRY_INTERVAL_MINUTES=15
\`\`\`

Configure only variables used by your current backend implementation. If your repository contains an example environment file, use it as the source of truth.

If the frontend needs a custom API base URL, create a \`.env\` file inside \`frontend/\`:

\`\`\`env
VITE_API_BASE_URL=http://localhost:5000
\`\`\`

**Security:** Never commit real passwords, API keys, database credentials, SMTP credentials, JWT secrets, or production environment files to GitHub.

### 4. Seed the administrator account

From the \`backend/\` directory, run:

\`\`\`bash
npm run seed:admin
\`\`\`

Use strong credentials for local development and keep administrator login details private.

### 5. Start the application

Start the backend in one terminal:

\`\`\`bash
cd backend
npm run dev
\`\`\`

Start the frontend in another terminal:

\`\`\`bash
cd frontend
npm run dev
\`\`\`

With the default configuration, the local URLs are typically:

- Frontend: http://localhost:5173
- Backend: http://localhost:5000

Actual ports and API URLs may vary depending on your environment configuration.

## Security and Implementation Notes

- Passwords are hashed using bcrypt.
- JWT authentication uses HTTP-only cookies.
- API access is controlled through authentication and role-based authorization middleware.
- NGO functionality requiring verification is restricted until administrator approval.
- Cloudinary is used for configured document and image uploads.
- Email delivery and OTP verification depend on valid SMTP configuration.
- Sensitive values should be excluded from API responses and never exposed in client-side code.

These notes summarize the intended implementation. Review the current source code and deployment configuration when verifying individual security controls.

## Useful Scripts

Run scripts from the appropriate directory.

### Backend

\`\`\`bash
npm run dev
npm start
npm run seed:admin
\`\`\`

### Frontend

\`\`\`bash
npm run dev
npm run build
npm run preview
npm run lint
\`\`\`

To verify the frontend production build:

\`\`\`bash
cd frontend
npm run build
\`\`\`

## Project Status

FoodBridge is a full-stack academic project demonstrating web application development, role-based workflows, authentication and authorization, file uploads, email verification, and donation-request lifecycle management.

The final-year project is being completed in two phases as part of the BS Computer Science degree.

## Contact and Resources

For the live application and source code, use the links at the top of this README. Add the project report PDF when it is ready to share publicly.
