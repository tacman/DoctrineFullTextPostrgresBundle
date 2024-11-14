DoctrineFullTextPostrgresBundle
===================================

Symfony2 Bundle for the <a href="https://github.com/jaimz22/DoctrineFullTextPostrgres">DoctrineFullTextPostgres package</a>

## Install

Add the DoctrineFullTextPostgresBundle to your composer.json:

```js
{
    "require": {
        "vertigolabs/doctrine-full-text-postgres-bundle": "v1.0"
	}
}
```

Or require it directly with composer:

```bash
$ php composer.phar require vertigolabs/doctrine-full-text-postgres-bundle:v1.0
```

The bundle will be installed in your projects vendor directory in ```vertigolabs/doctrine-full-text-postgres-bundle/```

## Enable

Add the bundle to your kernel:

```php
<?php
// app/AppKernel.php

public function registerBundles()
{
    $bundles = array(
    	//...
    	new VertigoLabs\DoctrineFullTextPostgresBundle(),
    );
}
```

## Configure Doctrine

The bundle should handle this automatically.

```yml
# Doctrine Configuration
doctrine:
    dbal:
        types:
            tsvector: VertigoLabs\DoctrineFullTextPostgres\DBAL\Types\TsVector
        mapping_types:
        	tsvector: tsvector
    orm:
        entity_managers:
            default:
                dql:
                    string_functions:
                        tsquery: VertigoLabs\DoctrineFullTextPostgres\ORM\Query\AST\Functions\TsQueryFunction
                        tsrank: VertigoLabs\DoctrineFullTextPostgres\ORM\Query\AST\Functions\TsRankFunction
                        tsrankcd: VertigoLabs\DoctrineFullTextPostgres\ORM\Query\AST\Functions\TsRankCDFunction

services:
    vertigolabs.doctrinefulltextpostgres.listener:
        class: VertigoLabs\DoctrineFullTextPostgres\Common\TsVectorSubscriber
        tags:
            - { name: doctrine.event_subscriber, connection: default }
```

## Usage

refer to the <a href="https://github.com/jaimz22/DoctrineFullTextPostrgres/blob/master/README.md#usage" target="_blank">read me for the DoctrineFullTextPostgres package for usage instructions</a>
