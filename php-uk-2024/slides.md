---
author: Steve McDougall
date: MMMM dd
theme: theme.json
---

# Leveraging API Platform

## A Laravel Developers Guide

---

# Who am I?

---

## I give talks at places like this

---

## I write for PHP Architect, as well as other places.

---

## I livestream on YouTube

---

## I live in Wales

---

## I like to take a selfie anytime I do a talk ...

---

## Say Cheese!

---

📸

---

# What is this talk?

---

## This isn't a Framework War ...

---

## At least it isn't JavaScript!

---

#  Let's talk about API Platform

---

- PHP Framework for building APIs

---

- PHP Framework for building APIs
- Plugs into Doctrine with zero hassle.

---

- PHP Framework for building APIs
- Plugs into Doctrine with zero hassle.
- Focus on HTTP Resources instead of ORM Entities or Models.

---

I am a Laravel Developer

---

I am a _pretty good_ Laravel Developer

---

I am a _pretty good_ Laravel Developer 😏

---

but

---

## Building APIs in Laravel feels like pulling teeth

---

Let me explain ...

---

## We start with

---

## We start with

```bash
laravel new project --git --pest
```

---

## We have a great starting point!

---

## For a Full-Stack application ...

---

## But ...

---

## But, we have all seen this initial commit ...

```git
Changes to be commited:
  (use "git restore --staged <file>..." to unstage)
    deleted: package.json
    deleted: resources/js/app.js
    deleted: resources/js/bootstrap.js
    deleted: resources/css/app.css
    deleted: resources/views/welcome.blade.php 
    deleted: vite.config.js
```
---

(┛ಠ_ಠ)┛彡┻━┻

---

## The ecosystem is rich though!

---

```bash
composer require spatie/laravel-permissions
```

---

```bash
composer require spatie/laravel-query-builder
```

---

```bash
composer require spatie/laravel-data
```


---

## I mean, we might as well ...

---

## I mean, we might as well ...

```bash
composer require spatie/*
```

---

## Not forgetting the first party packages

---

```bash
composer require laravel/sanctum
```

---

```bash
composer require laravel/passport
```

---

```bash
composer require laravel/breeze
```

---

```bash
composer require laravel/pennant
```

---

```bash
composer require laravel/horizon
```

---

## Then we need to configure the packages ....

---

## Add our routes ....

---

## Create relevant Controllers ....

---

## Return reasonable Responses ....

---

## I'm not talking about this

```php
return Greeting::all();
```

---

## Or this

```php

return response()->json(Greeting::all())
```

---

## I am talking about this

---

```php
final readonly class CollectionResponse implements Responsable
{
  // constructor here
  public function toResponse(): JsonResponse
  {
    return new JsonResponse(
      data: $this->data,
      status: $this->status->value,
    );
  }
}
```

---

# Yes **FINAL** and **READONLY** 😎

---

## Go big or go home...

---

## Validate user input ....

---

## Finally ....

---

## We have an API with Authentication!

---

## Now we can finally work on our Business Logic!

---

```bash
php artisan make:model Greeting -mf
```

---

## Now we need to configure our Database Migration

---

## Not forgetting we need to set up the Model itself

---

## Now we need to add our routes again ....

---

## Back to working on our Controllers ....

---

## Now let's Design our API Resources

---

## Time to validation more user input

---

## And ...

---

## We have full CRUD on **one** resource.

---

## Webby

---

## Webby, help us out please!?

---

# How can API Platform help us?

---

## We can define our Entities

---

## and

---

## That's it

---

## we have automatic CRUD endpoints already!

---

## Let's let that sink in for a moment ....

---

## Maybe a moment longer

---

## When I first experienced this

---

# I

---

# I was

---

# I was Speachless

---


## We went from this

---

## We went from this

- Generate Model, Migration, and Factory

---

## We went from this

- Generate Model, Migration, and Factory
- Customize our Database Migration

---

## We went from this

- Generate Model, Migration, and Factory
- Customize our Database Migration
- Configure the Eloquent Model

---

## We went from this

- Generate Model, Migration, and Factory
- Customize our Database Migration
- Configure the Eloquent Model
- Register Routes for the new Model

---

## We went from this

- Generate Model, Migration, and Factory
- Customize our Database Migration
- Configure the Eloquent Model
- Register Routes for the new Model
- Create and add logic to all required Controllers

---

## We went from this

- Generate Model, Migration, and Factory
- Customize our Database Migration
- Configure the Eloquent Model
- Register Routes for the new Model
- Create and add logic to all required Controllers
- Create our API Resources to return

---

## We went from this

- Generate Model, Migration, and Factory
- Customize our Database Migration
- Configure the Eloquent Model
- Register Routes for the new Model
- Create and add logic to all required Controllers
- Create our API Resources to return
- Make sure we have our validation rules in place

---

## To this

---

## To this

- Create Resource class

---

## To this

- Create Resource class
- Add Entity attributes

---

## To this

- Create Resource class
- Add Entity attributes
- Add relevent properties

---

## And all we used

---

## Was

---

## PHP

---

## Yep, standard PHP.

---

## A couple of PHP Attributes to handle the Database and Routing

---

## Easy right?

---

## All in one place too!

---

< yay >
 -----
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

---

## So,

---

## So, why haven't I been using for longer?

---

## Honestly?

---

## I thought I needed an indepth knowledge of Symfony ....

---

## Turns out, all I needed to know was PHP

---

## We get CRUD Endpoints for all Resources

---

## We can configure them, customize them, do what we need

---

## All without having to touch a framework ....

---

## Let's look at an example Laravel Model

---

```php
class Greeting extends Model
{
  protected $fillable = [
    'name',
  ];
}
```

---

## Not overly complicated, I think we can agree on that

```php
class Greeting extends Model
{
  protected $fillable = [
    'name',
  ];
}
```

---

## Now, let's compare it to an API Platform Resource

---

```php
#[ORM\Entity]
class Greeting
{
  #[ORM\Id]
  #[ORM\Column(type: 'integer')]
  #[ORM\GeneratedValue]
  private null|int $id = null;

  #[ORM\Column]
  #[Assert\NotBlank]
  public string $name = '';
}
```

---

## Like for like, they are both relatively simple

---

## One uses properties

---

## The other uses attributes

---

## A question I get asked _all the time_

---

> When would I use Laravel?

---

> When would I use Laravel?

- Full-Stack applications

---

> When would I use Laravel?

- Full-Stack applications
- Application where I have a frontend and an API

---

> When would I use Laravel?

- Full-Stack applications
- Application where I have a frontend and an API
- When I don't know if I need an API yet.

---

## Laravel is a FULL-STACK framework first

---

## This is by design

---

## This is by design, and decision

---

## API Platform

---

## API Platform, as the name suggests

---

## API Platform, as the name suggests is designed

---

## API Platform, as the name suggests is designed for

---

## API Platform, as the name suggests is designed for APIs

---

## Adding Auth in Laravel is just a package

---

## Adding Auth in Laravel is just a package

```bash
composer require laravel/passport
```

---

## Adding Auth in Laravel is just a package

```bash
composer require laravel/passport
php artisan migrate
```

---

## Adding Auth in Laravel is just a package

```bash
composer require laravel/passport
php artisan migrate
php artisan passport:install --uuids
```

---

## How about API Platform?

---

## How about API Platform?

```bash
composer require symfony/security-bundle
```

---

## How about API Platform?

```bash
composer require symfony/security-bundle
```

Then we configure it how we want to use it.

---

## But, in Laravel we have Jobs!

```bash
php artisan make:job GreetUser
```

---

## I see your job, and raise you Async messaging

---

## All you have to do is tell your Resource to use messaging!

---

```php
#[ApiResource(operations: [
  new Get(controller: NotFoundAction::class, read: false, status: 404),
  new Post(messenger: true, output: false, status: 202),
])]
#[ORM\Entity]
class Greeting
{
  // properties and set up here ...
}
```

---

## API Platform gives you all the tools you could possibly need

---

## So, when building an API.

---

## So, when building an API. Try it.

---

< Try API Platform >
 ------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

---

- There is no requirement to know Symfony

---

- There is no requirement to know Symfony
- You can just use PHP with annotations, ignore the rest

---

- There is no requirement to know Symfony.
- You can just use PHP with annotations, ignore the rest.
- Content Negotiation is configurable.

---

- There is no requirement to know Symfony.
- You can just use PHP with annotations, ignore the rest.
- Content Negotiation is configurable.
- The community is a lot more approachable than you have been lead to believe.

---

< give your API super-powers >
 ----------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

---

< Use API-Platform for your next API >
 ----------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

---

# Thanks for listening

---

# Thanks for listening

- GitHub: JustSteveKing

---

# Thanks for listening

- GitHub: JustSteveKing
- Twitter: JustSteveKing

---

# Thanks for listening

- GitHub: JustSteveKing
- Twitter: JustSteveKing
- Mastodon: JustSteveKing

---

# Thanks for listening

- GitHub: JustSteveKing
- Twitter: JustSteveKing
- Mastodon: JustSteveKing
- Whatever is next: JustSteveKing

---

< Any Questions >
 --------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
