# redmine_project_repo 

## Setup Guide

This guide will walk you through the process of setting up the Redmine project.

### Prerequisites

Before you begin, ensure that you have the following prerequisites installed:

- Ruby (version >= 2.5)
- RubyGems
- Bundler
- MySQL or PostgreSQL
- Git

### Step 1: Clone the Repository

Clone the repository from GitHub:

```bash
git clone https://github.com/hayderabdela/redmine_project_repo.git
cd redmine_project_repo 
```

### Step 2: Install Dependencies

Install required gems using Bundler:

```bash
bundle install --without development test
```

### Step 3: Configure the Database

Copy the database configuration file:

```bash
cp config/database.yml.example config/database.yml
```
Edit config/database.yml with your database credentials for the desired database adapter (MySQL or PostgreSQL).

### Step 4: Initialize the Database

Run the database migrations and seed data:

```bash
RAILS_ENV=production bundle exec rake db:migrate
RAILS_ENV=production bundle exec rake redmine:load_default_data
```

### Step 5: Generate Secret Token

Generate a secret token for the application:

```bash
bundle exec rake generate_secret_token
```

### Step 6: Precompile Assets

Precompile the assets for production:

```bash
RAILS_ENV=production bundle exec rake assets:precompile
```

### Step 7: Start the Redmine Server

Start the Redmine server:

```bash
bundle exec rails server -e production
```

### Step 8: Access Redmine

Open your web browser and navigate to `http://localhost:3000` to access Redmine. You will be prompted to create an administrator account.

### Additional Configuration (Optional)

- Configure email settings in `config/configuration.yml` to enable email notifications.
- Configure additional plugins or themes as needed.

### Troubleshooting

If you encounter any issues during setup, refer to the Redmine documentation or search for solutions online. Common issues include database configuration errors and missing dependencies.
