Step 1: Laravel Installation
We are going from scratch so, If you haven't installed laravel in your system then you can run bellow command and get fresh Laravel project.
composer create-project --prefer-dist laravel/laravel blog
Step 2: Install Composer Packages
Now we require to install Spatie package for ACL, that way we can use it's method. Also we will install form collection package. So Open your terminal and run bellow command.
composer require spatie/laravel-permission
composer require laravelcollective/html
Now open config/app.php file and add service provider and aliase.
'providers' => [
	Spatie\Permission\PermissionServiceProvider::class,
],
We can also custom changes on Spatie package, so if you also want to changes then you can fire bellow command and get config file in config/permission.php and migration files.
php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"
Now you can see permission.php file and one migrations. so you can run migration using following command:
php artisan migrate
Step 3: Create Product Migration
php artisan make:migration create_products_table
php artisan migrate
Step 4: Create Models
In this step we have to create model for User and Product table, so if you get fresh project then you have User Model have so just replace code and other you should create.
app/Models/User.php
app/Models/Product.php
Step 5: Add Middleware
Spatie package provide it's in-built middleware that way we can use it simply and that is display as bellow:
role
permission
So, we have to add middleware in Kernel.php file this way :
app/Http/Kernel.php
Step 6: Create Authentication
You have to follow few step to make auth in your laravel 8 application.
First, you need to install laravel/ui package as like bellow:
composer require laravel/ui
Here, we need to generate auth scaffolding in laravel 8 using laravel ui command. so, let's generate it by bellow command:
php artisan ui bootstrap --auth
Now you need to run npm command, otherwise you can not see better layout of login and register page
Install NPM:
npm install
Run NPM:
npm run dev
Step 7: Create Routes
We require to add number of route for users module, products module and roles module. In this this route i also use middleware with permission for roles and products route, so add route this way:
routes/web.php
Step 8: Add Controllers
In this step we have add three controller for users module, products module and roles module so you can create three controller like as bellow:
app/Http/Controllers/UserController.php
app/Http/Controllers/ProductController.php
app/Http/Controllers/RoleController.php
Step 9: Add Blade Files
In this step, we need to create following files as like listed bellow:
Theme Layout
app.blade.php
Users Module
index.blade.php create.blade.php edit.blade.php show.blade.php
Roles Module
index.blade.php create.blade.php edit.blade.php show.blade.php
Product Module
index.blade.php create.blade.php edit.blade.php show.blade.php
So, let's create following files:
resources/views/layouts/app.blade.php
resources/views/users/index.blade.php
resources/views/users/create.blade.php
resources/views/users/edit.blade.php
resources/views/users/show.blade.php
resources/views/roles/index.blade.php
resources/views/roles/create.blade.php
resources/views/roles/edit.blade.php
resources/views/roles/show.blade.php
resources/views/products/index.blade.php
resources/views/products/create.blade.php
resources/views/products/edit.blade.php
resources/views/products/show.blade.php
Step 10: Create Seeder For Permissions and AdminUser
In this step we will create seeder for permissions, Right now we have fixed permission so we create using seeder as listed bellow, but if you can add more permission as you want:
1.role-list
2.role-create
3.role-edit
4.role-delete
5.product-list
6.product-create
7.product-edit
8.product-delete
So, first create seeder using bellow command:
php artisan make:seeder PermissionTableSeeder
And put bellow code in PermissionTableSeeder seeder this way:
database/seeds/PermissionTableSeeder.php
After this we have to run bellow command for run PermissionTableSeeder seeder:
php artisan db:seed --class=PermissionTableSeeder
Now let's create new seeder for creating admin user.
php artisan make:seeder CreateAdminUserSeeder
database/seeds/CreateAdminUserSeeder.php
php artisan db:seed --class=CreateAdminUserSeeder
Now we are ready to to run full example of ACL. so let's run our example so run bellow command for quick run:
php artisan serve
Access By
http://localhost:8000/
Email: admin@gmail.com
Password: 123456
