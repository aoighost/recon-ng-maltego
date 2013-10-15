# README - Recon-ng-maltego

Welcome to Canari. You might be wondering what all these files are about. Before you can use the power of
`canari install-package` you needed to create a transform package and that's exactly what you did here! I've given you a
directory structure to use in the following manner:

* `src/recon-ng-maltego` directory is where all your stuff goes in terms of auxiliary modules that you may need for your
  modules
* `src/recon-ng-maltego/transforms` directory is where all your transform modules should be placed. An example
  `helloworld` transform is there for your viewing pleasure.
* `src/recon-ng-maltego/transforms/common` directory is where you can put some common code for your transforms like result
  parsing, entities, etc.
* `src/recon-ng-maltego/transforms/common/entities.py` is where you define your custom entities. Take a look at the
  examples provided if you want to play around with custom entities.
* `maltego/` is where you can store your Maltego entity exports.
* `src/recon-ng-maltego/resources/maltego` directory is where your `entities.mtz` and `*.machine` files can be stored for auto
  install and uninstall.
* `src/recon-ng-maltego/resources/external` directory is where you can place non-Python transforms written in other languages.

If you're going to add a new transform in the transforms directory, remember to update the `__all__` variable in
`src/recon-ng-maltego/transforms/__init__.py`. Otherwise, `canari install-package` won't attempt to install the transform.
Alternatively, `canari create-transform <transform name>` can be used within the `src/recon-ng-maltego/transforms` directory
to generate a transform module and have it automatically added to the `__init__.py` file, like so:

To test your transform, simply `cd` into the src directory and run `canari debug-transform`, like so:

```bash
$ canari debug-transform Recon-ng-maltego.transforms.helloworld Phil
%50
D:This was pointless!
%100
`- MaltegoTransformResponseMessage:
  `- Entities:
    `- Entity:  {'Type': 'test.MyTestEntity'}
      `- Value: Hello Phil!
      `- Weight: 1
      `- AdditionalFields:
        `- Field: 2 {'DisplayName': 'Field 1', 'Name': 'test.field1', 'MatchingRule': 'strict'}
        `- Field: test {'DisplayName': 'Field N', 'Name': 'test.fieldN', 'MatchingRule': 'strict'}
```

Cool right? If you have any further questions don't hesitate to drop us a line;)

Have fun!