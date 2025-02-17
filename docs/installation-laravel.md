---
title: Installation in Laravel
weight: 4
---

## Laravel Version Compatibility

This package can be used with Laravel 6.0 or higher.

Package Version | Laravel Version
----------------|-----------
   ^6.0         |  8,9,10
   ^5.8         |  7,8,9,10
   ^5.7         |  7,8,9
   ^5.4-^5.6    |  7,8
   5.0-5.3      |  6,7,8
   ^4           |  6,7,8
   ^3           |  5.8
   

## Installing

1. Consult the **Prerequisites** page for important considerations regarding your **User** models!

2. This package **publishes a `config/permission.php` file**. If you already have a file by that name, you must rename or remove it.

3. You can **install the package via composer**:

        composer require spatie/laravel-permission

4. Optional: The service provider will automatically get registered. Or you may manually add the service provider in your `config/app.php` file:

    ```
    'providers' => [
        // ...
        Spatie\Permission\PermissionServiceProvider::class,
    ];
    ```

5. **You should publish** [the migration](https://github.com/spatie/laravel-permission/blob/main/database/migrations/create_permission_tables.php.stub) and the [`config/permission.php` config file](https://github.com/spatie/laravel-permission/blob/main/config/permission.php) with:

    ```
    php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"
    ```

6. NOTE: **If you are using UUIDs**, see the Advanced section of the docs on UUID steps, before you continue. It explains some changes you may want to make to the migrations and config file before continuing. It also mentions important considerations after extending this package's models for UUID capability.

    **If you are going to use the TEAMS features**, you must update your [`config/permission.php` config file](https://github.com/spatie/laravel-permission/blob/main/config/permission.php) and set `'teams' => true,`; and in your database if you want to use a custom foreign key for teams you must change `team_foreign_key`.

7. NOTE: If you are using MySQL 8, look at the migration files for notes about MySQL 8 to set/limit the index key length, and edit accordingly.

8. **Clear your config cache**. This package requires access to the `permission` config. Generally it's bad practice to do config-caching in a development environment. If you've been caching configurations locally, clear your config cache with either of these commands:

        php artisan optimize:clear
        # or
        php artisan config:clear

9. **Run the migrations**: After the config and migration have been published and configured, you can create the tables for this package by running:

        php artisan migrate

10. **Add the necessary trait to your User model**: 

        // The User model requires this trait
        use HasRoles;

   Consult the **Basic Usage** section of the docs to get started using the features of this package.

.


### Default config file contents

You can view the default config file contents at:

[https://github.com/spatie/laravel-permission/blob/main/config/permission.php](https://github.com/spatie/laravel-permission/blob/main/config/permission.php)
