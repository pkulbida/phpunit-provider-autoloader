PHPUnit Provider Autoloader
===========================

> Magic helper to autoload CSV, JSON, PHP, XML and YAML data provider in PHPUnit.

[![Build Status](https://img.shields.io/travis/redaxmedia/phpunit-provider-autoloader.svg)](https://travis-ci.org/redaxmedia/phpunit-provider-autoloader)
[![Packagist Version](https://img.shields.io/packagist/v/redaxmedia/phpunit-provider-autoloader.svg)](https://packagist.org/packages/redaxmedia/phpunit-provider-autoloader)
[![License](https://img.shields.io/packagist/l/redaxmedia/phpunit-provider-autoloader.svg)](https://packagist.org/packages/redaxmedia/phpunit-provider-autoloader)


Installation
------------

```
composer require redaxmedia/phpunit-provider-autoloader
```


Usage
-----

Create the `TestCaseAbstract` for your testing suite:

```php
<?php
namespace ExampleProject\Tests;

use PHPUnitProviderAutoloader;

/**
 * TestCaseAbstract
 *
 * @since 4.0.0
 *
 * @package ExampleProject
 * @category Tests
 */

abstract class TestCaseAbstract extends PHPUnitProviderAutoloader\TestCaseAbstract
{
	/**
	 * directory of the provider
	 *
	 * @var string
	 */

	protected $_providerDirectory = 'tests' . DIRECTORY_SEPARATOR . 'provider';
    	
	/**
	 * namespace of the testing suite
	 *
	 * @var string
	 */

	protected $_testNamespace = __NAMESPACE__;
}
```

Extend `ExampleTest` from `TestCaseAbstract` and set `@dataProvider` as needed:

```php
<?php
namespace ExampleProject\Tests;

/**
 * ExampleTest
 *
 * @since 4.0.0
 *
 * @package ExampleProject
 * @category Tests
 */

class ExampleTest extends TestCaseAbstract
{
	/**
	 * testMethod
	 *
	 * @since 4.0.0
	 *
	 * @param string $expect
	 *
	 * @dataProvider providerAutoloader
	 */

	public function testMethod(string $expect = null) : void
	{
		$this->assertEquals($expect, 'test');
	}
}
```

Create the `ExampleTest{_testMethod}.{csv|json|php|xml|yml}` file:

```json
[
	[
		"test"
	]
]
```
