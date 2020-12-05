# 503 Service unavailable

## Problem

You just created a new project, pulled in an existing project or imported a database and you get a 503 Service unavailable page.

## Possible causes

### 1. Your database config is wrong

#### Cause

Your database configuration is incorrectly set

#### Solution

Update your database config, the default location of database config changes is in the `.env` folder in the root of your project.

```
# The Data Source Name (“DSN”) that tells Craft how to connect to the database
DB_DSN=mysql:host=[HOSTNAME/IP];port=[PORT];dbname=[DATABASE NAME];

# The database username to connect with
DB_USER=[USERNAME]

# The database password to connect with
DB_PASSWORD=[PASSWORD]

# The database schema that will be used (PostgreSQL only)
DB_SCHEMA=

# The prefix that should be added to generated table names (only necessary if multiple things are sharing the same database)
DB_TABLE_PREFIX=[TABLE PREFIX]
```

### 2. Your vendor folder is not installed

#### Cause

Your forgot to install your composer dependencies so there is no `vendor` folder in the root of your project

#### Solution

In the root of your project run the `composer install` command

### 3. Your project config is out of sync

#### Cause

Craft keeps track of each project’s configuration in a central store called project config

As you make changes to system settings, Craft will record those setting values to YAML files in a `config/project/` folder. You can then commit those files to your Git repository, just like your templates and front-end resources.

This config can get out of sync when you migrate projects.

#### Solution

Run the `./craft project-config/apply` (windows `.\craft project-config/apply`) command in the root of your project

