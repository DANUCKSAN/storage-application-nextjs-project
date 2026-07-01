# Storage Management System - Next.js

A modern **Storage Management System** built with **Next.js**, **TypeScript**, **Appwrite**, **Tailwind CSS**, and secure OTP-based authentication.

This application allows users to upload, manage, search, sort, rename, share, download, and delete files through a clean dashboard interface. It also includes storage analytics and file type summaries for documents, images, media, and other files.

## Overview

The Storage Management System is a full-stack file management application built with Next.js App Router and Appwrite. It provides secure user authentication, cloud file storage, file categorization, file sharing, dashboard analytics, and a responsive user interface.

The project is designed to demonstrate real-world SaaS-style application development using modern frontend and backend technologies.

## Features

* User sign up and sign in
* Email OTP authentication
* Secure Appwrite session handling
* File upload using drag and drop
* Maximum file size validation
* Store files in Appwrite Storage
* Save file metadata in Appwrite Database
* Dashboard with storage usage summary
* Recent uploaded files section
* File type categories
* View documents, images, media, and other files
* Search files by name
* Sort files by name, size, and created date
* Rename files
* View file details
* Share files with other users using email
* Download files
* Delete files
* Responsive sidebar navigation
* Mobile navigation
* Toast notifications
* Storage usage chart
* Clean UI with reusable components

## Tech Stack

* Next.js 15
* React 19 RC
* TypeScript
* Tailwind CSS v3
* Appwrite
* Node Appwrite SDK
* React Hook Form
* Zod
* React Dropzone
* Recharts
* Radix UI
* Lucide React
* Input OTP
* Tailwind Merge
* Tailwind CSS Animate
* ESLint
* Prettier

## Project Structure

```bash
storage-application-nextjs-project/
├── app/
│   ├── (auth)/
│   │   ├── sign-in/
│   │   ├── sign-up/
│   │   └── layout.tsx
│   │
│   ├── (root)/
│   │   ├── [type]/
│   │   ├── layout.tsx
│   │   └── page.tsx
│   │
│   ├── fonts/
│   ├── favicon.ico
│   ├── globals.css
│   └── layout.tsx
│
├── components/
│   ├── ui/
│   ├── ActionDropdown.tsx
│   ├── ActionModalContent.tsx
│   ├── AuthForm.tsx
│   ├── Card.tsx
│   ├── Chart.tsx
│   ├── FileUploader.tsx
│   ├── FormattedDateTime.tsx
│   ├── Header.tsx
│   ├── MobileNavigation.tsx
│   ├── OtpModal.tsx
│   ├── Search.tsx
│   ├── SideBar.tsx
│   ├── Sort.tsx
│   └── Thumbnail.tsx
│
├── constants/
│   └── index.ts
│
├── hooks/
│
├── lib/
│   ├── actions/
│   │   ├── file.action.ts
│   │   └── user.action.ts
│   │
│   ├── appwrite/
│   │   ├── config.ts
│   │   └── index.ts
│   │
│   └── utils.ts
│
├── public/
├── type/
│   └── index.d.ts
│
├── .eslintrc.json
├── next.config.ts
├── package.json
├── postcss.config.mjs
├── tailwind.config.ts
├── tsconfig.json
└── README.md
```

## Main Pages

### Sign Up Page

Allows new users to create an account using:

* Full name
* Email address
* Email OTP verification

### Sign In Page

Allows existing users to sign in using:

* Email address
* OTP verification

### Dashboard

The dashboard gives users an overview of their storage usage and recently uploaded files.

Dashboard features include:

* Storage usage summary
* File type usage cards
* Recent uploaded files
* File thumbnails
* File actions dropdown
* Upload button

### File Type Pages

The application includes category-based file pages.

Available categories:

* Documents
* Images
* Media
* Others

Users can filter, search, and sort files inside each category.

## Authentication Flow

The application uses Appwrite email OTP authentication.

```txt
User enters email
        |
        v
Appwrite sends OTP
        |
        v
User enters OTP
        |
        v
Session is created
        |
        v
User is redirected to dashboard
```

## File Upload Flow

```txt
User uploads file
        |
        v
File is validated
        |
        v
File is uploaded to Appwrite Storage
        |
        v
File metadata is saved in Appwrite Database
        |
        v
Dashboard and file list are revalidated
```

## File Management Features

Users can perform the following actions on uploaded files:

| Action   | Description                                    |
| -------- | ---------------------------------------------- |
| Rename   | Rename an uploaded file                        |
| Details  | View file information                          |
| Share    | Share file access with other users using email |
| Download | Download the uploaded file                     |
| Delete   | Delete the file from storage and database      |

## Storage Categories

Files are categorized based on file type.

| Category  | Description                                           |
| --------- | ----------------------------------------------------- |
| Documents | PDF, DOC, DOCX, TXT, and related document files       |
| Images    | JPG, PNG, SVG, GIF, and image files                   |
| Media     | Video and audio files                                 |
| Others    | Any file type that does not match the main categories |

## Sorting Options

Users can sort files by:

* Date created, newest first
* Date created, oldest first
* Name, A-Z
* Name, Z-A
* Size, highest first
* Size, lowest first

## Environment Variables

Create a `.env.local` file in the root directory and add the following values:

```env
NEXT_PUBLIC_APPWRITE_ENDPOINT=your_appwrite_endpoint
NEXT_PUBLIC_APPWRITE_PROJECT=your_appwrite_project_id
NEXT_PUBLIC_APPWRITE_DATABASE=your_appwrite_database_id
NEXT_PUBLIC_APPWRITE_USERS_COLLECTION=your_users_collection_id
NEXT_PUBLIC_APPWRITE_FILES_COLLECTION=your_files_collection_id
NEXT_PUBLIC_APPWRITE_BUCKET=your_storage_bucket_id
NEXT_APPWRITE_KEY=your_appwrite_secret_key
```

Important: never commit your real `.env.local` file to GitHub.

## Appwrite Setup

To run this project, create the following in Appwrite:

### Database

Create a database with two collections:

* Users collection
* Files collection

### Storage

Create a storage bucket for uploaded files.

### Authentication

Enable email OTP authentication in your Appwrite project.

### API Key Permissions

Your Appwrite API key should have permissions for:

* Users
* Databases
* Documents
* Storage
* Files

## Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/DANUCKSAN/storage-application-nextjs-project.git
```

### 2. Navigate to the project folder

```bash
cd storage-application-nextjs-project
```

### 3. Install dependencies

```bash
npm install
```

### 4. Create environment variables

Create a `.env.local` file and add your Appwrite credentials.

### 5. Run the development server

```bash
npm run dev
```

The application will run locally at:

```txt
http://localhost:3000
```

## Available Scripts

### Start development server

```bash
npm run dev
```

### Build for production

```bash
npm run build
```

### Start production server

```bash
npm run start
```

### Run linting

```bash
npm run lint
```

## Main Components

### AuthForm

Handles sign-in and sign-up form submission using React Hook Form and Zod validation.

### OtpModal

Displays the OTP verification modal and verifies the user’s email OTP.

### FileUploader

Handles drag-and-drop file uploads using React Dropzone.

### ActionDropdown

Provides file actions such as rename, details, share, download, and delete.

### ActionModalContent

Displays modal content for file details and sharing.

### Chart

Displays storage usage analytics.

### Search

Allows users to search files by name.

### Sort

Allows users to sort files by date, name, and size.

### SideBar

Displays the main desktop navigation.

### MobileNavigation

Displays the mobile-friendly navigation menu.

### Thumbnail

Displays file thumbnails based on file type.

## Navigation

The application includes the following navigation items:

| Route        | Description           |
| ------------ | --------------------- |
| `/`          | Dashboard             |
| `/documents` | Document files        |
| `/images`    | Image files           |
| `/media`     | Video and audio files |
| `/others`    | Other file types      |
| `/sign-in`   | User sign in          |
| `/sign-up`   | User sign up          |

## Storage Limit

The application calculates storage usage against a default total storage limit of:

```txt
2 GB
```

## UI and Design Highlights

* Clean SaaS-style dashboard
* Responsive desktop and mobile layout
* File type cards
* Storage analytics chart
* Modern sidebar navigation
* Drag-and-drop upload experience
* Modal-based file actions
* Toast notification feedback
* Reusable UI components
* Professional file management interface

## Learning Outcomes

This project demonstrates practical experience with:

* Building a full-stack Next.js application
* Using Appwrite for authentication, database, and storage
* Implementing OTP-based authentication
* Handling secure sessions with cookies
* Uploading files with React Dropzone
* Managing server actions in Next.js
* Creating reusable dashboard components
* Implementing file search and sorting
* Managing file metadata
* Building responsive layouts with Tailwind CSS
* Creating SaaS-style user interfaces

## Future Improvements

* Add real-time upload progress
* Add folder creation support
* Add file preview page
* Add bulk file delete
* Add bulk file download
* Add drag-and-drop folder upload
* Add user profile settings
* Add storage upgrade plans
* Add role-based access control
* Add team/workspace support
* Add advanced file permissions
* Add dark/light mode toggle
* Add automated testing
* Add CI/CD workflow using GitHub Actions
* Deploy to Vercel

## Repository Description

A modern storage management system built with Next.js, TypeScript, Appwrite, Tailwind CSS, file upload, OTP authentication, sharing, and dashboard analytics.

## Topics

```txt
nextjs
nextjs15
typescript
react
react19
tailwindcss
tailwind3
appwrite
storage-management
file-management
file-upload
cloud-storage
otp-authentication
dashboard
recharts
react-hook-form
zod
radix-ui
react-dropzone
fullstack
responsive-design
portfolio-project
```

## Author

**Danucksan Sathiyaraj**

GitHub: DANUCKSAN

## License

This project is open-source and available for learning, portfolio, and demonstration purposes.
