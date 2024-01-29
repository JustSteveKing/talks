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
- Plugs into Doctrine with zero hassle.
- Focus on HTTP Resources instead of ORM Entities or Models.

---

I am a Laravel Developer

---

I am a _pretty good_ Laravel Developer

---

but

---

## Building APIs in Laravel feels like pulling teeth

---

Let me explain ...

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

## But, we have to do this ...

```git
Changes to be commited:
  (use "git restore --staged <file>..." to unstage)
    deleted: package.json
    deleted: resources/js/app.js
    deleted: resources/js/bootstrap.js
    renamed: resources/css/app.css -> resources/views/.gitkeep
    deleted: resources/views/welcome.blade.php
    deleted: vite.config.js
```

---

## Then comes the packages ....

---

```bash
composer require spatie/laravel-query-builder
```

---

```bash
composer require timacdonald/json-api
```

---

## Not forgetting authentication of course!

---

```bash
composer require laravel/sanctum
```

---

```bash
composer require laravel/passport
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

## So, we have CRUD on one Model/Entity....

---

## Webby, help us out please!?

---

# How can API Platform help us?

---

## We can define our Entities

---

## and we have automatic CRUD endpoints already!

---

## Let's let that sink in for a moment ....

---

## We went from this

---

## We went from this

- Generate Model, Migration, and Factory
- Customize our Database Migration
- Configure the Eloquent Mode
- Register Routes for the new Model
- Create and add logic to all required Controllers
- Create our API Resources to return
- Make sure we have our validation rules in place

---

## To this

---

## To this

- Create Resource class
- Add Entity attribute
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


