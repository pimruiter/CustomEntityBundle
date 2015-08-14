# CustomEntityBundle

[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/akeneo/CustomEntityBundle/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/akeneo/CustomEntityBundle/?branch=master)
[![Build Status](https://travis-ci.org/akeneo/CustomEntityBundle.svg?branch=master)](https://travis-ci.org/akeneo/CustomEntityBundle)

## Purpose
Eases the creation of PIM reference datas and related views in the PIM.

For more information, please see http://docs.akeneo.com/

## Requirements

| CustomEntityBundle   | Akeneo PIM Community Edition |
|:--------------------:|:----------------------------:|
| (in progress) v1.6.* | dev-master (release v1.4.*)  |
| v1.5.0-RC1           | v1.3.*                       |
| v1.4.*               | v1.2.*                       |
| v1.3.*               | v1.2.*                       |
| v1.2.*               | v1.1.*                       |
| v1.1.*               | v1.1.*                       |

## Installation
You can install this bundle with composer (see requirements section):

    $ php composer.phar require akeneo/custom-entity-bundle:1.6.*

Then add the following lines **at the end** of your app/config/routing.yml :

    pim_customentity:
        prefix: /enrich
        resource: "@PimCustomEntityBundle/Resources/config/routing.yml"

Then enable the bundle in the `app/AppKernel.php` file in the registerBundles() method:

    $bundles = [
        // ...
        new Pim\Bundle\CustomEntityBundle\PimCustomEntityBundle(),
    ]

Then, you've to load the following job fixtures if you want to use the quick export and/or the mass edit features.
Job fixture is defined in [Resources/fixtures/jobs.yml] file and you can copy/paste it to your installer.
If you're in a production environment and you can't reinstall your PIM, you can use the `akeneo:batch:create-job` command like:

    $ php app/console akeneo:batch:create-job "Akeneo Mass Edit Connector" "reference_data_quick_export" "quick_export" "csv_reference_data_quick_export" "{\"delimiter\":\";\",\"enclosure\":\"\\\"\",\"withHeader\":true,\"filePath\":\"\\/tmp\\/reference_data_quick_export.csv\"}"


## Documentation

Some example usages for this bundle can be found in the [PIM documentation](http://docs.akeneo.com/master/cookbook/custom_entity/index.html)

The full documentation for the bundle can be found in the [Resources/doc](Resources/doc/index.rst) folder.
