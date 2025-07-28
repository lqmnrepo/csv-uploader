# CSV Uploader

A Laravel application that allows users to upload and process CSV files in the background. The system handles deduplication, upserts, and real-time status updates using polling.

## Features

- Upload CSV files via a simple web interface
- Background processing with Laravel queues (Redis + Horizon recommended)
- Handles invalid encoding (non-UTF-8 characters)
- Idempotent file uploads (duplicate rows avoided)
- Supports upserts by `UNIQUE_KEY`
- Upload history with real-time status updates
- Clean, Bootstrap-based UI

## Requirements

- PHP >= 8.1
- Laravel >= 10
- Redis
- Node.js & npm (for assets)
- SQLite or other DB of your choice

## Setup Instructions

1. Clone the repository
1.1 git clone https://github.com/lqmnrepo/csv-uploader.git/
1.2 cd csv-uploader

2. Install PHP dependencies
    composer install

3. Install JS dependencies and compile assets
    npm install
    npm run dev

4. Copy .env
    cp .env.example .env
    php artisan key:generate

5. Set up your database
    php artisan migrate

6. Start the queue worker (or Horizon)
    php artisan queue:work

7. Serve the app
    php artisan serve

## Usage

- Upload a CSV file via the homepage.
- Upload progress is shown in the table.
- Files are processed in the background.
- Duplicate rows are skipped, and existing rows updated using UNIQUE_KEY.
