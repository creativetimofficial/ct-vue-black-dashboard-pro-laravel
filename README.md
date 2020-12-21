# [Vue Black Dashboard Pro Laravel](https://www.creative-tim.com/product/vue-black-dashboard-pro-laravel)

![version](https://img.shields.io/badge/version-1.0.0-blue.svg) [![GitHub issues open](https://img.shields.io/github/issues/creativetimofficial/ct-vue-black-dashboard-pro-laravel.svg?maxAge=2592000)](https://github.com/creativetimofficial/ct-vue-black-dashboard-pro-laravel/issues?q=is%3Aopen+is%3Aissue) [![GitHub issues closed](https://img.shields.io/github/issues-closed-raw/creativetimofficial/ct-vue-black-dashboard-pro-laravel/ct-vue-black-dashboard-pro-laravel.svg?maxAge=2592000)](https://github.com/creativetimofficial/ct-vue-black-dashboard-pro-laravel/issues?q=is%3Aissue+is%3Aclosed)

_Vue version_: Vue Black Dashboard v1.2.3. More info at https://www.creative-tim.com/product/vue-black-dashboard-pro

![Product Image](https://raw.githubusercontent.com/creativetimofficial/public-assets/master/vue-black-dashboard-laravel-pro/intro.gif)

What if you could go from frontend to fullstack in an instant when building your app? We partnered with [UPDIVISION](https://updivision.com) to bring you Vue Black Dashboard PRO , the ultimate fullstack resource. Vue Black Dashboard PRO comes not only with a huge number of UI components and a Vue Black frontend, but also with an API-powered Laravel backend.

# Download

For the PRO version of the project you will download the .zip file from the Creative Tim site and extract it.

You will get two project folders: one for the Laravel API project and one for the Vue frontend.

# Laravel API Setup

## Introduction

JSON:API is a specification for how a client should request that resources be fetched or modified, and how a server should respond to those requests. It is designed to minimize both the number of requests and the amount of data transmitted between clients and servers. This efficiency is achieved without compromising readability, flexibility, or discoverability.

[Click here to go to the JSON:API docs](https://explore.postman.com/api/6357/laravel-jsonapi)

## Prerequisites

The Laravel JSON:API project requires a working Apache/Nginx local environment with PHP, Composer and MySQL.

If you don't already have a local development environment, use one of the following links:

- Windows: [How to install WAMP on Windows](https://updivision.com/blog/post/beginner-s-guide-to-setting-up-your-local-development-environment-on-windows)
- Linux: [How to install LAMP on Linux](https://howtoubuntu.org/how-to-install-lamp-on-ubuntu)
- Mac: [How to install MAMP on MAC](https://wpshout.com/quick-guides/how-to-install-mamp-on-your-mac/)
- Install Composer: [https://getcomposer.org/doc/00-intro.md](https://getcomposer.org/doc/00-intro.md)

Install Composer: https://getcomposer.org/doc/00-intro.md

Install Node: https://nodejs.org/ (version 8.11.0+ recommended)

Install NPM: https://www.npmjs.com/get-npm

Install VueCLI: https://cli.vuejs.org/guide/installation.html

## Laravel API Project Installation

1. Navigate in your Laravel API project folder: `cd your-laravel-json-api-project`
2. Install project dependencies: `composer install`
3. Create a new .env file: `cp .env.example .env`
4. Add your own database credentials in the .env file in DB_DATABASE, DB_USERNAME, DB_PASSWORD
5. Create users table: `php artisan migrate --seed`
6. Generate application key: `php artisan key:generate`
7. Install Laravel Passport: `php artisan passport:install`
8. Add your own mailtrap.io credentials in MAIL_USERNAME and MAIL_PASSWORD in the .env file

## Vue Black Dashboard Project Installation

1. Navigate to your Vue Black Dashboard project folder: `cd your-vue-black-dashboard-project`
2. Install project dependencies: `npm install`
3. Create a new .env file: `cp .env.example .env`
4. `VUE_APP_BASE_URL` should contain the URL of your Vue Black Dashboard Project (eg. http://localhost:8080/)
5. `VUE_API_BASE_URL` should contain the URL of your Laravel JSON:API Project. (eg. http://localhost:3000/api/v1)
6. Run `npm run dev` to start the application in a local development environment or `npm run build` to build release distributables.

## Usage

To start testing the Pro theme, register as a user or log in using one of the default users:

- admin type - **admin@jsonapi.com** with the password **secret**
- creator type - **creator@jsonapi.com** with the password **secret**
- member type - **member@jsonapi.com** with the password **secret**

In addition to the features included in the free theme, the Pro theme also has a role management example with an updated user management, as well as tag management, category management and item management examples. All the necessary files are installed out of the box and all the needed routes are added to `src\router\routes.js`. Keep in mind that all the features can be viewed once you log in using the credentials provided above or by registering your own user.

Each role has a different privilege level and can perform a certain number of actions according to this level.

A **member type** user can log in, update his profile and view a list of added items.
A **creator type** user can log in, update his profile and perform actions on categories, tags and items.
A **admin type** user can log in, update his profile and perform actions on categories, tags, items, roles and users.

### Dashboard

You can access the dashboard either by using the "**Dashboards/Dashboard**" link in the left sidebar or by adding **/dashboard** in the URL.

### Login

The login functionality is fully implemented in our theme helping you to start your project in no time. To login into dashboard you just have to add **/login** in the URL and fill the login form with one of the credentials (user: **admin@jsonapi.com**, **creator@jsonapi.com**, **member@jsonapi.com** and password: **secret**).

The `src\pages\Pages\Login.vue` is the Vue component which handles the login functionality. You can easily adapt it to your needs.

It uses the auth store located in `src\store\modules\auth.js`.

### Login Card

```
<div class="container mt-3">
  <div class="col-lg-4 col-md-6 ml-auto mr-auto">
    <form @submit.prevent="handleSubmit()">
      <card class="card-login card-white">
        <template slot="header">
          <img src="/img/card-primary.png" alt="" />
          <h1 class="card-title">Log in</h1>
        </template>

        <div>
          <ValidationProvider
            name="email"
            rules="required|email"
            v-slot="{ passed, failed, errors }"
          >
          <base-input
            required
            v-model="email"
            type="email"
            placeholder="Email"
            addon-left-icon="tim-icons icon-email-85"
            :error="errors[0]"
            :class="[{ 'has-success': passed }, { 'has-danger': failed }]">
          </base-input>
          <validation-error :errors="apiValidationErrors.email" />
          </ValidationProvider>

          <ValidationProvider
            name="password"
            rules="required|min:5"
            v-slot="{ passed, failed, errors }"
          >
          <base-input
            required
            v-model="password"
            placeholder="Password"
            addon-left-icon="tim-icons icon-lock-circle"
            type="password"
            :error="errors[0]"
            :class="[{ 'has-success': passed }, { 'has-danger': failed }]">
          </base-input>
          <validation-error :errors="apiValidationErrors.password" />
        </ValidationProvider>
        </div>

        <div slot="footer">
          <base-button native-type="submit" type="primary" class="mb-3" size="lg" block>
            Get Started
          </base-button>
          <div class="pull-left">
            <h6>
              <router-link class="link footer-link" to="/register">
                Create Account
              </router-link>
            </h6>
          </div>

          <div class="pull-right">
            <h6><a href="/password/reset" class="link footer-link">Forgot Password?</a></h6>
          </div>
        </div>
      </card>
    </form>
    <!-- </ValidationObserver> -->
  </div>
</div>
```

### Register

The register functionality is fully implemented in our theme helping you to start your project in no time. To register a new user you just have to add **/register** in the URL or click on register link from register page and fill the register form with user details.

The `src\pages\Pages\Register.vue` is the Vue component which handles the register functionality. You can easily extend it to your needs.

It uses the auth store located in `src\store\modules\auth.js`.

#### Register card

```
<form @submit.prevent="handleSubmit()">
  <card class="card-register card-white">
    <template slot="header">
      <img class="card-img" src="/img/card-primary.png" alt="Card image"/>
      <h4 class="card-title">Register</h4>
    </template>

      <base-input
        required
        v-model="name"
        placeholder="Full Name"
        addon-left-icon="tim-icons icon-single-02"
        type="text"
        >
      </base-input>
    <validation-error :errors="apiValidationErrors.name" />

      <base-input
        required
        v-model="email"
        placeholder="Email"
        addon-left-icon="tim-icons icon-email-85"
        type="email"
        >
      </base-input>
    <validation-error :errors="apiValidationErrors.email" />

      <base-input
        required
        v-model="password"
        placeholder="Password"
        addon-left-icon="tim-icons icon-lock-circle"
        type="password"
        >
      </base-input>
    <validation-error :errors="apiValidationErrors.password" />

      <base-input
        required
        placeholder="Confirm Password"
        type="password"
        name="Password confirmation"
        v-model="password_confirmation"
        addon-left-icon="tim-icons icon-lock-circle"
      >
      </base-input>
    <validation-error :errors="apiValidationErrors.password_confirmation" />

    <base-checkbox v-model="boolean" class="text-left">
      I agree to the <a href="#something">terms and conditions</a>.
    </base-checkbox>

    <base-button native-type="submit" slot="footer" type="primary" round block size="lg">
      Get Started
    </base-button>
  </card>
</form>
```

### Profile edit

You have the option to edit the current logged in user's profile information (name, email, profile picture) and password. To access this page, just click the "**Examples/Profile**" link in the left sidebar or add **/examples/user-profile** in the URL.

The `src\pages\Pages\Examples\UserProfile` is the folder with Vue components that handle the update of the user information and password.

#### Edit profile component

```
<template>
  <card class="stacked-form" title="Stacked Form">
    <h4 slot="header" class="card-title">Edit Profile</h4>
    <form @submit.prevent>
      <div>
         <div class="col-md-4 col-sm-4">
            <h4 class="card-title">Profile Photo</h4>
            <image-upload
              type="avatar"
              select-text="Add photo"
              @change="onAvatarChange"
            />
          </div>
        <validation-error :errors="apiValidationErrors.attachment" />
        <base-input v-model="user.email" label="Email" type="email" placeholder="Enter email"/>
        <validation-error :errors="apiValidationErrors.email" /> 
        <base-input v-model="user.name" label="Name" placeholder="Name"/>
        <validation-error :errors="apiValidationErrors.name" />
        <base-button @click="updateProfile()" class="mt-3" native-type="submit" type="primary">Submit</base-button>
      </div>
    </form>
  </card>
</template>

<script>
import {
  ImageUpload,
} from 'src/components/index';
import ValidationError from "src/components/ValidationError.vue";
import formMixin from "@/mixins/form-mixin";
export default {
  mixins: [formMixin],
  components: {
    ImageUpload,
    ValidationError
  },
  props: {
      user: Object
    },
  data() {
    return {
      images: {
        avatar: null
      }
    }
  },
  methods: {
    onAvatarChange(file) {
      this.images.avatar = file;
    },
     async updateProfile() {
        try {
          if (this.images.avatar) {
            await this.$store.dispatch("users/upload", {user: this.user, image: this.images.avatar})
            this.user.profile_image = await this.$store.getters["users/url"]
          }

          await this.$store.dispatch("profile/update", this.user)
          this.$notify({
            type: 'success',
            message: 'Profile updated successfully.',
            icon: 'tim-icons icon-bell-55',
          })
          await this.$store.getters["profile/me"]
        } catch (e) {
          this.$notify({
            type: 'danger',
            message: 'Oops, something went wrong!',
            icon: 'tim-icons icon-bell-55',
          })
          this.setApiValidation(e.response.data.errors)
        }
    }
  }
}
</script>
```

#### Edit password component

```
<template>
  <card class="stacked-form" title="Change Password">
    <h4 slot="header" class="card-title">Change Password</h4>
    <form ref="password_form" @submit.prevent>
      <div>
        <base-input v-model="password" label="Password" type="password" placeholder="Password"/>
        <validation-error :errors="apiValidationErrors.password"/>
        <base-input v-model="password_confirmation" label="Password Confirmation" type="password" placeholder="Password Confirmation"/>
        <validation-error :errors="apiValidationErrors.password_confirmation"/>
        <base-button class="mt-3" native-type="submit" type="primary" @click="changePassword()"
          >Submit</base-button
        >
      </div>
    </form>
  </card>
</template>
<script>
  import ValidationError from "src/components/ValidationError.vue";
  import formMixin from "@/mixins/form-mixin";
  export default {
    name: "edit-password-card",

    props: {
      user: Object
    },

    components: {ValidationError},

    mixins: [formMixin],

    data: () => ({
      password: null,
      password_confirmation: null,
    }),

    methods: {
      async changePassword() {

        this.user.password = this.password;
        this.user.password_confirmation = this.password_confirmation;

        try {
          this.resetApiValidation();
          await this.$store.dispatch("users/update", this.user)
          this.$notify({
            type: 'success',
            message: 'Password changed successfully.',
            icon: 'tim-icons icon-bell-55',
          })
          this.user = await this.$store.getters["profile/me"]
          this.$refs['password_form'].reset()
        } catch (e) {
          this.$notify({
            type: 'danger',
            message: 'Oops, something went wrong!',
            icon: 'tim-icons icon-bell-55',
          })
          this.setApiValidation(e.response.data.errors)
        }
      }
    }
  };
</script>
```

### Role management

The Pro theme allows you to add user roles. By default, the theme comes with **Admin**, **Creator** and **Member** roles. To access the role management example click the "**Examples/Role Management**" link in the left sidebar or add **/examples/role-management/list-roles** to the URL. Here you can add/edit new roles.
To add a new role, click the "**Add role**" button. To edit an existing role, click the dotted menu (available on every table row) and then click "**Edit**". In both cases, you will be directed to a form which allows you to modify the name and description of a role.

The store used for role functionality is found in `src\store\modules\roles-module.vue`

You can find the compoments for role functionality in `src\pages\Pages\Examples\RoleManagement` folder.

#### List page

```
<el-table :data="table" @sort-change="sortChange">
  <div slot="empty" v-if="loading">
    <img src="/img/loading.gif" style="height: 100px; width: 100px" />
  </div>
  <el-table-column label="Name" prop="name" sortable="custom" />
  <el-table-column
    label="Created At"
    prop="created_at"
    sortable="custom"
  />
    <el-table-column :min-width="135" align="right" label="Actions">
      <div slot-scope="{row}">
        <base-button
          @click="goToEdit(row.id)"
          class="edit btn-link"
          type="warning"
          size="sm"
          icon
        >
          <i class="tim-icons icon-pencil"></i>
        </base-button>
        <base-button
          @click="destroy(row.id)"
          class="remove btn-link"
          type="danger"
          size="sm"
          icon
        >
          <i class="tim-icons icon-simple-remove"></i>
        </base-button>
      </div>
    </el-table-column>
  </el-table>
```

#### Add/edit role

```
<form @submit.prevent>
  <div>
    <base-input v-model="role.name" label="Name" placeholder="Name"/>
    <validation-error :errors="apiValidationErrors.name" />
    <base-button class="mt-3" native-type="submit" type="primary">Submit</base-button>
  </div>
</form>
```

### User management

The theme comes with an out of the box user management option. To access this option ,click the "**Examples/User Management**" link in the left sidebar or add **/examples/user-management/list-users** to the URL.
The first thing you will see is a list of existing users. You can add new ones by clicking the "**Add user**" button (above the table on the right). On the Add user page, you will find a form which allows you to fill out the user`s name, email, role and password.

The store used for role functionality is found in `src\store\modules\users-module.vue`

You can find the compoments for role functionality in `src\pages\Pages\Examples\UserManagement` folder.

Once you add more users, the list will grow and for every user you will have edit and delete options (access these options by clicking the three dotted menu that appears at the end of every row).

```
<el-table :data="table" @sort-change="sortChange">
  <div slot="empty" v-if="loading">
    <img src="/img/loading.gif" style="height: 100px; width: 100px" />
  </div>
  <el-table-column label="Author">
    <template v-slot="{ row }">
        <img v-if="row.profile_image" :src="row.profile_image" class="avatar rounded-circle mr-3"/>
    </template>
</el-table-column>
  <el-table-column label="Name" prop="name" sortable="custom" />
  <el-table-column label="Email" prop="email" sortable="custom" />
  <el-table-column
  label="Role"
  prop="roles.name"
  sortable="custom"
>
  <template v-slot="{ row }">
    <span>{{ row.roles[0].name }}</span>
  </template>
</el-table-column>
<el-table-column
  label="Created At"
  prop="created_at"
  sortable="custom"
/>
  <el-table-column :min-width="135" align="right" label="Actions">
    <div slot-scope="{row}">
      <base-button
        @click="goToEdit(row.id)"
        class="edit btn-link"
        type="warning"
        size="sm"
        icon
      >
        <i class="tim-icons icon-pencil"></i>
      </base-button>
      <base-button
        @click="destroy(row.id)"
        class="remove btn-link"
        type="danger"
        size="sm"
        icon
      >
        <i class="tim-icons icon-simple-remove"></i>
      </base-button>
    </div>
  </el-table-column>
</el-table>
```

### Tag management

Out of the box you will have an example of tag management (for the cases in which you are developing a blog or a shop). To access this example, click the "**Examples/Tag Management**" link in the left sidebar or add **/examples/tag-management/list-tags** to the URL.
You can add and edit tags here, but you can only delete them if they are not attached to any items.

The store used for role functionality is found in `src\store\modules\tags-module.vue`

You can find the compoments for role functionality in `src\pages\Pages\Examples\TagManagement` folder.

```
<el-table :data="table" @sort-change="sortChange">
  <div slot="empty" v-if="loading">
    <img src="/img/loading.gif" style="height: 100px; width: 100px" />
  </div>
  <el-table-column label="Name" prop="name" sortable="custom" />
  <el-table-column label="Color" prop="color" sortable="custom">
  <template slot-scope="{ row }">
    <span
      class="badge badge-default"
      :style="{ backgroundColor: row.color }"
      >{{ row.name }}</span
    >
  </template>
</el-table-column>
<el-table-column
  label="Created At"
  prop="created_at"
  sortable="custom"
/>
  <el-table-column :min-width="135" align="right" label="Actions">
    <div slot-scope="{row}">
      <base-button
        @click="goToEdit(row.id)"
        class="edit btn-link"
        type="warning"
        size="sm"
        icon
      >
        <i class="tim-icons icon-pencil"></i>
      </base-button>
      <base-button
        @click="destroy(row.id)"
        class="remove btn-link"
        type="danger"
        size="sm"
        icon
      >
        <i class="tim-icons icon-simple-remove"></i>
      </base-button>
    </div>
  </el-table-column>
</el-table>
```

### Category management

Out of the box you will have an example of category management (for the cases in which you are developing a blog or a shop). To access this example, click the "**Examples/Category Management**" link in the left sidebar or add **/examples/category-management/list-categories** to the URL.
You can add and edit categories here, but you can only delete them if they are not attached to any items.

The store used for category functionality is found in `src\store\modules\categories-module.vue`

You can find the compoments for category functionality in `src\pages\Pages\Examples\CategoryManagement` folder.

```
<el-table :data="table" @sort-change="sortChange">
  <div slot="empty" v-if="loading">
    <img src="/img/loading.gif" style="height: 100px; width: 100px" />
  </div>
  <el-table-column label="Name" prop="name" sortable="custom" />
  <el-table-column label="Description" prop="description" sortable="custom" />
  <el-table-column
    label="Created At"
    prop="created_at"
    sortable="custom"
  />
    <el-table-column :min-width="135" align="right" label="Actions">
      <div slot-scope="{row}">
        <base-button
          @click="goToEdit(row.id)"
          class="edit btn-link"
          type="warning"
          size="sm"
          icon
        >
          <i class="tim-icons icon-pencil"></i>
        </base-button>
        <base-button
          @click="destroy(row.id)"
          class="remove btn-link"
          type="danger"
          size="sm"
          icon
        >
          <i class="tim-icons icon-simple-remove"></i>
        </base-button>
      </div>
    </el-table-column>
  </el-table>
```

### Item management

Item management is the most advanced example included in the Pro theme, because every item has a picture, belongs to a category and has multiple tags. To access this example click the "**Examples/Item Management**" link in the left sidebar or add **/examples/item-management/list-items** to the URL.
Here you can manage the items. A list of items will appear once you start adding them (to access the add page click "**Add item**").
On the add page, besides the Name and Description fields (which are present in most of the CRUD examples) you can see a category dropdown, which contains the categories you added, a file input and a tag multi select. If you did not add any categories or tags, please go to the corresponding sections (category management, tag management) and add some.

The store used for roles functionality is found in `src\store\modules\items-module.vue`

You can find the compoments for items functionality in `src\pages\Pages\Examples\ItemManagement` folder.

#### List Items

```
<el-table :data="table" @sort-change="sortChange">
  <div slot="empty" v-if="loading">
    <img src="/img/loading.gif" style="height: 100px; width: 100px" />
  </div>
  <el-table-column label="Name" prop="name" sortable="custom" />
  <el-table-column label="Category" prop="category.name" sortable="custom" />
  <el-table-column label="Picture">
    <template v-slot="{ row }">
      <img
        v-if="row.image"
        :src="row.image"
        style="width: 100px; height: auto"
        alt="avatar"
      />
    </template>
  </el-table-column>
  <el-table-column label="Tags" sortable="custom" prop="tags.name">
    <template slot-scope="{ row }">
      <span
        v-for="(tag, index) in row.tags"
        :key="'tag' + index"
        class="badge badge-default"
        :style="{ backgroundColor: tag.color, margin: '.1rem' }"
        >{{ tag.name }}</span
      >
    </template>
  </el-table-column>
  <el-table-column
    label="Created At"
    prop="created_at"
    sortable="custom"
  />
    <el-table-column :min-width="135" align="right" label="Actions">
      <div slot-scope="{row}">
        <base-button
          @click="goToEdit(row.id)"
          class="edit btn-link"
          type="warning"
          size="sm"
          icon
        >
          <i class="tim-icons icon-pencil"></i>
        </base-button>
        <base-button
          @click="destroy(row.id)"
          class="remove btn-link"
          type="danger"
          size="sm"
          icon
        >
          <i class="tim-icons icon-simple-remove"></i>
        </base-button>
      </div>
    </el-table-column>
  </el-table>
```

#### Add/Edit Item

```
<form @submit.prevent>
  <div>
    <div class="col-md-4 col-sm-4">
      <h4 class="card-title">Profile Photo</h4>
      <image-upload
        type="avatar"
        select-text="Add photo"
        @change="onAvatarChange"
      />
    </div>
    <base-input v-model="item.name" label="Name" placeholder="Name"/>
    <validation-error :errors="apiValidationErrors.name" />
    <base-input label="Description">
    <ckeditor :editor="editor" v-model="item.description" :config="editorConfig"></ckeditor>
    </base-input>
    <validation-error :errors="apiValidationErrors.excerpt" />

    <base-input label="Category">
    <el-select class="select-primary" v-model="item.category.id">
        <el-option
          v-for="category in available_categories"
          :key="category.id"
          :value="category.id"
          :label="category.name"
        >
        </el-option>
      </el-select>
    </base-input>
    <base-input label="Status">
      <base-radio v-model="item.status" name="published">
        Published
      </base-radio>
      <base-radio v-model="item.status" name="draft">
        Draft
      </base-radio>
      <base-radio v-model="item.status" name="archive">
        Archive
      </base-radio>
    </base-input>

    <base-input label="Tag">
    <el-select  multiple class="select-primary" collapse-tags v-model="tags">
        <el-option
          v-for="tag in available_tags"
          :key="tag.id"
          :value="tag.id"
          :label="tag.name"
        >
        </el-option>
      </el-select>
    </base-input>
    <base-input label="Show on homepage?">
      <base-switch v-model="item.is_on_homepage"></base-switch>
    </base-input>
    <base-input label="Date">
      <el-date-picker type="date" placeholder="Select date" v-model="item.date_at"/>
    </base-input>
      <validation-error :errors="apiValidationErrors.date_at" />
  
    <base-button @click="update()" class="mt-3" native-type="submit" type="primary">Submit</base-button>
  </div>
</form>
```

## Table of Contents

- [Versions](#versions)
- [Demo](#demo)
- [Documentation](#documentation)
- [File Structure](#file-structure)
- [Browser Support](#browser-support)
- [Resources](#resources)
- [Reporting Issues](#reporting-issues)
- [Licensing](#licensing)
- [Useful Links](#useful-links)

## Versions

[<img src="https://github.com/creativetimofficial/public-assets/blob/master/logos/html-logo.jpg" height="80" />](#)
[<img src="https://github.com/creativetimofficial/public-assets/blob/master/logos/laravel_logo.png" height="80" />](#)
[<img src="https://github.com/creativetimofficial/public-assets/blob/master/logos/vue.jpg" height="80" />](#)
[<img src="https://github.com/creativetimofficial/public-assets/blob/master/logos/json-api.png" height="75" />](#)

 LARAVEL | VUE | LARAVEL & VUE|
| --- | --- | --- |
| [![Black Dashboard Pro Laravel](https://s3.amazonaws.com/creativetim_bucket/products/166/original/opt_blkp_laravel_thumbnail.jpg)](https://www.creative-tim.com/product/black-dashboard-pro-laravel?ref=vbdpl-readme) | [![Vue Black Dashboard Pro ](https://s3.amazonaws.com/creativetim_bucket/products/135/original/opt_bdp_vue_thumbnail_%285%29.jpg)](https://www.creative-tim.com/product/vue-black-dashboard-pro?ref=vbdpl-readme) | [![Vue Black Dashboard Pro Laravel](https://s3.amazonaws.com/creativetim_bucket/products/403/original/opt_bdp_vuelaravel_thumbnail.jpg)](https://www.creative-tim.com/product/vue-black-dashboard-pro-laravel?ref=vbdpl-readme) |

## Demo

| Register                                                                                                                                                                                                                   | Login                                                                                                                                                                                                             | Dashboard                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [![Register](https://raw.githubusercontent.com/creativetimofficial/public-assets/master/vue-black-dashboard-laravel-pro/register.png)](https://vue-black-dashboard-pro-laravel.creative-tim.com/register?ref=vbdpl-readme) | [![Login](https://raw.githubusercontent.com/creativetimofficial/public-assets/master/vue-black-dashboard-laravel-pro/login.png)](https://vue-black-dashboard-pro-laravel.creative-tim.com/login?ref=vbdpl-readme) | [![Dashboard](https://raw.githubusercontent.com/creativetimofficial/public-assets/master/vue-black-dashboard-laravel-pro/dashboard.png)](https://vue-black-dashboard-pro-laravel.creative-tim.com/?ref=vbdpl-readme) |

| Profile Page                                                                                                                                                                                                                               | Users Page                                                                                                                                                                                                                                           | Tables Page                                                                                                                                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [![Profile Page](https://raw.githubusercontent.com/creativetimofficial/public-assets/master/vue-black-dashboard-laravel-pro/profile.png)](https://vue-black-dashboard-pro-laravel.creative-tim.com/examples/user-profile?ref=vbdpl-readme) | [![Users Page](https://raw.githubusercontent.com/creativetimofficial/public-assets/master/vue-black-dashboard-laravel-pro/users.png)](https://vue-black-dashboard-pro-laravel.creative-tim.com/examples/user-management/list-users?ref=vbdpl-readme) | [![Tables Page](https://raw.githubusercontent.com/creativetimofficial/public-assets/master/vue-black-dashboard-laravel-pro/table.png)](https://vue-black-dashboard-pro-laravel.creative-tim.com/table-list/extended?ref=vbdpl-readme) |

[View More](https://vue-black-dashboard-pro-laravel.creative-tim.com/?ref=vbdpl-readme)

## Documentation

The documentation for the Vue Black Dashboard PRO is hosted at our [website](https://vue-black-dashboard-pro-laravel.creative-tim.com/documentation/?ref=vbdpl-github-readme).

## File Structure

Within the download you'll find the following directories and files:

```
├───vue-black-dashboard
│   App.vue
│   main.js
│   polyfills.js
│
├── assets
│   ├── css
│   │   ├── custom.css
│   │   ├── demo.css
│   │   └── nucleo-icons.css
│   ├── fonts
│   │   ├── nucleo.eot
│   │   ├── nucleo.ttf
│   │   ├── nucleo.woff
│   │   └── nucleo.woff2
│   └── sass
│       ├── black-dashboard-pro.scss
│       ├── dashboard
│       └── vendor
│           └── bootstrap-rtl.scss
├── components
│   ├── AnimatedNumber.vue
│   ├── Badge.vue
│   ├── BaseAlert.vue
│   ├── BaseButton.vue
│   ├── BaseDropdown.vue
│   ├── BasePagination.vue
│   ├── BaseProgress.vue
│   ├── BaseSwitch.vue
│   ├── BaseTable.vue
│   ├── Breadcrumb
│   │   ├── BreadcrumbItem.vue
│   │   ├── Breadcrumb.vue
│   │   └── RouteBreadcrumb.vue
│   ├── Cards
│   │   ├── Card.vue
│   │   └── StatsCard.vue
│   ├── Charts
│   │   ├── BarChart.js
│   │   ├── config.js
│   │   ├── LineChart.js
│   │   ├── PieChart.js
│   │   └── utils.js
│   ├── CloseButton.vue
│   ├── Collapse
│   │   ├── CollapseItem.vue
│   │   └── Collapse.vue
│   ├── ImageUpload.vue
│   ├── index.js
│   ├── Inputs
│   │   ├── BaseCheckbox.vue
│   │   ├── BaseInput.vue
│   │   ├── BaseRadio.vue
│   │   ├── IconCheckbox.vue
│   │   └── TagsInput.vue
│   ├── LoadingPanel.vue
│   ├── Modal.vue
│   ├── Navbar
│   │   ├── BaseNav.vue
│   │   └── NavbarToggleButton.vue
│   ├── NavbarToggleButton.vue
│   ├── NotificationPlugin
│   │   ├── index.js
│   │   ├── Notifications.vue
│   │   └── Notification.vue
│   ├── SidebarPlugin
│   │   ├── index.js
│   │   ├── SidebarItem.vue
│   │   └── SideBar.vue
│   ├── Slider.vue
│   ├── Tabs
│   │   ├── Tabs.vue
│   │   └── Tab.vue
│   ├── Timeline
│   │   ├── TimeLineItem.vue
│   │   └── TimeLine.vue
│   ├── ValidationError.vue
│   ├── Wizard
│   │   ├── throttle.js
│   │   ├── WizardTab.vue
│   │   └── Wizard.vue
│   └── WorldMap
│       ├── AsyncWorldMap.vue
│       └── WorldMap.vue
├── middleware
│   ├── auth.js
│   └── guest.js
├── mixins
│   └── form-mixin.js
├── pages
│   ├── Calendar
│   │   ├── CalendarHeader.vue
│   │   ├── CalendarRoute.vue
│   │   └── Calendar.vue
│   ├── Charts.vue
│   ├── Components
│   │   ├── Buttons.vue
│   │   ├── GridSystem.vue
│   │   ├── Headers
│   │   │   └── SweetAlertHeader.vue
│   │   ├── Icons.vue
│   │   ├── Notifications.vue
│   │   ├── Panels.vue
│   │   ├── SweetAlert.vue
│   │   └── Typography.vue
│   ├── Dashboard
│   │   ├── CountryMapCard.vue
│   │   ├── Dashboard.vue
│   │   ├── TaskList.vue
│   │   └── UserTable.vue
│   ├── Forms
│   │   ├── ExtendedForms.vue
│   │   ├── RegularForms.vue
│   │   ├── ValidationForms
│   │   │   ├── LoginForm.vue
│   │   │   ├── RangeValidationForm.vue
│   │   │   ├── RegisterForm.vue
│   │   │   └── TypeValidationForm.vue
│   │   ├── ValidationForms.vue
│   │   ├── Wizard
│   │   │   ├── FirstStep.vue
│   │   │   ├── SecondStep.vue
│   │   │   └── ThirdStep.vue
│   │   └── Wizard.vue
│   ├── GeneralViews
│   │   └── NotFoundPage.vue
│   ├── Layout
│   │   ├── ContentFooter.vue
│   │   ├── Content.vue
│   │   ├── DashboardLayout.vue
│   │   ├── DashboardNavbar.vue
│   │   ├── LoadingMainPanel.vue
│   │   ├── SidebarFixedToggleButton.vue
│   │   ├── SidebarSharePlugin.vue
│   │   └── SidebarToggleButton.vue
│   ├── Maps
│   │   ├── API_KEY.js
│   │   ├── FullScreenMap.vue
│   │   ├── GoogleMaps.vue
│   │   └── VectorMaps.vue
│   ├── Pages
│   │   ├── AuthLayout.vue
│   │   ├── Examples
│   │   │   ├── CategoryManagement
│   │   │   │   ├── AddCategoryPage.vue
│   │   │   │   ├── EditCategoryPage.vue
│   │   │   │   └── ListCategoryPage.vue
│   │   │   ├── ItemManagement
│   │   │   │   ├── AddItemPage.vue
│   │   │   │   ├── EditItemPage.vue
│   │   │   │   └── ListItemPage.vue
│   │   │   ├── RoleManagement
│   │   │   │   ├── AddRolePage.vue
│   │   │   │   ├── EditRolePage.vue
│   │   │   │   └── ListRolePage.vue
│   │   │   ├── TagManagement
│   │   │   │   ├── AddTagPage.vue
│   │   │   │   ├── EditTagPage.vue
│   │   │   │   └── ListTagPage.vue
│   │   │   ├── UserManagement
│   │   │   │   ├── AddUserPage.vue
│   │   │   │   ├── EditUserPage.vue
│   │   │   │   └── ListUserPage.vue
│   │   │   ├── UserProfile
│   │   │   │   ├── EditPasswordCard.vue
│   │   │   │   └── EditProfileCard.vue
│   │   │   └── UserProfile.vue
│   │   ├── Lock.vue
│   │   ├── Login.vue
│   │   ├── Password
│   │   │   ├── Email.vue
│   │   │   └── Reset.vue
│   │   ├── Pricing.vue
│   │   ├── Register.vue
│   │   ├── RTLPage.vue
│   │   ├── TimeLinePage.vue
│   │   ├── UserProfile
│   │   │   ├── EditProfileForm.vue
│   │   │   └── UserCard.vue
│   │   └── UserProfile.vue
│   ├── Starter
│   │   ├── SampleFooter.vue
│   │   ├── SampleLayout.vue
│   │   ├── SampleNavbar.vue
│   │   └── SamplePage.vue
│   ├── Tables
│   │   ├── ExtendedTables
│   │   │   └── ShoppingTable.vue
│   │   ├── ExtendedTables.vue
│   │   ├── PaginatedTables.vue
│   │   ├── RegularTables.vue
│   │   └── users.js
│   └── Widgets.vue
├── plugins
│   ├── dashboard-plugin.js
│   ├── globalComponents.js
│   ├── globalDirectives.js
│   └── RTLPlugin.js
├── router
│   ├── index.js
│   ├── routes.js
│   └── starterRouter.js
├── store
│   ├── index.js
│   ├── modules
│   │   ├── alerts-module.js
│   │   ├── auth.js
│   │   ├── categories-module.js
│   │   ├── items-module.js
│   │   ├── profile-module.js
│   │   ├── reset.js
│   │   ├── roles-module.js
│   │   ├── tags-module.js
│   │   └── users-module.js
│   └── services
│       ├── categories-service.js
│       ├── items-service.js
│       ├── profile-service.js
│       ├── roles-service.js
│       ├── tags-service.js
│       └── users-service.js
└── util
    └── throttle.js
```

## Browser Support

At present, we officially aim to support the last two versions of the following browsers:

<img src="https://github.com/creativetimofficial/public-assets/blob/master/logos/chrome-logo.png?raw=true" width="64" height="64"> <img src="https://raw.githubusercontent.com/creativetimofficial/public-assets/master/logos/firefox-logo.png" width="64" height="64"> <img src="https://raw.githubusercontent.com/creativetimofficial/public-assets/master/logos/edge-logo.png" width="64" height="64"> <img src="https://raw.githubusercontent.com/creativetimofficial/public-assets/master/logos/safari-logo.png" width="64" height="64"> <img src="https://raw.githubusercontent.com/creativetimofficial/public-assets/master/logos/opera-logo.png" width="64" height="64">

## Resources

- Demo: <https://vue-black-dashboard-pro-laravel.creative-tim.com/?ref=vbdpl-readme>
- Download Page: <https://www.creative-tim.com/product/vue-black-dashboard-pro-laravel?ref=vbdpl-readme>
- Documentation: <https://vue-black-dashboard-pro-laravel.creative-tim.com/documentation?ref=vbdpl-readme>
- License Agreement: <https://www.creative-tim.com/license>
- Support: <https://www.creative-tim.com/contact-us>
- Issues: [Github Issues Page](https://github.com/creativetimofficial/ct-vue-black-dashboard-pro-laravel/issues)
- **Dashboards:**

 LARAVEL | VUE | LARAVEL & VUE|
| --- | --- | --- |
| [![Black Dashboard Pro Laravel](https://s3.amazonaws.com/creativetim_bucket/products/166/original/opt_blkp_laravel_thumbnail.jpg)](https://www.creative-tim.com/product/black-dashboard-pro-laravel?ref=vbdpl-readme) | [![Vue Black Dashboard Pro ](https://s3.amazonaws.com/creativetim_bucket/products/135/original/opt_bdp_vue_thumbnail_%285%29.jpg)](https://www.creative-tim.com/product/vue-black-dashboard-pro?ref=vbdpl-readme) | [![Vue Black Dashboard Pro Laravel](https://s3.amazonaws.com/creativetim_bucket/products/403/original/opt_bdp_vuelaravel_thumbnail.jpg)](https://www.creative-tim.com/product/vue-black-dashboard-pro-laravel?ref=vbdpl-readme) |

## Reporting Issues

We use GitHub Issues as the official bug tracker for the Black Kit. Here are some advices for our users that want to report an issue:

1. Make sure that you are using the latest version of the Black Kit. Check the CHANGELOG from your dashboard on our [website](https://www.creative-tim.com/?ref=vbdpl-readme).
2. Providing us reproducible steps for the issue will shorten the time it takes for it to be fixed.
3. Some issues may be browser specific, so specifying in what browser you encountered the issue might help.

## Licensing

- Copyright 2020 Creative Tim (https://www.creative-tim.com/?ref=vbdpl-readme)

- Creative Tim license - (https://www.creative-tim.com/license)

## Useful Links

- [Tutorials](https://www.youtube.com/channel/UCVyTG4sCw-rOvB9oHkzZD1w?ref=vbdpl-readme)
- [Affiliate Program](https://www.creative-tim.com/affiliates/new?ref=vbdpl-readme) (earn money)
- [Blog Creative Tim](http://blog.creative-tim.com/?ref=vbdpl-readme)
- [Free Products](https://www.creative-tim.com/bootstrap-themes/free?ref=vbdpl-readme) from Creative Tim
- [Premium Products](https://www.creative-tim.com/bootstrap-themes/premium?ref=vbdpl-readme) from Creative Tim
- [React Products](https://www.creative-tim.com/bootstrap-themes/react-themes?ref=vbdpl-readme) from Creative Tim
- [Angular Products](https://www.creative-tim.com/bootstrap-themes/angular-themes?ref=vbdpl-readme) from Creative Tim
- [VueJS Products](https://www.creative-tim.com/bootstrap-themes/vuejs-themes?ref=vbdpl-readme) from Creative Tim
- [More products](https://www.creative-tim.com/bootstrap-themes?ref=vbdpl-readme) from Creative Tim
- Check our Bundles [here](https://www.creative-tim.com/bundles?ref=vbdpl-readme)

## Social Media

### Creative Tim:

Twitter: <https://twitter.com/CreativeTim?ref=vbdpl-readme>

Facebook: <https://www.facebook.com/CreativeTim?ref=vbdpl-readme>

Dribbble: <https://dribbble.com/creativetim?ref=vbdpl-readme>

Instagram: <https://www.instagram.com/CreativeTimOfficial?ref=vbdpl-readme>

### Updivision:

Twitter: <https://twitter.com/updivision?ref=vbdpl-readme>

Facebook: <https://www.facebook.com/updivision?ref=vbdpl-readme>

Linkedin: <https://www.linkedin.com/company/updivision?ref=vbdpl-readme>

Updivision Blog: <https://updivision.com/blog/?ref=vbdpl-readme>

## Credits

- [Creative Tim](https://creative-tim.com/?ref=vbdpl-readme)
- [UPDIVISION](https://updivision.com)
