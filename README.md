# [Material Dashboard 2 PRO Laravel](https://material-dashboard-pro-laravel.creative-tim.com)
![version](https://img.shields.io/badge/version-3.0.1-blue.svg) 
[![GitHub issues open](https://img.shields.io/github/issues/creativetimofficial/ct-material-dashboard-pro-laravel.svg)](https://github.com/creativetimofficial/ct-material-dashboard-pro-laravel/issues?q=is%3Aopen+is%3Aissue) 
[![GitHub issues closed](https://img.shields.io/github/issues-closed-raw/creativetimofficial/ct-material-dashboard-pro-laravel.svg)](https://github.com/creativetimofficial/ct-material-dashboard-pro-laravel/issues?q=is%3Aissue+is%3Aclosed)


*Frontend version*: Material Dashboard v3.0.1. More info at  https://www.creative-tim.com/product/material-dashboard-pro

[<img src="https://s3.amazonaws.com/creativetim_bucket/products/158/original/material-dashboard-pro-laravel.jpg" width="100%" />](https://material-dashboard-pro-laravel.creative-tim.com) 

Material Dashboard PRO Laravel combines hundreds of premium Bootstrap 5 frontend components with an out of the box Laravel backend. In short, it's the ultimate fullstack resource we coded with [UPDIVISION](https://updivision.com/) to help developers build complex apps faster. 

## Designed to save time
The backend is fully integrated, meaning you can easily tick all the boxes for a fully-functional admin panel for your custom application. You have hundreds of UI components to choose from, which you can easily edit using Sass files and classes. In short, everything you need so that your app looks like you want it to look and does what you want it to do.
## Free demo
Check out the open-source demo version for a taste of what Material Dashboard PRO Laravel has to offer. 
## Table of Contents
* [Prerequisites](#prerequisites)
* [Installation](#installation)
* [Usage](#usage)
* [Versions](#versions)
* [Demo](#demo)
* [Documentation](#documentation)
* [Login](#login)
* [Register](#register)
* [Forgot Password](#forgot-password)
* [Reset Password](#reset-password)
* [User Profile](#my-profile)
* [User Management](#user-management)
* [Role Management](#role-management)
* [Category Management](#category-management)
* [Tag Management](#tag-management)
* [Item Management](#item-management)
* [File Structure](#file-structure)
* [Browser Support](#browser-support)
* [Reporting Issues](#reporting-issues)
* [Licensing](#licensing)
* [Useful Links](#useful-links)
* [Social Media](#social-media)
* [Credits](#credits)
## Prerequisites
If you don't already have an Apache local environment with PHP and MySQL, use one of the following links:
 - Windows: https://updivision.com/blog/post/beginner-s-guide-to-setting-up-your-local-development-environment-on-windows
 - Linux: https://howtoubuntu.org/how-to-install-lamp-on-ubuntu
 - Mac: https://wpshout.com/quick-guides/how-to-install-mamp-on-your-mac/
Also, you will need to install Composer: https://getcomposer.org/doc/00-intro.md   
And Laravel: https://laravel.com/docs/9.x/installation
## Installation
1. Unzip the downloaded archive
2. Copy and paste **material-dashboard-2-pro-laravel-main** folder in your **projects** folder. Rename the folder to your project's name
3. In your terminal run `composer install`
4. Copy `.env.example` to `.env` and updated the configurations (mainly the database configuration)
5. In your terminal run `php artisan key:generate`
6. Run `php artisan migrate --seed` to create the database tables and seed the roles and users tables
7. Run `php artisan storage:link` to create the storage symlink (if you are using **Vagrant** with **Homestead** for development, remember to ssh into your virtual machine and run the command from there).

## Usage
Register a user or login with the default users with different roles from your database and start testing (make sure to run the migrations and seeders for these credentials to be available):
* **admin@material.com** and password **secret**
* **creator@material.com** and password **secret**
* **member@material.com** and password **secret**

Besides the numerous types of dashboard, you can find pages for editing your profile, pages for managing the users, the roles, the items, the categories and the tags. There are also static pages for profile, for users, for projects, for accounts, for various applications, for ecommerce and different styles of pages for authentication. All the necessary files are installed out of the box and all the needed routes are added to `routes/web.php`. Keep in mind that all of the features can be viewed once you login using the credentials provided or by registering your own user. 

## Versions
[<img src="https://github.com/creativetimofficial/public-assets/blob/master/logos/html-logo.jpg?raw=true" width="60" height="60" />](https://demos.creative-tim.com/material-dashboard-pro/pages/dashboards/analytics.html)
[<img src="https://github.com/creativetimofficial/public-assets/blob/master/logos/laravel_logo.png?raw=true" width="60" height="60" />](https://material-dashboard-pro-laravel.creative-tim.com)

| HTML | Laravel |
| --- | --- |
| [<img src="https://s3.amazonaws.com/creativetim_bucket/products/51/thumb/opt_mdp_thumbnail.jpg" width="483"/>](https://www.creative-tim.com/product/material-dashboard-pro) | [<img src="https://s3.amazonaws.com/creativetim_bucket/products/158/thumb/material-dashboard-pro-laravel.jpg" width="483"/>](https://www.creative-tim.com/product/material-dashboard-pro-laravel)

| Vue | React |
| --- | --- |
| [<img src="https://s3.amazonaws.com/creativetim_bucket/products/595/thumb/vue-material-dashboard-pro.jpg" width="483"/>](https://www.creative-tim.com/product/vue-material-dashboard-2-pro) | [<img src="https://s3.amazonaws.com/creativetim_bucket/products/80/thumb/material-dashboard-pro-react.jpg" width="483"/>](https://www.creative-tim.com/product/material-dashboard-pro-react)

## Demo
| Register | Login | 
| --- | --- | 
| [<img src="https://github.com/AlexVlad95/material-dashboard-2-laravel-pro/blob/main/screens/register.png" width="483" />](https://material-dashboard-pro-laravel.creative-tim.com/sign-up) | [<img src="https://github.com/AlexVlad95/material-dashboard-2-laravel-pro/blob/main/screens/login.png" width="483" />](https://material-dashboard-pro-laravel.creative-tim.com/sign-in)  

| Forgot Password Page | Reset Password Page | 
| --- | --- | 
| [<img src="https://github.com/AlexVlad95/material-dashboard-2-laravel-pro/blob/main/screens/forgot-password.png" width="483" />](https://material-dashboard-pro-laravel.creative-tim.com/verify) | [<img src="https://github.com/AlexVlad95/material-dashboard-2-laravel-pro/blob/main/screens/reset-password.PNG" width="483" />](https://material-dashboard-pro-laravel.creative-tim.com/sign-in) 

| Dashboard | Virtual Reality  |
| ---  | ---  |
| [<img src="https://github.com/AlexVlad95/material-dashboard-2-laravel-pro/blob/main/screens/dashboard.PNG" width="480" />](https://material-dashboard-pro-laravel.creative-tim.com/dashboard) | [<img src="https://github.com/AlexVlad95/material-dashboard-2-laravel-pro/blob/main/screens/vritual-reality.PNG" width="484"/>](https://material-dashboard-pro-laravel.creative-tim.com/vr-default)

| Profile Page | User Management |
| ---  | ---  |
| [<img src="https://github.com/AlexVlad95/material-dashboard-2-laravel-pro/blob/main/screens/profile.png" width="485"/>](https://material-dashboard-pro-laravel.creative-tim.com/user-profile) | [<img src="https://github.com/AlexVlad95/material-dashboard-2-laravel-pro/blob/main/screens/user-management.png" width="475"/>](https://material-dashboard-pro-laravel.creative-tim.com/user-management)

| Role Management | Item Management  |
| --- | --- | 
| [<img src="https://github.com/AlexVlad95/material-dashboard-2-laravel-pro/blob/main/screens/role.png" width="483"/>](https://material-dashboard-pro-laravel.creative-tim.com/roles)| [<img src="https://github.com/AlexVlad95/material-dashboard-2-laravel-pro/blob/main/screens/items.PNG" width="483"/>](https://material-dashboard-pro-laravel.creative-tim.com/items)

| Category Management | Tag Management | 
| --- | --- |
| [<img src="https://github.com/AlexVlad95/material-dashboard-2-laravel-pro/blob/main/screens/category.png" width="483"/>](https://material-dashboard-pro-laravel.creative-tim.com/category) | [<img src="https://github.com/AlexVlad95/material-dashboard-2-laravel-pro/blob/main/screens/tag.png" width="483"/>](https://material-dashboard-pro-laravel.creative-tim.com/tag)
[View More](https://material-dashboard-pro-laravel.creative-tim.com/dashboard)

## Documentation
The documentation for the Material Dashboard Laravel is hosted at our [website](https://material-dashboard-pro-laravel.creative-tim.com/documentation/getting-started/installation.html).

### Login
If you are not logged in you can only access this page or the Sign Up page. The default url takes you to the login page where you use the default credentials **admin@material.com** with the password **secret** but you can change them with the credentials for creator and for member. Logging in is possible only with already existing credentials. For this to work you should have run the migrations. The user also has the option to choose if he wants to be remembered or not.

The `App/Http/Controllers/SessionsController.php` handles the logging in of an existing user.

```
      public function store()
    {
        $attributes = request()->validate([
            'email' => 'required|email',
            'password' => 'required'
        ]);

        if (! auth()->attempt($attributes)) {
            throw ValidationException::withMessages([
                'email' => 'Your provided credentials could not be verified.'
            ]);
        }

        session()->regenerate();

        return redirect('/dashboard');

    }
```

### Register
You can register as a user by filling in the name, email, role and password for your account. For your role you can choose between the Admin, Creator and Member. It is important to know that an admin user has access to all the pages and actions, can delete, add and edit another users, other roles, items, tags or categories; a creator user has acces to category, tag and item management, but can not add, edit or delete other users; a member user has access to the item management but can not take any actions. You can do this by accessing the sign up page from the "**Sign Up**" button in the top navbar or by clicking the "**Sign Up**" button from the bottom of the log in form. Another simple way is adding **/sign-up** in the url.

The `App/Http/Controllers/RegisterController.php` handles the registration of a new user.

```
    public function store(){

        $attributes = request()->validate([
            'name' => 'required|max:255|unique:users,name',
            'email' => 'required|email|max:255|unique:users,email',
            'password' => 'required|min:7|max:255',
            'role_id'=>'required'
        ]);

        $user = User::create($attributes);
        auth()->login($user);
        
        return redirect('/dashboard');
    } 
```

### Forgot Password
If a user forgets the account's password it is possible to reset the password. For this the user should click on the "**here**" under the login form.

The `App/Http/Controllers/SessionsController.php` takes care of sending an email to the user where he can reset the password afterwards.

```
    public function show(){
    
        request()->validate([
            'email' => 'required|email',
        ]);

        $status = Password::sendResetLink(
            request()->only('email')
        );
    
        return $status === Password::RESET_LINK_SENT
                    ? back()->with(['status' => __($status)])
                    : back()->withErrors(['email' => __($status)]);
    }
```

### Reset Password
The user who forgot the password gets an email on the account's email address. The user can access the reset password page by clicking the button found in the email. The link for resetting the password is available for 12 hours. The user must add the new password and confirm the password for his password to be updated. The user is redirected to the login page.

The `App/Http/Controllers/SessionsController.php` helps the user reset the password.

```
    public function update(){
        
        request()->validate([
            'token' => 'required',
            'email' => 'required|email',
            'password' => 'required|min:8|confirmed',
        ]); 
          
        $status = Password::reset(
            request()->only('email', 'password', 'password_confirmation', 'token'),
            function ($user, $password) {
                $user->forceFill([
                    'password' => ($password)
                ])->setRememberToken(Str::random(60));
    
                $user->save();
    
                event(new PasswordReset($user));
            }
        );
    
        return $status === Password::PASSWORD_RESET
                    ? redirect()->route('login')->with('status', __($status))
                    : back()->withErrors(['email' => [__($status)]]);
    }
```

### My Profile
The profile can be accessed by a logged in user by clicking "**User Profile**" from the sidebar or adding **/user-profile** in the url. The user can add information like phone number, location or change name, email and password.

The `App/Http/Controllers/UserController.php` handles the user's profile information.

```
    public function passwordUpdate(){

        request()->validate([ 
            'old_password' => 'required',
            'password' => 'required|min:7|confirmed',
        ]);
 
        $hashedPassword = auth()->user()->password;

        if (Hash::check(request()->old_password , $hashedPassword)) {
            if (!Hash::check(request()->password , $hashedPassword))
            {
                $users = User::findorFail(auth()->user()->id);
                $users->password = request()->password;
                $users->save();
                return back()->with(['success'=>'Password successfully updated.']);
            }
            else{
                return back()->with(['error' =>"New password can not be the old password!"]);
            } 
        }
        else{
            return back()->with(['error' =>"Old password doesn't match"]);
        }
    }
```

### User Management
The user management can be accessed by clicking "**User Management**" from the **Laravel Examples** section from the sidebar or by adding "**/users-management** in the url. This page is available for users with the **Admin** role and the user is able to **add**, **edit** and **delete** other users. For adding a new user you can press the "**+ Add User**". If you would like to edit or delete an user you can click on the **Action** column. It is also possible to sort the fields or to search in the fields.

On the page for adding a new user you will find a form which allows you to fill the information. All pages are generated using blade templates.

The `App/Http/Controllers/UserManagementController.php ` takes care of data validation and creating the new user:

```
      public function store(){

        $attributes = request()->validate([
            'email' => 'required|unique:users,email',
            'name' =>'required|',
            'password' => 'required|confirmed|min:7',
            'picture' => 'required|mimes:jpg,jpeg,png,bmp,tiff |max:4096',
            'role_id' => 'required|exists:roles,id',
        ]);

        $path = request()->picture->store('profile', 'public');
        $attributes['picture'] = "$path";


        User::create($attributes);

        return redirect('users-management')->withStatus('User successfully created.');
    }
```
Once the user pressed **Send** at the end of the form the new user is added to the table.
For authorizing this actions have been used policies such as `App\Policies\UserPolicy`:
```
    /**
     * Determine whether the authenticate user can manage other users.
     */
    public function manageUsers(User $user)
    {
        return $user->isAdmin();
    }
```

### Role Management
The PRO version lets you add roles to the user. The default roles are **Admin**, **Creator**  and **Member**. The role management can be accessed by clicking "**Role Management**" from the **Laravel Examples** section of the sidebar or by adding "**/roles** in the url. This page is available for users with the **Admin** role and the user is able to **add**, **edit** and **delete** roles. For adding a new role you can press the "**+ Add Role**" button. If you would like to edit or delete a role you can click on the **Action** column. It is also possible to sort the fields or to search in the fields.

On the page for adding a new role you will find a form which allows you to fill the name and the description of the new role.

The `App/Http/Controllers/RolesController.php ` takes care of data validation and creation of a the new role:

```
    public function store(){

        $attributes = request()->validate([
            'name' => 'required|max:255|unique:roles,name',
            'description' =>'required|min:5',
        ]);

        Role::create($attributes);

        return redirect('roles')->withStatus('Role successfully created.');
    }

```

### Category Management
The theme has some default categories but an **Admin** or **Creator** user can manage these categories.The category management can be accessed by clicking "**Category Management**" from the **Laravel Examples** section of the sidebar or by adding "**/category** in the url. The authenticated user can **add**, **edit** and **delete** categories. For adding a new category you can press the "**+ Add Category**" button. If you would like to edit or delete a category you can click on the **Action** column. It is also possible to sort the fields or to search in the fields.

On the page for adding a new category you will find a form which allows you to fill the name and the description of the new category.

The `App/Http/Controllers/CategoryController.php ` takes care of data validation when changing a category and updating it:

```
       public function update($id){
        
        request()->validate([
            'name' => 'required|max:255|unique:categories,name,'.$id,
            'description' =>'required|min:5',
        ]);

        Category::find($id)->update(request()->all());

        return redirect('category')->withStatus('Category successfully updated.');
    }
```

### Tag Management
The theme has some default tags but an **Admin** or **Creator** user can manage these tags.The tag management can be accessed by clicking "**Tag Managmenet**" from the **Laravel Examples** section from the sidebar or by adding "**/tag** in the url. The authenticated user can **add**, **edit** and **delete** tags. For adding a new tag you can press the "**+ Add Tag**" button. If you would like to edit or delete a tag you can click on the **Action** column. It is also possible to sort the fields or to search in the fields.

On the page for adding a new category you will find a form which allows you to fill the name and the description of the new tag and on the edit page you will find a similar form for the changes you wish to make.

The `/resources/views/laravel-examples/tag/edit.blade.php` is the blade template for editing a tag:

```
    @error('color')
      <p class='text-danger'>{{ $message }} </p>
    @enderror
    <div class="form-group col-12 mt-2 col-md-6">
      <label for="exampleColorInput" class="form-label">Color picker</label>
      <input type="color" name='color' class="form-control form-control-color" id="exampleColorInput" value="{{ old('color', $tag->color) }}">
    </div>
```

### Item Management
Item Management is the most advanced example included in the PRO theme because every item has a picture, has a category and has multiple tags. The item management can be accessed by clicking "**Item Management**" from the **Laravel Examples** section of the sidebar or by adding "**/items** in the url. The authenticated user as an Admin or Creator can **add**, **edit** and **delete** items. For adding a new item you can press the "**+ Add Item**" button. If you would like to edit or delete an item you can click on the **Action** column. It is also possible to sort the fields or to search in the fields. The Member user can not take any actions on the item, he is only able to see the item management table.

On the page for adding a new item you will find a form which allows you to add an image of the item, to  fill the name, description of the item, a dropdown to choose the category and a multiselect for the tags.

The `App/Http/Controllers/ItemsController.php` takes care of data validation when adding a new item and of the item creation(see snippet below):

```
      public function store(){

        $attributes=request()->validate([
            'name' => 'required|min:3|unique:items,name',
            'category_id' =>'required|exists:categories,id',
            'description' => 'required',
            'picture' => 'required|mimes:jpg,jpeg,png,bmp,tiff |max:4096',
            'tags' => 'required',
            'tags.*' => 'exists:tags,id',
            'status' =>'required|in:published,draft,archive',
            'options' => 'required',
            'date' => 'required'
        ]);
       
        $path = request()->picture->store('pictures', 'public');
        $attributes['picture'] = "$path";

        $attributes['homepage'] = request()->homepage ? 1 : 0;
        $attributes['options'] = request()->options ? request()->options : null;

        $item = Item::create($attributes);
        $item->tag()->sync(request()->get('tags'));

        return redirect('items')->withStatus('Item successfully created.');

    }
```

## File Structure
```
app
├── Console
│   └── Kernel.php
├── Exceptions
│   └── Handler.php
├── Http
│   ├── Controllers
│   │   ├── Controller.php
│   │   ├── CategoryController.php
│   │   ├── DashboardController.php
│   │   ├── ItemsController.php
│   │   ├── RolesController.php 
│   │   ├── SessionsController.php
│   │   ├── TagController.php
│   │   ├── UserController.php
│   │   ├── UserManagementController.php
|   ├── Kernel.php
│   └── Middleware
│       ├── Authenticate.php
│       ├── EncryptCookies.php
│       ├── PreventRequestsDuringMaintenance.php
│       ├── RedirectIfAuthenticated.php
│       ├── TrimStrings.php
│       ├── TrustHosts.php
│       ├── TrustProxies.php
│       └── VerifyCsrfToken.php
├── Models
│   ├── Category.php
│   ├── Item.php
│   ├── Role.php
│   ├── Tag.php
│   └── User.php
├── Policies
│   ├── CategoryPolicy.php
│   ├── ItemPolicy.php
│   ├── RolePolicy.php
│   ├── TagPolicy.php
│   └── UserPolicy.php
├── Providers
│   ├── AppServiceProvider.php
│   ├── AuthServiceProvider.php
│   ├── BroadcastServiceProvider.php
│   ├── EventServiceProvider.php
│   └── RouteServiceProvider.php
├── Database
|   ...
|   |
│   └── Seeders
│       ├── CategorySeeder.php
│       ├── DatabaseSeeder.php
│       ├── ItemSeeder.php
│       ├── RolesSeeder.php
│       ├── TagSeeder.php
│       └── UserSeeder.php
└── Resources
|   |
|   ...
│   └── Views
│       ├── applications
|       │          ├── calendar.blade.php
│       |          ├── crm.blade.php
│       |          ├── datatables.blade.php
│       |          ├── kanban.blade.php
│       |          ├── stats.blade.php
│       |          └── wizard.blade.php
│       ├── authentication
│       |          ├── lock
|       |          |        ├── basic.blade.php
|       |          |        ├── cover.blade.php
|       |          |        └── illustration.blade.php
│       |          ├── reset
|       |          |        ├── basic.blade.php
|       |          |        ├── cover.blade.php
|       |          |        └── illustration.blade.php
│       |          ├── sign-in
|       |          |        ├── basic.blade.php
|       |          |        ├── cover.blade.php
|       |          |        └── illustration.blade.php
│       |          ├── sign-up
|       |          |        ├── basic.blade.php
|       |          |        ├── cover.blade.php
|       |          |        └── illustration.blade.php
│       |          └── verification
|       |                   ├── basic.blade.php
|       |                   ├── cover.blade.php
|       |                   └── illustration.blade.php
│       ├── components
|       │          ├── auth
|       |          |        ├── footers
|       |          |        |        ├── auth
|       |          │        |              └── footer.blade.php
|       |          │        |        └── guest
|       |          │        |              ├── basic-footer.blade.php
|       |          │        |              └── social-icons-footer.blade.php 
|       │          |        └── navbars
|       |          |                ├── navs
|       |          |                |     ├── auth,blade.php
|       |          │                |     └── guest.blade.php
|       |          │                └── sidebar.blade.php
│       |          ├── page-template.blade.php
│       |          └── plugins.blade.php
│       ├── dashboard
│       |          ├── automotive.blade.php
│       |          ├── discover.blade.php
│       |          ├── index.blade.php
│       |          ├── sales.blade.php
│       |          └── smart-home.blade.php
│       ├── ecommerce
|       │          ├── orders
|       |          |        ├── details.blade.php
|       │          |        └── list.blade.php
|       │          ├── products
|       |          |        ├── edit-product.blade.php
|       |          |        ├── new-product.blade.php
|       |          |        ├── product-page.blade.php
|       │          |        └── products-list.blade.php
│       |          └── referral.blade.php
│       ├── errors
|       │          ├── 401.blade.php
│       |          ├── 403.blade.php
│       |          ├── 404.blade.php
│       |          ├── 419.blade.php
│       |          ├── 429.blade.php
│       |          ├── 500.blade.php
│       |          └── 503.blade.php
│       ├── laravel-examples
|       │          ├── category
|       |          |        ├── create.blade.php
|       |          |        ├── edit.blade.php
|       |          |        └── index.blade.php
|       │          ├── items
|       |          |        ├── create.blade.php
|       |          |        ├── edit.blade.php
|       │          |        └── index.blade.php
|       │          ├── roles
|       |          |        ├── create.blade.php
|       |          |        ├── edit.blade.php
|       │          |        └── index.blade.php
|       │          ├── tag
|       |          |        ├── create.blade.php
|       |          |        ├── edit.blade.php
|       │          |        └── index.blade.php
|       |          |
|       │          ├── user-profile
|       │          |        └── edit.blade.php
|       │          ├── users
|       |          |        ├── create.blade.php
|       |          |        ├── edit.blade.php
|       │          |        └── index.blade.php
│       ├── pages
|       │          ├── account
|       |          |        ├── billing.blade.php
|       |          |        ├── invoice.blade.php
|       |          |        ├── security.blade.php
|       │          |        └── settings.blade.php
|       │          ├── profile
|       |          |        ├── overview.blade.php
|       │          |        └── projects.blade.php
|       │          ├── projects
|       |          |        ├── general.blade.php
|       |          |        ├── new-project.blade.php
|       │          |        └── timeline.blade.php
|       │          ├── users
|       |          |        ├── new-user.blade.php
|       │          |        └── reports.blade.php
|       │          ├── vr
|       |          |        ├── vr-default.blade.php
|       │          |        └── vr-info.blade.php
│       |          ├── charts.blade.php
│       |          ├── notifications.blade.php
│       |          ├── pricing-page.blade.php
│       |          ├── rtl.blade.php
│       |          ├── sweet-alerts.blade.php
│       |          └── widgets.blade.php
│       ├── register
│       |          └── create.blade.php
│       └── sessions
│       |          ├── password
|       |          |        ├── reset.blade.php
|       │          |        └── verify.blade.php
│       |          └── create.blade.php
```

## Browser Support
At present, we officially aim to support the last two versions of the following browsers:

<img src="https://s3.amazonaws.com/creativetim_bucket/github/browser/chrome.png" width="64" height="64"> <img src="https://s3.amazonaws.com/creativetim_bucket/github/browser/firefox.png" width="64" height="64"> <img src="https://s3.amazonaws.com/creativetim_bucket/github/browser/edge.png" width="64" height="64"> <img src="https://s3.amazonaws.com/creativetim_bucket/github/browser/safari.png" width="64" height="64"> <img src="https://s3.amazonaws.com/creativetim_bucket/github/browser/opera.png" width="64" height="64">

## Reporting Issues
We use GitHub Issues as the official bug tracker for the Soft UI Dashboard. Here are some advices for our users that want to report an issue:

1. Make sure that you are using the latest version of the Material Dashboard. Check the CHANGELOG from your dashboard on our [website](https://www.creative-tim.com/product/material-dashboard-pro-laravel).
2. Providing us reproducible steps for the issue will shorten the time it takes for it to be fixed.
3. Some issues may be browser specific, so specifying in what browser you encountered the issue might help.

## Licensing
- Copyright 2022 [Creative Tim](https://www.creative-tim.com?ref=readme-md2pl)
- Creative Tim [license](https://www.creative-tim.com/license?ref=readme-md2pl)

## Useful Links
- [Tutorials](https://www.youtube.com/channel/UCVyTG4sCw-rOvB9oHkzZD1w)
- [Affiliate Program](https://www.creative-tim.com/affiliates/new) (earn money)
- [Blog Creative Tim](http://blog.creative-tim.com/)
- [Free Products](https://www.creative-tim.com/bootstrap-themes/free) from Creative Tim
- [Premium Products](https://www.creative-tim.com/bootstrap-themes/premium?ref=md2pl-readme) from Creative Tim
- [React Products](https://www.creative-tim.com/bootstrap-themes/react-themes?ref=md2pl-readme) from Creative Tim
- [VueJS Products](https://www.creative-tim.com/bootstrap-themes/vuejs-themes?ref=md2pl-readme) from Creative Tim
- [More products](https://www.creative-tim.com/bootstrap-themes?ref=md2pl-readme) from Creative Tim
- Check our Bundles [here](https://www.creative-tim.com/bundles??ref=md2pl-readme)

### Social Media

### Creative Tim
Twitter: <https://twitter.com/CreativeTim?ref=md2pl-readme>

Facebook: <https://www.facebook.com/CreativeTim?ref=md2pl-readme>

Dribbble: <https://dribbble.com/creativetim?ref=md2pl-readme>

Instagram: <https://www.instagram.com/CreativeTimOfficial?ref=md2pl-readme>

### Updivision:

Twitter: <https://twitter.com/updivision?ref=md2pl-readme>

Facebook: <https://www.facebook.com/updivision?ref=md2pl-readme>

Linkedin: <https://www.linkedin.com/company/updivision?ref=md2pl-readme>

Updivision Blog: <https://updivision.com/blog/?ref=md2pl-readme>

## Credits

- [Creative Tim](https://creative-tim.com/?ref=md2pl-readme)
- [UPDIVISION](https://updivision.com)
