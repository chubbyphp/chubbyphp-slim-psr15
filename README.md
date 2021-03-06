# chubbyphp-slim-psr15

[![Build Status](https://api.travis-ci.org/chubbyphp/chubbyphp-slim-psr15.png?branch=master)](https://travis-ci.org/chubbyphp/chubbyphp-slim-psr15)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/chubbyphp/chubbyphp-slim-psr15/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/chubbyphp/chubbyphp-slim-psr15/?branch=master)
[![Code Coverage](https://scrutinizer-ci.com/g/chubbyphp/chubbyphp-slim-psr15/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/chubbyphp/chubbyphp-slim-psr15/?branch=master)
[![Total Downloads](https://poser.pugx.org/chubbyphp/chubbyphp-slim-psr15/downloads.png)](https://packagist.org/packages/chubbyphp/chubbyphp-slim-psr15)
[![Monthly Downloads](https://poser.pugx.org/chubbyphp/chubbyphp-slim-psr15/d/monthly)](https://packagist.org/packages/chubbyphp/chubbyphp-slim-psr15)
[![Latest Stable Version](https://poser.pugx.org/chubbyphp/chubbyphp-slim-psr15/v/stable.png)](https://packagist.org/packages/chubbyphp/chubbyphp-slim-psr15)
[![Latest Unstable Version](https://poser.pugx.org/chubbyphp/chubbyphp-slim-psr15/v/unstable)](https://packagist.org/packages/chubbyphp/chubbyphp-slim-psr15)

## Description

*DEPRECATED*: Use Slim 4 instead, it got PSR15 support out of the box.

A slim psr15 adapter for middleware and request handler.

## Requirements

 * php: ^7.0
 * psr/container: ^1.0
 * psr/http-message: ^1.0.1
 * psr/http-server-middleware: ^1.0.1

## Installation

Through [Composer](http://getcomposer.org) as [chubbyphp/chubbyphp-slim-psr15][1].

```sh
composer require chubbyphp/chubbyphp-slim-psr15 "^1.1"
```

## Usage

### Middleware adapter

```php
<?php

declare(strict_types=1);

namespace App;

use App\Middleware\Psr15Middleware;
use Chubbyphp\SlimPsr15\MiddlewareAdapter;
use Slim\App;

$app = new App();
$app->add(new MiddlewareAdapter(new Psr15Middleware()));
```

### Lazy Middleware adapter

```php
<?php

declare(strict_types=1);

namespace App;

use App\Middleware\Psr15Middleware;
use Chubbyphp\SlimPsr15\LazyMiddlewareAdapter;
use Psr\Container\ContainerInterface;
use Slim\App;

/** @var ContainerInterface $container */
$container = ...;

$app = new App();
$app->add(new LazyMiddlewareAdapter($container, Psr15Middleware::class));
```

### RequestHandler adapter

```php
<?php

declare(strict_types=1);

namespace App;

use App\RequestHandler\Psr15RequestHandler;
use Chubbyphp\SlimPsr15\RequestHandlerAdapter;
use Slim\App;

$app = new App();
$app->get('/', new RequestHandlerAdapter(new Psr15RequestHandler()));
```

### Lazy RequestHandler adapter

```php
<?php

declare(strict_types=1);

namespace App;

use App\RequestHandler\Psr15RequestHandler;
use Chubbyphp\SlimPsr15\LazyRequestHandlerAdapter;
use Psr\Container\ContainerInterface;
use Slim\App;

/** @var ContainerInterface $container */
$container = ...;

$app = new App();
$app->get('/', new LazyRequestHandlerAdapter($container, Psr15RequestHandler::class));
```

## Copyright

Dominik Zogg 2019

[1]: https://packagist.org/packages/chubbyphp/chubbyphp-slim-psr15
