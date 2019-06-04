# Manifest Format (v1)
An example `manifest.json` with all attributes filled is [here](v1/manifest.json).


### Required Attributes

##### Name
The display name of the package.

```json
{
    "name": "Marker Deleter"
}
```

##### Version
The version of the package.  Should be [Semanticly Versioned](https://semver.org/).  Other packages can require your package as a dependency using version ranges ([similar to npm](https://docs.npmjs.com/files/package.json#dependencies)).

```json
{
    "version": "1.2.3"
}
```

##### Namespace
This is the primary identifier - it is a unique name for the package.  Do not change this value once your package has been published.  It is used internally within Blish HUD for Settings and more.  Modules should not be within the `bh` namespace unless they have been contributed and approved to the base community packages.

```json
{
    "namespace": "jdoe.mypackages.markerdeleter"
}
```

##### Package
The name of your compiled module with or without ".dll" at the end.

```json
{
    "package": "Marker Deleter.dll"
}
```

##### Manifest Version
The version of manifest used.  This is currently 1.

```json
{
    "manifest_version": 1
}
```

## Recommended Attributes

##### Description
A description of the module.

```json
{
    "description": "This module allows you to select any marker and delete it."
}
```


##### Dependencies
The dependencies required for your module.  Our implementation is [similar to npm](https://docs.npmjs.com/files/package.json#dependencies).  We use [semver.net](https://github.com/adamreeve/semver.net) to verify dependency versions.

A dependency on `bh.blishhud` indicates the versions of Blish HUD the module supports.

```json
{
    "dependencies": {
        "bh.blishhud" : "~0.7.1",
        "bh.general.markersandpaths" : "~1.2.3",
    }
}
```

##### URL
A url that can be used to link to the project or a link to more details instructions.

```json
{
    "url": "https://github.com/blish-hud/manifest.json"
}
```

##### Author
The author of the module.  If there are multiple authors, use the `contributers` attribute, instead.

```json
{
    "author": {
        "name":     "Freesnöw",                   // required
        "username": "LandersXanders.1235",        // optional
        "url":      "https://github.com/dlamkins" // optional
    }
}
```

##### Contributers
If provided, it will be used instead of the `author` attribute (if `author` is provided, it will be ignored).  The attributes for each contributer match the structure of the `author` attribute.

```json
{
    "contributers": [
        {
            "name":     "Freesnöw",
            "username": "LandersXanders.1235",
            "url":      "https://github.com/dlamkins"
        },
        {
            "name":     "jdoe",
            "username": "jdoe.1234"
        }
    ]
}
```

## Optional Attributes

##### Directories
A list of directory names that are used by the module.  These directories will be registered by the `FileService` and a button to open the directory directly will be shown in the module settings.

```json
{
    "directories": ["markers"]
}
```

##### Enabled Without GW2
Allows the module to continue to run when GW2 is not running and Blish HUD is still running in the tray.  Do not set to true unless your module requires this.

```json
{
    "enabled_without_gw2": false
}
```

##### API Permissions
Gives the module permission to access the specified API permissions.  A permission can be marked as optional if the functionality of the module does not rely on the permission (the module must check for this).  A description can also be provided to provide justification to the end user as to why the permission is needed.

```json
{
    "api_permissions": {
        "account"     : { "optional": true,  "details": "Needed if you want the special feature enabled." },
        "inventories" : { "optional": false, "details": "Needed to review the item in your inventory." }
    }
}
```