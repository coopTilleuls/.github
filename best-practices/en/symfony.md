# Les-Tilleuls.coop’s Symfony Best Practices

> TODO update ? Last edit 2018

## Environment

- PHPStorm/Webstorm + Symfony plugin + PHP EA Inspections (or vim, for advanced users only)
- Docker

## Getting Started / Stack

- Start the project using the API Platform distribution (preferred) or Docker for Symfony 4 (using https://github.com/dunglas/symfony-docker).
- Always the latest stable version of PHP, Symfony and API Platform
- Use Postgres as RDBMS (no MySQL). In prod, always use a managed version (Google Cloud SQL - prefered, Amazon RDS, Heroku Postgres…).
- Use Nginx as web server (no Apache).
- Use Varnish fast cache reverse proxy (or a managed service such as CloudFlare and Varnish)
- Create a user system by following Symfony's [Security User Providers](http://symfony.com/doc/current/security/entity_provider.html), no FOSUserBundle!
- Use Doctrine ORM.
- Always use Flysystem to store files (images, avatars, exports, invoices…). It allows to easily use Google Storage or Amazon S3 in production.
- To store and/or apply transformations to images (resizing, cropping…), use [Thumbor](https://github.com/thumbor/thumbor).
- To add a search engine to the website, use [Algolia](https://www.algolia.com/). Alternatively, when Algolia is too limited, you may use Elasticsearch.

## Security

- Always use HTTPS (no exceptions!). Using [CloudFlare](https://www.cloudflare.com) is preferred (no Let’s Encrypt).
- Add a [strict Content Security Policy](https://csp.withgoogle.com/docs/strict-csp.html) that blocks inline JS and CSS
- Set [security headers](https://securityheaders.com)
- Change the name of the session cookie: http://symfony.com/doc/current/reference/configuration/framework.html#name
- Customize error pages: http://symfony.com/fr/doc/current/cookbook/controller/error_pages.html
- If the site isn’t public, be sure that a Symfony firewall is properly configured and working properly (add functional tests) for non public routes
- Disable GZIP/Brotli for dynamically generated pages, except if they are public: http://breachattack.com

## Performances

- Follow https://symfony.com/doc/current/performance.html
- Run Lighthouse, and fix the reported issues: https://developers.google.com/web/tools/lighthouse/
- Use Varnish, be sure that is is properly configured (check if they are some HIT)
- Setup a proper HTTP cache strategy, see:
  - https://2ndscale.com/rtomayko/2008/things-caches-do
  - https://developers.google.com/web/fundamentals/performance/- optimizing-content-efficiency/http-caching
  - https://symfony.com/doc/current/http_cache.html
  - https://api-platform.com/docs/core/performance/
- Use Blackfire when appropriate (to add automated performance tests, and to debug)

## Frontend

- Use [Yarn](https://yarnpkg.com/lang/en/) to manage dependencies
- Prefer using React.
- If you create a SPA, use the appropriate skeleton (create react app, Vue CLI or Angular CLI)
- If not, use [Webpack Encore](https://symfony.com/doc/current/frontend.html)
- No inlined JS or CSS in Twig templates.
- Always concatenate and minify assets.

## Testing and Quality

- Use a versioning system (Git + Github is prefered)
- Use a git workflow (git-flow (simple or complete) is prefered)
- Create Docker images to install the project, use them also in the CI server and - if applicable - in production
- Add a Continuous Integration system: Travis (prefered), Brigade or GitLab CI
- Write unit tests (PHPUnit), functional tests (Web Test Case or Behat + Postman for APIs) and E2E tests (Panthère or Nightwatch). Execute them automatically in the - CI server.
- Use Behat if appropriate
- Run: bin/console doctrine:schema:validate
- Run Sensiolabs security checker in the CI
- Check CS in the CI using PHP CS Fixer (PHP) and Prettier (JS)
- Use static analysis tools: [phpstan](https://github.com/phpstan/phpstan), [psalm](https://psalm.dev/) [SensioLabs Insight](https://insight.symfony.com/) (PHP), ESLint (JS)
- Check that HTML files are valid with https://github.com/validator/validator
- Deploy every branch (including feature branches), and every commit on Kubernetes, see our [Kubernetes Best Practices](kubernetes.md).

## SEO / stats / external quality

- Be sure to display correct Cookie and RGPD popups https://www.cookiebot.com
- Add a custom favicon
- Add a [robots.txt](https://developers.google.com/search/docs/advanced/robots/intro) file
- Add [Google Analytics](https://www.google.com/analytics/), or a server-side analytics tool such as [GoAccess](https://goaccess.io/)
- Add [Schema.org](https://schema.org/) metadata (JSON-LD is prefered)
- Add a [sitemap](https://www.sitemaps.org/)
- Register the website on [Google Search Console](https://search.google.com/search-console/welcome), and register the sitemaps
- Be sure that every page has a different title and meta description
- Add Twitter card markup
- Add Facebook OpenGraph markup

## A11Y

- Run http://achecker.ca/checker/
- Run React a11y (if applicable)

## Deployment

- Use [Helm](https://helm.sh/) (prefered) or Capistrano with [Travis](https://travis-ci.com) (prefered), [Brigade](https://github.com/Azure/brigade), [GitLab CI](https://about.gitlab.com/features/gitlab-ci-cd/) or [Github actions](https://docs.github.com/en/actions) (no "manual" deployment)
- It’s the action of creating a Git tag (or merging in a specific branch like master) that must trigger a deployment. To do it with Travis: https://docs.travis-ci.com/user/deployment#Conditional-Releases-with-on%3A
