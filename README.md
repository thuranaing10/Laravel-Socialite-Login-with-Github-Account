composer create-project laravel/laravel example-app
composer require laravel/jetstream
php artisan jetstream:install livewire
npm install
npm run dev
php artisan migrate
composer require laravel/socialite
Create Github App
    In this step we need github client id and secret that way we can get information of other user. so if you don't have github app account then you can create from here : Github Developers Console. you can find bellow screen, Then click on "New OAuth App" and create new app:
    
config/services.php

return [
    ....
    'github' => [
        'client_id' => env('GITHUB_CLIENT_ID'),
        'client_secret' => env('GITHUB_CLIENT_SECRET'),
        'redirect' => 'http://localhost:8000/auth/github/callback',
    ],
]

.env

GITHUB_CLIENT_ID=xyz
GITHUB_CLIENT_SECRET=123

php artisan make:migration add_github_id_column

public function up()
    {
        Schema::table('users', function ($table) {
            $table->string('github_id')->nullable();
        });
    }
