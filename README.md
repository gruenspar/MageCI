Magento Continuous Integration Tools
====================================

A set of tools to help set up a proper environment for testing Magento.

Installation
------------

### Installation via Composer

Installation via Composer in your project is very easy.

In your application or dependent library root directory, create a _composer.json_ file.
In case you are not familiar with [Composer](http://getcomposer.org/), see [composer.json Schema](http://getcomposer.org/doc/04-schema.md).

Please add the following code to your _composer.json_ file.

```json
{
    "require": {
        "firegento/mage-ci": "dev-master"
    },
    "repositories": [
        {
            "type": "composer",
            "url": "http://packages.firegento.com"
        }
    ]
}
```

Note: You can add the dependency to the _require-dev_ part of the _composer.json_ as well.

### Installation via Bash

The installation via bash is very easy as well. Just paste either

```
bash < <(wget -O - https://raw.githubusercontent.com/firegento/MageCI/master/installer)
```

or

```
bash < <(curl -s https://raw.githubusercontent.com/firegento/MageCI/master/installer)
```

in your shell and hit enter.

Note: The installer will then download the MageCI script and place it in your current working directory where you run the command.


Usage
-----

### Running a batch of PHPUnit tests
    $ mage-ci phpunit <directory> <OPTIONS>
        Runs unit tests for all phpunit.xml or phpunit.dist.xml files in <directory> or its subdirectories.
        <OPTIONS> will be passed directly to phpunit binary.


### Installing a particular Magento version
    $ bin/mage-ci install <magento_directory> <version> <db_name> <OPTIONS>
        Installs a Magento version to a specified destination
          -c                  Create databases flag
          -t                  Create test database flag (only in combination with -c option)
          -u  <db_user>       DB Username
          -p  <db_pass>       DB Password
          -r  <sql_base_url>  SQL dumps repository url for a particular Magento version (<sql_base_url>/<version>.sql.gz)
          -f  <sql_dump_file> SQL dump file, if you'd like to preinstall some data and specfied -c option

### Installing a Magento module
    $ bin/mage-ci install-module <magento_directory> <module_dir_or_vcs_url>
        Installs a Magento module with modman definition

### Updating installed Magento modules
    $ bin/mage-ci update-modules <magento_directory>
        Updates all installed modman modules at specified Magento instnace

### Uninstalling Magento version
    $ bin/mage-ci uninstall <magento_directory> [<db_name>] <OPTIONS>
        Performs uninstall of Magento instance
          -u  <db_user>       DB Username
          -p  <db_pass>       DB Password

### Uninstalling Magento module
    $ bin/mage-ci uninstall-module <magento_directory> <module_dir_or_vcs_url>
        Performs uninstall of Magento module from instance

### Mass Install of Magento versions
    $ bin/mage-ci install-multiple <directory> <prefix> <version1> ... <versionN> <OPTIONS>
        Installs multiple version of magento at <directory> in subdirectories which name is a combined value of <prefix>-<version>
           -d  <download_dir>  Directory where all downloads are stored
           -u  <db_user>       DB Username
           -p  <db_pass>       DB Password
           -t                  Create test db as well
           -r  <sql_base_url>  SQL dumps repository url for a particular Magento version (<sql_base_url>/<version>.sql.gz)

### Dump databases of existing installed versions
    $ bin/mage-ci db-dump <directory> <prefix> <version1> ... <versionN> <OPTIONS>
        Creates Magento database dump file at <directory> directory with name <file_prefix><version>.sql.gz, the dumped database is <prefix>_<version>
           -u  <db_user>       DB Username
           -p  <db_pass>       DB Password
           -s  <file_prefix>   sql file prefix


Magento Clean DB Dumps
----------------------

It is possible to specify base url for downloading of database dump for a particular Magento version.
Most of the time clean installation of Magento takes a lot of time, so it is nice to have this clean db dump prepared for each Magento version.

We created such repository at the following url:
http://mage-ci.firegento.com

You just need to specify it during installation of process:

```bash
$ bin/mage-ci install magento-1.7.0.2 1.7.0.2 mage_1.7.0.2 -r http://mage-ci.firegento.com
```

This command will download db dump from the following URL: http://mage-ci.firegento.com/1.7.0.2.sql.gz

The following SQL dumps are provided by FireGento:

* http://mage-ci.firegento.com/1.8.1.0.sql.gz
* ..


Support
-------
If you encounter any problems or bugs, please create an issue on [GitHub](https://github.com/firegento/MageCI/issues).


Contribution
------------
Any contribution to the development of MageCI is highly welcome. The best possibility to provide any code is to open a [pull request on GitHub](https://help.github.com/articles/using-pull-requests).


Developer
---------
FireGento Team
* Website: [http://firegento.com](http://firegento.com)
* Twitter: [@firegento](https://twitter.com/firegento)

MageCI was originally developed by [EcomDev](https://github.com/EcomDev/MageCI) and also modified and extended by:

* [@daim2k5](https://twitter.com/daim2k5)
* [@therouv](https://twitter.com/therouv)


Licence
-------
[Open Software License v. 3.0 (OSL-3.0)](http://opensource.org/licenses/osl-3.0.php)


Copyright
---------

(c) 2014 FireGento Team / 2013 EcomDev BV
