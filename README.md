Symfony Demo Application
========================

The "Symfony Demo Application" is a reference application created to show how
to develop applications following the [Symfony Best Practices][1].

You can also learn about these practices in [the official Symfony Book][5].

Installation
------------

There are 3 different ways of installing this project depending on your needs:

[Download Composer][6] and use the `composer` binary installed
on your computer to run these commands:

```bash
composer install
php bin/console asset-map:compile
```

Usage
-----

There's no need to configure anything before running the application. There are
2 different ways of running this application depending on your needs:

**Option 1.** You can run this command to use the built-in PHP web server:

```bash
php -S localhost:8000 -t public/
```

**Option 2.** Use Wasmer.

```bash
wasmer run . --net
```

Then access the application in your browser at the given URL (<https://localhost:8000> by default).


Tests
-----

Execute this command to run tests:

```bash
./bin/phpunit
```

[1]: https://symfony.com/doc/current/best_practices.html
[2]: https://symfony.com/doc/current/setup.html#technical-requirements
[3]: https://symfony.com/doc/current/setup/web_server_configuration.html
[4]: https://symfony.com/download
[5]: https://symfony.com/book
[6]: https://getcomposer.org/
