# Symfony Demo App + Wasmer

This example shows how to run the official **Symfony Demo Application** on **Wasmer Edge**.

## Demo

`https://<your-subdomain>.wasmer.app/` (deploy to explore the blog UI)

## How it Works

The project is the upstream Symfony Demo with a few Wasmer-friendly tweaks:

* `public/index.php` bootstraps the HTTP kernel—Wasmer points web traffic to this front controller.
* `config/routes.yaml` imports attribute-based controllers under `src/Controller/` (blog, admin, comments, etc.).
* Doctrine uses the SQLite database defined in `.env` (`data/database.sqlite`), allowing the app to run without an external service.
* Assets are managed through AssetMapper; run `php bin/console asset-map:compile` during your build step so Wasmer serves optimised assets.

## Running Locally

```bash
composer install
php bin/console doctrine:database:create --if-not-exists
php bin/console doctrine:migrations:migrate --no-interaction
php bin/console doctrine:fixtures:load --no-interaction
php -S 127.0.0.1:8000 -t public
```

Open `http://127.0.0.1:8000/` to browse the demo blog. Sample admin accounts seeded by the fixtures include `jane_admin@symfony.com` (password `kitten`).

## Deploying to Wasmer (Overview)

1. Build assets and warm up caches:
   ```bash
   composer install --no-dev --optimize-autoloader
   php bin/console asset-map:compile
   php bin/console cache:warmup
   ```
2. Ensure the SQLite database file lives under `data/` and is writable.
3. Deploy to Wasmer Edge with a start command like `php -S 0.0.0.0:$PORT -t public` and visit `https://<your-subdomain>.wasmer.app/`.
