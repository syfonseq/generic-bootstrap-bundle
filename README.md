generic-bootstrap-bundle
========================

Very lightweight Symfony bundle to give access to jQuery and Bootstrap assets throught Assetic.
Some bugs can be there and the bundle needs some more testing, especially the setup of the scripts.

When this bundle will be enough reliable, I'll add it on Packagist.

Setup
=====

1. To install this bundle, you need to add these lines in the composer.json of your project:

{
    ...

    "repositories": [
        {
            "type": "vcs",
            "url":  "https://github.com/syfonseq/generic-bootstrap-bundle.git"
        }
    ],
    require": {
        ...
        "eutech/generic-bootstrap-bundle": "1.0.0"
    },
    "scripts": {
        "post-install-cmd": [
            // Needs to be before the script which installing assets ("Sensio\\Bundle\\DistributionBundle\\Composer\\ScriptHandler::installAssets")

            "Eutech\\Bundle\\GenericBootstrapBundle\\Composer\\ScriptHandler::symlinkAssets",
            "Sensio\\Bundle\\DistributionBundle\\Composer\\ScriptHandler::installAssets",
            ...
        ],
        "post-update-cmd": [
            // Needs to be before the script which installing assets ("Sensio\\Bundle\\DistributionBundle\\Composer\\ScriptHandler::installAssets")

            "Eutech\\Bundle\\GenericBootstrapBundle\\Composer\\ScriptHandler::symlinkAssets",
            "Sensio\\Bundle\\DistributionBundle\\Composer\\ScriptHandler::installAssets",
            ...
        ],


    ....
}


2. Register the bundle into your AppKernel:

new Eutech\Bundle\GenericBootstrapBundle\EutechGenericBootstrapBundle(),

3. Symlink the assets

php app/console assets:install --symlink
