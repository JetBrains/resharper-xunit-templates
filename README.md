# ReSharper Live Templates for xUnit.net

This extension adds various Live Templates for [xUnit.net](http://xunit.github.io/) to ReSharper.

Check out the [README](templates/README.md) for details on the available templates.

## Installation

To install, go to ReSharper &rarr; Extension Manager and search for "xunit live templates". Once installed, the templates are automatically available, and can be seen in the . They can be temporarily disabled by unchecking the appropriate entry in the ReSharper &rarr; Manage Options dialog.

## Contributing

The templates are distributed in a `.dotSettings` file, which is not designed to be a human-readable file, and is very difficult to work with in an editor. In order to modify or add templates, you can either edit the templates in ReSharper's Live Template editor, or in the markdown files in the `templates` folder, and running the template "compiler" program to generate the `.dotSettings` file.

Make sure that any new templates have the appropriate categories and language set.

### Editing in ReSharper

* Add the `templates.dotSettings` file in the ReSharper &rarr; Manage Options dialog. Select "This Computer", click the "plus" add icon and select "Open Settings File". Navigate to `templates.dotSettings` and select it.
* Open the Live Templates editor (ReSharper &rarr; Tools &rarr; Templates Editor)
* Select the `templates.dotSettings` file in the Layer drop down in the top left of the editor. This is **VERY IMPORTANT**. This means any new templates, or edits to the existing templates are saved into the `templates.dotSettings` file. Without selecting this layer, the changes will be save to the "This Computer" layer.
* Edit or add new templates. They will be automatically saved, as you update them.

### Editing markdown files

All of the templates are saved as markdown files, which makes it convenient to [browse and document](templates/README.md), as well as edit outside of ReSharper. The markdown files are processed with a small app that will translate between the required `.dotSettings` format, and the markdown files. Metadata is stored as [YAML "front matter"](https://jekyllrb.com/docs/frontmatter/).

* Edit an existing file, or add a new file (use an existing file as a guide). If you are adding a new file, make sure to give the file a new GUID.
* Save the file, and run `rstc compile -i *.md -o templates.dotSettings`. The `rstc.exe` file is in the `bin` folder.
* The `templates.dotSettings` file, as well as the `README.md` file are updated, ready for commit.

For more details, see [the resharper-template-compiler project](https://github.com/citizenmatt/resharper-template-compiler#readme).

* In order to update the markdown files after editing the `templates.dotSettings` file in ReSharper, run `rstc decompile templates.dotSettings`. It might be necessary to also run `rstc compile -i *.md -o foo.dotSettings` in order to regenerate `README.md`.

## History

These templates started life in the xunit plugin for ReSharper. Since ReSharper 2016.1, xunit support is built in to ReSharper, meaning the xunit plugin is no longer required. However, it is not appropriate to ship these templates by default, as they will not apply to all users. Hence they are available as a separate extension.
