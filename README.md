# Loady
A simple and lightweight php autoloader

#### USAGE
include it once near the top of your current PHP file.

<?php 
```php
require Loady.php
```
Then create a new Loady object. You can either provide the document root at the initialization of Loady or at the initialize method.
```php
	$loader 	= new Loady\Loady( 'document_root' );
```
Or

```php
	$loader 	= new Loady\Loady;
	$loader->initialize( 'document_root' );
```
Examples on how to set the file(s) to be autoloaded.

PSR-4 compliant
```php
	$loader->setPsr4([
		'Namespace\\'	=> 'path/'
	]);
	// or 
	$loader->addPsr4( 'Namespace\\', 'path/' );
```
Classmap
```php
	$loader->setClassMap([
		'classname'	=> 'path/',
		'namespace\classname' => 'path/'
	]);
	// or 
	$loader->addClassMap( 'classname', 'path/' );
```
Autoload Files
```php
	$loader->setFiles([
		'path/to/file.php'
	]);
	//or
	$loader->addFile('path/to/file.php');
```
The setAuto method can either take an array of file and directory or a file or directory. If a directory is provided Loady will try to load all the classes inside that directory.
```php
	$loader->setAuto([
		'directory/',
		'path/to/class.php'
	]);
	// or
	$loader->setAuto('directory/');
	// or
	$loader->setAuto('path/to/class.php');
```
Then register the autoloader.
```php
	$loader->register();
```
By default Loady will will prepend the autoloader on the autoload queue to append the autoloader just
```php
	$loader->register(false);
```
Loady comes with a built in caching of all the files you have set to be autoloaded and by default caching is on. 
By default Loady will try to find a cache directory with load.cache file it is here where Loady will cache the files. 
To change the default cache file just use setCacheFile method. 
Also please provide the necessary permission so that Loady can write and read the cache file.
```php
	$loader->setCacheFile('cachedir/cachefile.cache');
	// or if it is located in a different document root
	$loader->setCacheFile('otherdocumentroot/cachedir/cachefile.cache');
```
If you don't want caching just 
```php
	$loader->register(true, false);
```
##Requirements
* __PHP 5.4+__

##Installation
For now install it by clicking download zip then unzip and include it in your project's directory.
