# [Material Dashboard Pro Laravel](https://material-dashboard-pro-laravel.creative-tim.com/?ref=mdpl-readme) [![Tweet](https://img.shields.io/twitter/url/http/shields.io.svg?style=social&logo=twitter)](https://twitter.com/home?status=Material%20Dashboard%20Pro%20Laravel%E2%9D%A4%EF%B8%8F%0Ahttps%3A//material-dashboard-pro-laravel.creative-tim.com/%20%23%material%20%23design%20%23dashboard%20%23laravel%20%23pro%20via%20%40CreativeTim)

![version](https://img.shields.io/badge/version-1.0.1-blue.svg) ![license](https://img.shields.io/badge/license-MIT-blue.svg) [![GitHub issues open](https://img.shields.io/github/issues/creativetimofficial/ct-material-dashboard-pro-laravel.svg?maxAge=2592000)](https://github.com/creativetimofficial/ct-material-dashboard-pro-laravel/issues?q=is%3Aopen+is%3Aissue) [![GitHub issues closed](https://img.shields.io/github/issues-closed-raw/creativetimofficial/ct-material-dashboard-pro-laravel/ct-material-dashboard-pro-laravel.svg?maxAge=2592000)](https://github.com/creativetimofficial/ct-material-dashboard-pro-laravel/issues?q=is%3Aissue+is%3Aclosed)

*Frontend version*: Material Dashboard v2.1.0. More info at https://www.creative-tim.com/product/material-dashboard-pro

![Product Image](https://github.com/creativetimofficial/public-assets/raw/master/material-dashboard-pro-laravel/material-dashboard-pro-laravel.gif?raw=true)

Speed up your web development with the Bootstrap 4 Admin Dashboard built for Laravel Framework 5.5 and up.

## Prerequisites

If you don't already have an Apache local environment with PHP and MySQL, use one of the following links:

 - Windows: https://updivision.com/blog/post/beginner-s-guide-to-setting-up-your-local-development-environment-on-windows
 - Linux: https://howtoubuntu.org/how-to-install-lamp-on-ubuntu
 - Mac: https://wpshout.com/quick-guides/how-to-install-mamp-on-your-mac/

Also, you will need to install Composer: https://getcomposer.org/doc/00-intro.md
## Installation

1. Unzip the downloaded archive
2. Copy and paste **material-dashbaord-master** folder in your **projects** folder. Rename the folder to your project's name
3. In your terminal run `composer install`
4. Copy `.env.example` to `.env` and updated the configurations (mainly the database configuration)
5. In your terminal run `php artisan key:generate`
6. Run `php artisan migrate --seed` to create the database tables and seed the roles and users tables
7. Run `php artisan storage:link` to create the storage symlink (if you are using **Vagrant** with **Homestead** for development, remember to ssh into your virtual machine and run the command from there).

## Usage

To start testing the Pro theme, register as a user or log in using one of the default users: 

- admin type - **admin@material.com** with the password **secret**
- creator type - **creator@material.com** with the password **secret**
- member type - **member@material.com** with the password **secret**

Make sure to run the migrations and seeders for the above credentials to be available.

In addition to the features included in the free preset, the Pro theme also has a role management example with an updated user management, as well as tag management, category management and item management examples. All the necessary files (controllers, requests, views) are installed out of the box and all the needed routes are added to `routes/web.php`. Keep in mind that all the features can be viewed once you log in using the credentials provided above or by registering your own user.

Each role has a different privilege level and can perform a certain number of actions according to this level.  

A **member type** user can log in, update his profile and view a list of added items.  
A **creator type** user can log in, update his profile and perform actions on categories, tags and items.  
A **admin type** user can log in, update his profile and perform actions on categories, tags, items, roles and users.  

### Dashboard

You can access the dashboard either by using the "**Dashboards/Dashboard**" link in the left sidebar or by adding **/home** in the URL.

### Profile edit

You have the option to edit the current logged in user's profile information (name, email, profile picture) and password. To access this page, just click the "**Examples/Profile**" link in the left sidebar or add **/profile** in the URL.

The `App\Http\Controllers\ProfileController` handles the update of the user information and password.

```
public function update(ProfileRequest $request)
{
    auth()->user()->update(
        $request->merge(['picture' => $request->photo ? $request->photo->store('profile', 'public') : null])
            ->except([$request->hasFile('photo') ? '' : 'picture'])
    );

    return back()->withStatus(__('Profile successfully updated.'));
}

/**
* Change the password
*
* @param  \App\Http\Requests\PasswordRequest  $request
* @return \Illuminate\Http\RedirectResponse
*/
public function password(PasswordRequest $request)
{
    auth()->user()->update(['password' => Hash::make($request->get('password'))]);

    return back()->withStatus(__('Password successfully updated.'));
}
```

If you input the wrong data when editing the profile, don`t worry. Validation rules have been added to prevent this (see `App\Http\Requests\ProfileRequest`). If you try to change the password, you will see that additional validation rules have been added in `App\Http\Requests\PasswordRequest`. You also have  a custom validation rule that can be found in `App\Rules\CurrentPasswordCheckRule`.

```
public function rules()
{
    return [
        'old_password' => ['required', 'min:6', new CurrentPasswordCheckRule],
        'password' => ['required', 'min:6', 'confirmed', 'different:old_password'],
        'password_confirmation' => ['required', 'min:6'],
    ];
}
```

### Role management

The Pro theme allows you to add user roles. By default, the theme comes with **Admin**, **Creator** and **Member** roles. To access the role management example click the "**Examples/Role Management**" link in the left sidebar or add **/role** to the URL. Here you can add/edit new roles. Deletion is not allowed in this section.
To add a new role, click the "**Add role**" button. To edit an existing role, click the dotted menu (available on every table row) and then click "**Edit**". In both cases, you will be directed to a form which allows you to modify the name and description of a role.

The policy which authorizes the user to access the role management option is implemented in `App\Policies\RolePolicy.php`.``

You can find this functionality in `App\Http\RoleController.php`.

Also, validation rules were added so you will know exactly what to input in the form fields (see `App\Http\Requests\RoleRequest`). Note that these validation rules also apply for the role edit option.
```
public function rules()
{
    return [
        'name' => [
            'required', 'min:3', Rule::unique((new Role)->getTable())->ignore($this->route()->role->id ?? null)
        ],
        'description' => [
            'nullable', 'min:5'
        ]
    ];
}
```

### User management

The theme comes with an out of the box user management option. To access this option ,click the "**Examples/User Management**" link in the left sidebar or add **/user** to the URL.
The first thing you will see is a list of existing users. You can add new ones by clicking the "**Add user**" button (above the table on the right). On the Add user page, you will find a form which allows you to fill out the user`s name, email, role and password. All pages are generated using blade templates:

```
<div class="row">
  <label class="col-sm-2 col-form-label">{{ __('Name') }}</label>
  <div class="col-sm-7">
    <div class="form-group{{ $errors->has('name') ? ' has-danger' : '' }}">
      <input class="form-control{{ $errors->has('name') ? ' is-invalid' : '' }}" name="name" id="input-name" type="text" placeholder="{{ __('Name') }}" value="{{ old('name') }}" required="true" aria-required="true"/>
      @include('alerts.feedback', ['field' => 'name'])
    </div>
  </div>
</div>
```

Validation rules were added to prevent errors in the form fields (see `App\Http\Requests\UserRequest`). Note that these validation rules also apply for the user edit option.

```
public function rules()
{
    return [
        'name' => [
            'required', 'min:3'
        ],
        'email' => [
            'required', 'email', Rule::unique((new User)->getTable())->ignore($this->route()->user->id ?? null)
        ],
        'role_id' => [
            'required', 'exists:'.(new Role)->getTable().',id'
        ],
        'password' => [
            $this->route()->user ? 'nullable' : 'required', 'confirmed', 'min:6'
        ]
    ];
}

/**
* Get the validation attributes that apply to the request.
*
* @return array
*/
public function attributes()
{
    return [
        'role_id' => 'role',
    ];
}
```

The policy which authorizes the user to access the user management pages is implemented in `App\Policies\UserPolicy.php`.``

Once you add more users, the list will grow and for every user you will have edit and delete options (access these options by clicking the three dotted menu that appears at the end of every row).

All the sample code for the user management can be found in `App\Http\Controllers\UserController`. See store method example bellow:

```
public function store(UserRequest $request, User $model)
{
    $model->create($request->merge([
        'picture' => $request->photo ? $request->photo->store('profile', 'public') : null,
        'password' => Hash::make($request->get('password'))
    ])->all());

    return redirect()->route('user.index')->withStatus(__('User successfully created.'));
}
```

### Tag management

The Pro theme also comes with a tag management option. To access this example, click the "**Examples/Tag Management**" link in the left sidebar or add **/tag** to the URL.
In this section you can add and edit tags, but you can only delete them if they are not attached to any items. You can add new ones by clicking the "**Add tag**" button (above the table on the right). You will then be directed to a form which allows you to add new tags.
Although you can add in the form only the name and color of a tag, you can write your own migrations to extend this functionality.

```
public function destroy(Tag $tag)
{
    if (!$tag->items->isEmpty()) {
        return redirect()->route('tag.index')->withErrors(__('This tag has items attached and can\'t be deleted.'));
    }

    $tag->delete();

    return redirect()->route('tag.index')->withStatus(__('Tag successfully deleted.'));
}
```

The policy which authorizes the user to access tags management pages is implemented in `App\Policies\TagPolicy.php`.

### Category management

Out of the box you will have an example of category management (for the cases in which you are developing a blog or a shop). To access this example, click the "**Examples/Category Management**" link in the left sidebar or add **/category** to the URL.
You can add and edit categories here, but you can only delete them if they are not attached to any items.

```
@if ($category->items->isEmpty() && auth()->user()->can('delete', $category))
    <button type="button" class="btn btn-danger btn-link" data-original-title="" title="" onclick="confirm('{{ __("Are you sure you want to delete this category?") }}') ? this.parentElement.submit() : ''">
        <i class="material-icons">close</i>
        <div class="ripple-container"></div>
    </button>
@endif
```

The policy which authorizes the user on categories management pages is implemented in `App\Policies\CategoryPolicy.php`.

### Item management

Item management is the most advanced example included in the Pro theme, because every item has a picture, belongs to a category and has multiple tags. To access this example click the "**Examples/Item Management**" link in the left sidebar or add **/item** to the URL.
Here you can manage the items. A list of items will appear once you start adding them (to access the add page click "**Add item**").
On the add page, besides the Name and Description fields (which are present in most of the CRUD examples) you can see a category dropdown, which contains the categories you added, a file input and a tag multi select. If you did not add any categories or tags, please go to the corresponding sections (category management, tag management) and add some.  


The code for saving a new item is a bit different than before (see snippet bellow):

```
public function store(ItemRequest $request, Item $model)
{
    $item = $model->create($request->merge([
        'picture' => $request->photo->store('pictures', 'public'),
        'show_on_homepage' => $request->show_on_homepage ? 1 : 0,
        'options' => $request->options ? $request->options : null,
        'date' => $request->date ? Carbon::parse($request->date)->format('Y-m-d') : null
    ])->all());

    $item->tags()->sync($request->get('tags'));

    return redirect()->route('item.index')->withStatus(__('Item successfully created.'));
}
```

Notice how the picture and tags are easily saved in the database and on the disk.

Similar to all the examples included in the theme, this one also has validation rules in place. Note that the picture is mandatory only on the item creation. On the edit page, if no new picture is added, the old picture will not be modified.

```
public function rules()
{
    return [
        'name' => [
            'required', 'min:3', Rule::unique((new Item)->getTable())->ignore($this->route()->item->id ?? null)
        ],
        'category_id' => [
            'required', 'exists:'.(new Category)->getTable().',id'
        ],
        'description' => [
            'required'
        ],
        'photo' => [
            $this->route()->item ? 'nullable' : 'required', 'image'
        ],
        'tags' => [
            'required'
        ],
        'tags.*' => [
            'exists:'.(new Tag)->getTable().',id'
        ],
        'status' => [
            'required',
            'in:published,draft,archive'
        ],
        'date' => [
            'required',
            'date_format:d-m-Y'
        ]
    ];
}
```

In the item management we have an **observer** (`app\Observers\ItemObserver`) example. This observer handles the deletion of the picture from the disk when the item is deleted or when the picture is changed via the edit form. The **observer** also removes the association between the item and the tags.

```
public function deleting(Item  $item)
{
    File::delete(storage_path("/app/public/{$item->picture}"));
    
    $item->tags()->detach();
}
```

The policy which authorizes the user on item management pages is implemented in `App\Policies\ItemPolicy.php`.

## Table of Contents

* [Versions](#versions)
* [Demo](#demo)
* [Documentation](#documentation)
* [File Structure](#file-structure)
* [Browser Support](#browser-support)
* [Resources](#resources)
* [Reporting Issues](#reporting-issues)
* [Licensing](#licensing)
* [Useful Links](#useful-links)

## Versions

[<img src="https://github.com/creativetimofficial/public-assets/blob/master/logos/html-logo.jpg?raw=true" width="60" height="60" />](https://demos.creative-tim.com/argon-dashboard-pro/pages/dashboards/dashboard.html?ref=mdl-readme)
[<img src="https://github.com/creativetimofficial/public-assets/blob/master/logos/laravel_logo.png?raw=true" width="60" height="60" />](https://argon-dashboard-pro-laravel.creative-tim.com/?ref=mdl-readme)

| HTML | LARAVEL |
| --- | --- |
| [![Material Dashboard Pro HTML](https://s3.amazonaws.com/creativetim_bucket/products/51/thumb/opt_mdp_thumbnail.jpg?1521134752)](https://demos.creative-tim.com/material-dashboard-pro/examples/dashboard.html?ref=mdl-readme) | [![Material Dashboard Pro Laravel](https://s3.amazonaws.com/creativetim_bucket/products/158/thumb/opt_mdp_laravel_thumbnail.jpg)](https://material-dashboard-pro-laravel.creative-tim.com/?ref=mdl-readme)

## Demo

| Register | Login | Dashboard |
| --- | --- | ---  |
| [![Register](https://github.com/creativetimofficial/public-assets/raw/master/material-dashboard-pro-laravel/Register.png)](https://material-dashboard-pro-laravel.creative-tim.com/register?ref=mdl-readme)  | [![Login](https://github.com/creativetimofficial/public-assets/raw/master/material-dashboard-pro-laravel/Login.png)](https://material-dashboard-pro-laravel.creative-tim.com/login?ref=mdl-readme)  | [![Dashboard](https://github.com/creativetimofficial/public-assets/raw/master/material-dashboard-pro-laravel/Dashboard.png)](https://material-dashboard-pro-laravel.creative-tim.com/?ref=mdl-readme)

| Profile Page | Users Page | Tables Page  |
| --- | --- | ---  |
| [![Profile Page](https://github.com/creativetimofficial/public-assets/raw/master/material-dashboard-pro-laravel/Profile.png)](https://material-dashboard-pro-laravel.creative-tim.com/profile?ref=mdl-readme)  | [![Users Page](https://github.com/creativetimofficial/public-assets/raw/master/material-dashboard-pro-laravel/Users.png)](https://material-dashboard-pro-laravel.creative-tim.com/user?ref=mdl-readme) | [![Tables Page](https://github.com/creativetimofficial/public-assets/raw/master/material-dashboard-pro-laravel/Tables.png)](https://material-dashboard-pro-laravel.creative-tim.com/table-list?ref=mdl-readme)
[View More](https://material-dashboard-pro-laravel.creative-tim.com/?ref=mdl-readme)

## Documentation
The documentation for the Material Dashboard Laravel is hosted at our [website](https://material-dashboard-pro-laravel.creative-tim.com/docs/getting-started/laravel-setup.html?ref=mdpl-readme).

## File Structure
```
|   artisan
|   composer.json
|   composer.lock
|   package.json
|   phpunit.xml
|   README.md
|   server.php
|   yarn.lock
|   
+---app
|   |   Category.php
|   |   Item.php
|   |   Role.php
|   |   Tag.php
|   |   User.php
|   |   
|   +---Console
|   |       Kernel.php
|   |       
|   +---Exceptions
|   |       Handler.php
|   |       
|   +---Http
|   |   |   Kernel.php
|   |   |   
|   |   +---Controllers
|   |   |   |   CategoryController.php
|   |   |   |   ComponentPagesController.php
|   |   |   |   Controller.php
|   |   |   |   ExamplePagesController.php
|   |   |   |   FormPagesController.php
|   |   |   |   HomeController.php
|   |   |   |   ItemController.php
|   |   |   |   MapPagesController.php
|   |   |   |   ProfileController.php
|   |   |   |   RoleController.php
|   |   |   |   TablePagesController.php
|   |   |   |   TagController.php
|   |   |   |   UserController.php
|   |   |   |   
|   |   |   \---Auth
|   |   |           ForgotPasswordController.php
|   |   |           LoginController.php
|   |   |           RegisterController.php
|   |   |           ResetPasswordController.php
|   |   |           VerificationController.php
|   |   |           
|   |   +---Middleware
|   |   |       Authenticate.php
|   |   |       CheckForMaintenanceMode.php
|   |   |       EncryptCookies.php
|   |   |       RedirectIfAuthenticated.php
|   |   |       TrimStrings.php
|   |   |       TrustProxies.php
|   |   |       VerifyCsrfToken.php
|   |   |       
|   |   \---Requests
|   |           CategoryRequest.php
|   |           ItemRequest.php
|   |           PasswordRequest.php
|   |           ProfileRequest.php
|   |           RoleRequest.php
|   |           TagRequest.php
|   |           UserRequest.php
|   |           
|   +---Observers
|   |       ItemObserver.php
|   |       UserObserver.php
|   |       
|   +---Policies
|   |       CategoryPolicy.php
|   |       ItemPolicy.php
|   |       RolePolicy.php
|   |       TagPolicy.php
|   |       UserPolicy.php
|   |       
|   +---Providers
|   |       AppServiceProvider.php
|   |       AuthServiceProvider.php
|   |       BroadcastServiceProvider.php
|   |       EventServiceProvider.php
|   |       RouteServiceProvider.php
|   |       
|   \---Rules
|           CurrentPasswordCheckRule.php
|           
+---config
|       app.php
|       auth.php
|       broadcasting.php
|       cache.php
|       database.php
|       filesystems.php
|       hashing.php
|       items.php
|       logging.php
|       mail.php
|       queue.php
|       services.php
|       session.php
|       view.php
|       
+---database
|   |   
|   |   
|   +---factories
|   |       UserFactory.php
|   |       
|   +---migrations
|   |       2014_10_12_100000_create_password_resets_table.php
|   |       2019_01_15_100000_create_roles_table.php
|   |       2019_01_15_110000_create_users_table.php
|   |       2019_01_17_121504_create_categories_table.php
|   |       2019_01_21_130422_create_tags_table.php
|   |       2019_01_21_163402_create_items_table.php
|   |       2019_01_21_163414_create_item_tag_table.php
|   |       2019_03_06_132557_add_photo_column_to_users_table.php
|   |       2019_03_06_143255_add_fields_to_items_table.php
|   |       2019_03_20_090438_add_color_tags_table.php
|   |       
|   \---seeds
|           CategoriesTableSeeder.php
|           DatabaseSeeder.php
|           ItemsTableSeeder.php
|           RolesTableSeeder.php
|           TagsTableSeeder.php
|           UsersTableSeeder.php
|           
+---public
|   |   .htaccess
|   |   favicon.ico
|   |   index.php
|   |   
|   +---css
|   |       app.css
|   |       
|   +---js
|   |       app.js
|   |       
|   +---material
|   |   +---css
|   |   |   |   material-dashboard.css
|   |   |   |   material-dashboard.css.map
|   |   |   |   material-dashboard.min.css
|   |   |   |   
|   |   |   \---partials
|   |   |       +---dashboard
|   |   |       |   \---core
|   |   |       |       \---bootstrap
|   |   |       |           \---scss
|   |   |       |                   bootstrap-grid.css
|   |   |       |                   bootstrap-grid.css.map
|   |   |       |                   bootstrap-reboot.css
|   |   |       |                   bootstrap-reboot.css.map
|   |   |       |                   bootstrap.css
|   |   |       |                   bootstrap.css.map
|   |   |       |                   
|   |   |       \---kit
|   |   |           \---core
|   |   |               \---bootstrap
|   |   |                   \---scss
|   |   |                           bootstrap-grid.css
|   |   |                           bootstrap-grid.css.map
|   |   |                           bootstrap-reboot.css
|   |   |                           bootstrap-reboot.css.map
|   |   |                           bootstrap.css
|   |   |                           bootstrap.css.map
|   |   |                           
|   |   +---demo
|   |   |       demo.css
|   |   |       demo.js
|   |   |       
|   |   +---img
|   |   |   |   apple-icon.png
|   |   |   |   bg-pricing.jpg
|   |   |   |   bg3.jpg
|   |   |   |   bg9.jpg
|   |   |   |   card-1.jpeg
|   |   |   |   card-1.jpg
|   |   |   |   card-2.jpeg
|   |   |   |   card-2.jpg
|   |   |   |   card-3.jpeg
|   |   |   |   card-3.jpg
|   |   |   |   clint-mckoy.jpg
|   |   |   |   default-avatar.png
|   |   |   |   favicon.png
|   |   |   |   header-doc.jpg
|   |   |   |   image_placeholder.jpg
|   |   |   |   laravel.svg
|   |   |   |   lock.jpg
|   |   |   |   login.jpg
|   |   |   |   mask.png
|   |   |   |   new_logo.png
|   |   |   |   placeholder.jpg
|   |   |   |   product1.jpg
|   |   |   |   product2.jpg
|   |   |   |   product3.jpg
|   |   |   |   register.jpg
|   |   |   |   sidebar-1.jpg
|   |   |   |   sidebar-2.jpg
|   |   |   |   sidebar-3.jpg
|   |   |   |   sidebar-4.jpg
|   |   |   |   
|   |   |   +---faces
|   |   |   |       avatar.jpg
|   |   |   |       card-profile1-square.jpg
|   |   |   |       card-profile2-square.jpg
|   |   |   |       marc.jpg
|   |   |   |       
|   |   |   \---flags
|   |   |           AU.png
|   |   |           BR.png
|   |   |           DE.png
|   |   |           GB.png
|   |   |           RO.png
|   |   |           US.png
|   |   |           
|   |   +---js
|   |   |   |   application.js
|   |   |   |   material-dashboard.js
|   |   |   |   material-dashboard.js.map
|   |   |   |   material-dashboard.min.js
|   |   |   |   
|   |   |   +---core
|   |   |   |       bootstrap-material-design.min.js
|   |   |   |       jquery.min.js
|   |   |   |       popper.min.js
|   |   |   |       
|   |   |   \---plugins
|   |   |           arrive.min.js
|   |   |           bootstrap-datetimepicker.min.js
|   |   |           bootstrap-notify.js
|   |   |           bootstrap-selectpicker.js
|   |   |           bootstrap-tagsinput.js
|   |   |           chartist.min.js
|   |   |           fullcalendar.min.js
|   |   |           jasny-bootstrap.min.js
|   |   |           jquery-jvectormap.js
|   |   |           jquery.bootstrap-wizard.js
|   |   |           jquery.dataTables.min.js
|   |   |           jquery.tagsinput.js
|   |   |           jquery.validate.min.js
|   |   |           moment.min.js
|   |   |           nouislider.min.js
|   |   |           perfect-scrollbar.jquery.min.js
|   |   |           sweetalert2.js
|   |   |           
|   |   \---scss
|   |       |   material-dashboard.scss
|   |       |   
|   |       \---material-dashboard
|   |           |   _alerts.scss
|   |           |   _badges.scss
|   |           |   _buttons.scss
|   |           |   _cards.scss
|   |           |   _checkboxes.scss
|   |           |   _core-bootstrap.scss
|   |           |   _dropdown.scss
|   |           |   _example-pages.scss
|   |           |   _fixed-plugin.scss
|   |           |   _footers-extend.scss
|   |           |   _footers.scss
|   |           |   _forms-extend.scss
|   |           |   _forms.scss
|   |           |   _headers.scss
|   |           |   _images.scss
|   |           |   _info-areas.scss
|   |           |   _input-group.scss
|   |           |   _misc-extend.scss
|   |           |   _misc.scss
|   |           |   _mixins.scss
|   |           |   _modal.scss
|   |           |   _navbar.scss
|   |           |   _pages.scss
|   |           |   _pagination.scss
|   |           |   _pills.scss
|   |           |   _popover.scss
|   |           |   _popups.scss
|   |           |   _progress.scss
|   |           |   _radios.scss
|   |           |   _responsive.scss
|   |           |   _ripples.scss
|   |           |   _rtl.scss
|   |           |   _sidebar-and-main-panel.scss
|   |           |   _social-buttons.scss
|   |           |   _tables.scss
|   |           |   _tabs.scss
|   |           |   _timeline.scss
|   |           |   _togglebutton.scss
|   |           |   _tooltip.scss
|   |           |   _type.scss
|   |           |   _variables.scss
|   |           |   
|   |           +---bootstrap
|   |           |   \---scss
|   |           |       |   bootstrap-grid.scss
|   |           |       |   bootstrap-reboot.scss
|   |           |       |   bootstrap.scss
|   |           |       |   _alert.scss
|   |           |       |   _badge.scss
|   |           |       |   _breadcrumb.scss
|   |           |       |   _button-group.scss
|   |           |       |   _buttons.scss
|   |           |       |   _card.scss
|   |           |       |   _carousel.scss
|   |           |       |   _close.scss
|   |           |       |   _code.scss
|   |           |       |   _custom-forms.scss
|   |           |       |   _dropdown.scss
|   |           |       |   _forms.scss
|   |           |       |   _functions.scss
|   |           |       |   _grid.scss
|   |           |       |   _images.scss
|   |           |       |   _input-group.scss
|   |           |       |   _jumbotron.scss
|   |           |       |   _list-group.scss
|   |           |       |   _media.scss
|   |           |       |   _mixins.scss
|   |           |       |   _modal.scss
|   |           |       |   _nav.scss
|   |           |       |   _navbar.scss
|   |           |       |   _pagination.scss
|   |           |       |   _popover.scss
|   |           |       |   _print.scss
|   |           |       |   _progress.scss
|   |           |       |   _reboot.scss
|   |           |       |   _root.scss
|   |           |       |   _tables.scss
|   |           |       |   _tooltip.scss
|   |           |       |   _transitions.scss
|   |           |       |   _type.scss
|   |           |       |   _utilities.scss
|   |           |       |   _variables.scss
|   |           |       |   
|   |           |       +---mixins
|   |           |       |       _alert.scss
|   |           |       |       _background-variant.scss
|   |           |       |       _badge.scss
|   |           |       |       _border-radius.scss
|   |           |       |       _box-shadow.scss
|   |           |       |       _breakpoints.scss
|   |           |       |       _buttons.scss
|   |           |       |       _caret.scss
|   |           |       |       _clearfix.scss
|   |           |       |       _float.scss
|   |           |       |       _forms.scss
|   |           |       |       _gradients.scss
|   |           |       |       _grid-framework.scss
|   |           |       |       _grid.scss
|   |           |       |       _hover.scss
|   |           |       |       _image.scss
|   |           |       |       _list-group.scss
|   |           |       |       _lists.scss
|   |           |       |       _nav-divider.scss
|   |           |       |       _navbar-align.scss
|   |           |       |       _pagination.scss
|   |           |       |       _reset-text.scss
|   |           |       |       _resize.scss
|   |           |       |       _screen-reader.scss
|   |           |       |       _size.scss
|   |           |       |       _table-row.scss
|   |           |       |       _text-emphasis.scss
|   |           |       |       _text-hide.scss
|   |           |       |       _text-truncate.scss
|   |           |       |       _transition.scss
|   |           |       |       _visibility.scss
|   |           |       |       
|   |           |       \---utilities
|   |           |               _align.scss
|   |           |               _background.scss
|   |           |               _borders.scss
|   |           |               _clearfix.scss
|   |           |               _display.scss
|   |           |               _embed.scss
|   |           |               _flex.scss
|   |           |               _float.scss
|   |           |               _position.scss
|   |           |               _screenreaders.scss
|   |           |               _sizing.scss
|   |           |               _spacing.scss
|   |           |               _text.scss
|   |           |               _visibility.scss
|   |           |               
|   |           +---cards
|   |           |       _card-background.scss
|   |           |       _card-blog.scss
|   |           |       _card-collapse.scss
|   |           |       _card-contact.scss
|   |           |       _card-form-horizontal.scss
|   |           |       _card-plain-extend.scss
|   |           |       _card-plain.scss
|   |           |       _card-pricing.scss
|   |           |       _card-product.scss
|   |           |       _card-profile.scss
|   |           |       _card-rotate.scss
|   |           |       _card-signup.scss
|   |           |       _card-stats.scss
|   |           |       _card-testimonials.scss
|   |           |       
|   |           +---mixins
|   |           |       _alert.scss
|   |           |       _animations.scss
|   |           |       _breakpoints.scss
|   |           |       _buttons.scss
|   |           |       _chartist.scss
|   |           |       _colored-shadows.scss
|   |           |       _drawer.scss
|   |           |       _forms.scss
|   |           |       _hover.scss
|   |           |       _layout.scss
|   |           |       _navbar-colors.scss
|   |           |       _navs.scss
|   |           |       _sidebar-color.scss
|   |           |       _social-buttons.scss
|   |           |       _transparency.scss
|   |           |       _type.scss
|   |           |       _utilities.scss
|   |           |       _variables.scss
|   |           |       _vendor-prefixes.scss
|   |           |       
|   |           +---plugins
|   |           |       _animate.scss
|   |           |       _chartist.scss
|   |           |       _datatables.net.scss
|   |           |       _fullcalendar.scss
|   |           |       _jquery.jvectormap.scss
|   |           |       _perfect-scrollbar.scss
|   |           |       _plugin-bootstrap-select.scss
|   |           |       _plugin-datetime-picker.scss
|   |           |       _plugin-fileupload.scss
|   |           |       _plugin-flexisel.scss
|   |           |       _plugin-nouislider.scss
|   |           |       _plugin-tagsinput.scss
|   |           |       _sweetalert2.scss
|   |           |       _wizard-card.scss
|   |           |       
|   |           \---variables
|   |                   _body.scss
|   |                   _bootstrap-material-design-base.scss
|   |                   _bootstrap-material-design.scss
|   |                   _brand.scss
|   |                   _buttons.scss
|   |                   _card.scss
|   |                   _code.scss
|   |                   _colors-map.scss
|   |                   _colors.scss
|   |                   _custom-forms.scss
|   |                   _drawer.scss
|   |                   _dropdown.scss
|   |                   _forms.scss
|   |                   _layout.scss
|   |                   _list-group.scss
|   |                   _menu.scss
|   |                   _modals.scss
|   |                   _nav.scss
|   |                   _pagination.scss
|   |                   _shadow.scss
|   |                   _snackbar.scss
|   |                   _spacing.scss
|   |                   _state.scss
|   |                   _tables.scss
|   |                   _tooltip.scss
|   |                   _type.scss
|   |                   
|   \---storage
|       |   
|       +---pictures
|       |       
|       \---profile
|               
+---resources
|   +---lang
|   |   \---en
|   |           auth.php
|   |           pagination.php
|   |           passwords.php
|   |           validation.php
|   |           
|   \---views
|       |   home.blade.php
|       |   
|       +---alerts
|       |       errors.blade.php
|       |       feedback.blade.php
|       |       migrations_check.blade.php
|       |       
|       +---auth
|       |   |   login.blade.php
|       |   |   register.blade.php
|       |   |   verify.blade.php
|       |   |   
|       |   \---passwords
|       |           email.blade.php
|       |           reset.blade.php
|       |           
|       +---categories
|       |       create.blade.php
|       |       edit.blade.php
|       |       index.blade.php
|       |       
|       +---errors
|       |       401.blade.php
|       |       403.blade.php
|       |       404.blade.php
|       |       419.blade.php
|       |       429.blade.php
|       |       500.blade.php
|       |       503.blade.php
|       |       layout.blade.php
|       |       
|       +---items
|       |       create.blade.php
|       |       edit.blade.php
|       |       index.blade.php
|       |       
|       +---layouts
|       |   |   app.blade.php
|       |   |   
|       |   +---footers
|       |   |       auth.blade.php
|       |   |       guest.blade.php
|       |   |       
|       |   +---navbars
|       |   |   |   sidebar.blade.php
|       |   |   |   
|       |   |   \---navs
|       |   |           auth.blade.php
|       |   |           guest.blade.php
|       |   |           
|       |   \---page_templates
|       |           auth.blade.php
|       |           guest.blade.php
|       |           
|       +---pages
|       |   |   calendar.blade.php
|       |   |   charts.blade.php
|       |   |   dashboard.blade.php
|       |   |   welcome.blade.php
|       |   |   widgets.blade.php
|       |   |   
|       |   +---components
|       |   |       buttons.blade.php
|       |   |       grid.blade.php
|       |   |       icons.blade.php
|       |   |       notifications.blade.php
|       |   |       panels.blade.php
|       |   |       sweet_alert.blade.php
|       |   |       typography.blade.php
|       |   |       
|       |   +---example_pages
|       |   |       error.blade.php
|       |   |       language.blade.php
|       |   |       lock.blade.php
|       |   |       pricing.blade.php
|       |   |       timeline.blade.php
|       |   |       
|       |   +---forms
|       |   |       form_extended.blade.php
|       |   |       form_regular.blade.php
|       |   |       form_validation.blade.php
|       |   |       form_wizard.blade.php
|       |   |       
|       |   +---maps
|       |   |       maps_fullscreen.blade.php
|       |   |       maps_google.blade.php
|       |   |       maps_vector.blade.php
|       |   |       
|       |   \---tables
|       |           tables_datatable.blade.php
|       |           tables_extended.blade.php
|       |           tables_regular.blade.php
|       |           table_list.blade.php
|       |           
|       +---profile
|       |       edit.blade.php
|       |       
|       +---roles
|       |       create.blade.php
|       |       edit.blade.php
|       |       index.blade.php
|       |       
|       +---tags
|       |       create.blade.php
|       |       edit.blade.php
|       |       index.blade.php
|       |       
|       \---users
|               create.blade.php
|               edit.blade.php
|               index.blade.php
|               
+---routes
|       web.php
|       
+---storage
|   +---app
|   |   |   
|   |   |   
|   |   \---public
|   |       |   
|   |       +---pictures
|   |       |       
|   |       \---profile
```

## Browser Support

At present, we officially aim to support the last two versions of the following browsers:

<img src="https://github.com/creativetimofficial/public-assets/blob/master/logos/chrome-logo.png?raw=true" width="64" height="64"> <img src="https://raw.githubusercontent.com/creativetimofficial/public-assets/master/logos/firefox-logo.png" width="64" height="64"> <img src="https://raw.githubusercontent.com/creativetimofficial/public-assets/master/logos/edge-logo.png" width="64" height="64"> <img src="https://raw.githubusercontent.com/creativetimofficial/public-assets/master/logos/safari-logo.png" width="64" height="64"> <img src="https://raw.githubusercontent.com/creativetimofficial/public-assets/master/logos/opera-logo.png" width="64" height="64">


## Resources
- Demo: <https://material-dashboard-pro-laravel.creative-tim.com/?ref=mdl-readme>
- Download Page: <https://www.creative-tim.com/product/material-dashboard-pro-laravel?ref=mdl-readme>
- Documentation: <https://material-dashboard-pro-laravel.creative-tim.com/docs/getting-started/laravel-setup.html?ref=mdl-readme>
- License Agreement: <https://www.creative-tim.com/license>
- Support: <https://www.creative-tim.com/contact-us>
- Issues: [Github Issues Page](https://github.com/creativetimofficial/material-dashboard-pro-laravel/issues)
- **Dashboards:**

| HTML | LARAVEL |
| --- | --- |
| [![Material Dashboard Pro HTML](https://s3.amazonaws.com/creativetim_bucket/products/51/thumb/opt_mdp_thumbnail.jpg?1521134752)](https://demos.creative-tim.com/material-dashboard-pro/examples/dashboard.html?ref=mdl-readme) | [![Material Dashboard Pro Laravel](https://s3.amazonaws.com/creativetim_bucket/products/158/thumb/opt_mdp_laravel_thumbnail.jpg)](https://material-dashboard-pro-laravel.creative-tim.com/?ref=mdl-readme)

## Change log

Please see the [changelog](CHANGELOG.md) for more information on what has changed recently.

## Credits

- [Creative Tim](https://creative-tim.com/?ref=mdl-readme)
- [UPDIVISION](https://updivision.com)

## Reporting Issues

We use GitHub Issues as the official bug tracker for the Material Dashboard Laravel. Here are some advices for our users that want to report an issue:

1. Make sure that you are using the latest version of the Material Dashboard Laravel. Check the CHANGELOG from your dashboard on our [website](https://www.creative-tim.com/?ref=mdl-readme).
2. Providing us reproducible steps for the issue will shorten the time it takes for it to be fixed.
3. Some issues may be browser specific, so specifying in what browser you encountered the issue might help.

## Licensing

- Copyright 2019 Creative Tim (https://www.creative-tim.com/?ref=mdl-readme)
- [Creative Tim License](https://www.creative-tim.com/license).


## Useful Links

- [Tutorials](https://www.youtube.com/channel/UCVyTG4sCw-rOvB9oHkzZD1w)
- [Affiliate Program](https://www.creative-tim.com/affiliates/new) (earn money)
- [Blog Creative Tim](http://blog.creative-tim.com/)
- [Free Products](https://www.creative-tim.com/bootstrap-themes/free) from Creative Tim
- [Premium Products](https://www.creative-tim.com/bootstrap-themes/premium?ref=mdl-readme) from Creative Tim
- [React Products](https://www.creative-tim.com/bootstrap-themes/react-themes?ref=mdl-readme) from Creative Tim
- [Angular Products](https://www.creative-tim.com/bootstrap-themes/angular-themes?ref=mdl-readme) from Creative Tim
- [VueJS Products](https://www.creative-tim.com/bootstrap-themes/vuejs-themes?ref=mdl-readme) from Creative Tim
- [More products](https://www.creative-tim.com/bootstrap-themes?ref=mdl-readme) from Creative Tim
- Check our Bundles [here](https://www.creative-tim.com/bundles??ref=mdl-readme)

## Social Media

### Creative Tim:

Twitter: <https://twitter.com/CreativeTim?ref=mdl-readme>

Facebook: <https://www.facebook.com/CreativeTim?ref=mdl-readme>

Dribbble: <https://dribbble.com/creativetim?ref=mdl-readme>

Instagram: <https://www.instagram.com/CreativeTimOfficial?ref=mdl-readme>


### Updivision:

Twitter: <https://twitter.com/updivision?ref=mdl-readme>

Facebook: <https://www.facebook.com/updivision?ref=mdl-readme>

Linkedin: <https://www.linkedin.com/company/updivision?ref=mdl-readme>

Updivision Blog: <https://updivision.com/blog/?ref=mdl-readme>

## Credits

- [Creative Tim](https://creative-tim.com/?ref=mdpl-readme)
- [UPDIVISION](https://updivision.com)
