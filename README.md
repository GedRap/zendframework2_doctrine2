ZendSkeletonApplication With Doctrine2 Integration
=======================

Introduction
------------
This is a simple, skeleton application using the ZF2 MVC layer and module
systems. This application is meant to be used as a starting place for those
looking to get their feet wet with ZF2.

It comes together with doctrine 2 integration (thanks to the tutorial http://marco-pivetta.com/doctrine-orm-zf2-tutorial by Marco Pivetta).


Installation
------------

Using Composer (recommended)
----------------------------
Install Composer, please refer to Composer's manual for help. Once done, switch to the skeleton's directory and run

    php composer.phar self-update
    php composer.phar install

(The `self-update` directive is to ensure you have an up-to-date `composer.phar`
available.)

Enable ZF Developer Toolbar
---------------------------
`cp vendor/zendframework/zend-developer-tools/config/zenddevelopertools.local.php.dist config/autoload/zdt.local.php`

Configure Doctrine
------------------

Create a file config/autoload/doctrine.local.php which contains the database configuration:

    return array(
        'doctrine' => array(
            'connection' => array(
                'orm_default' => array(
                    'driverClass' =>'Doctrine\DBAL\Driver\PDOMySql\Driver',
                    'params' => array(
                    'host'     => 'localhost',
                    'port'     => '3306',
                    'user'     => 'username',
                    'password' => 'password',
                    'dbname'   => 'database',
    )))));

Validate mappings by running `./vendor/bin/doctrine-module orm:validate-schema`

Generate database schema by running `./vendor/bin/doctrine-module orm:schema-tool:create`

Virtual Host
------------
Afterwards, set up a virtual host to point to the public/ directory of the
project and you should be ready to go!
