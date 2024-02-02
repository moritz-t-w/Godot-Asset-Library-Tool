# Godot Asset Library Tool

Submit your assets to the [Godot Asset Library](https://godotengine.org/asset-library/assets) with ease.

## How it works

GALT creates a GitHub repository for your asset with your source repository as a subtree and necessary files for the Asset Library. This is to avoid the need to have the nonstandard directory structure required by the Asset Library in your source repository, which allows you to keep your source repository organized and modular.

## Automatic partial compliance with [Submission guidelines](https://docs.godotengine.org/en/latest/community/asset_library/submitting_to_assetlib.html)

Using GALT you can get some of the requirements and recommendations for submitting an asset to the Asset Library fulfilled automatically:

> ### Requirements
>
> [[...]](https://docs.godotengine.org/en/latest/community/asset_library/submitting_to_assetlib.html#requirements)

> - [ ] The asset must work. If the asset doesn't run or otherwise doesn't work in the specified Godot version, then it will be rejected.

Testing is not currently in scope for GALT.

> - [x] The asset must have a proper .gitignore file. It's important to keep redundant data out of the repository. [...]

Your `.gitignore` file will be automatically copied to the root of the distribution repository.

> - [x] No submodules, or any submodules must be non-essential. GitHub does not include submodules in the downloaded ZIP file, so if the asset needs the contents of the submodule, your asset won't work.

Submodules are replaced with subtrees in the distribution repository. The source repository is also referenced as a subtree in the distribution repository.

> - [x] The license needs to be correct. The license listed on the asset library must match the license in the repository. The repo MUST have a license file, called either "LICENSE" or "LICENSE.md". This file must contain the license text itself and a copyright statement that includes the year(s) and copyright holder.

Your `LICENSE` file will be automatically copied to the root of the distribution repository.

> - [ ] Use proper English for the name and description of your asset. This includes using correct capitalization, and using full sentences in the description. You can also include other languages, but there should at least be an English version.

Linting is not currently in scope for GALT.

> - [ ] The icon link must be a direct link. For icons hosted on GitHub, the link must start with "raw.githubusercontent.com", not "github.com".

This has to be done manually. [^1]

> ### Recommendations
>
> [[...]](https://docs.godotengine.org/en/latest/community/asset_library/submitting_to_assetlib.html#requirements)

> - [x] When creating non-project assets, it is common practice to place your files inside of an addons/asset_name/ folder. Do this to avoid having your files clash with other assets, or with the files of users installing your asset. This folder will not be automatically generated when a user installs your asset.

The purpose of GALT is to create a distribution repository that is ready to be used as an asset. The source repository is referenced as a subtree in the distribution repository under `addons/<asset_name>`, where `<asset_name>` is replaced with the name of the asset.

> - [ ] Fix or suppress all script warnings. The warning system is there to help identify issues with your code, but people using your asset don't need to see them.

Testing is not currently in scope for GALT.

> - [ ] Make your code conform to the official style guides. Having a consistent style helps other people read your code, and it also helps if other people wish to contribute to your asset. See: the GDScript style guide or the C# style guide.

Linting is not currently in scope for GALT.

> - [ ] If you have screenshots in your repo, place them in their own subfolder and add an empty .gdignore file in the same folder (note: gd, not git). This prevents Godot from importing your screenshots. On Windows, open a command prompt in the project folder and run type nul > .gdignore to create a file whose name starts with a period.

This has to be done manually, since GALT can't just decide which files should be imported and which shouldn't. [^1]

> - [ ] If your asset is a library for working with other files, consider including example files in the asset.

Example files belong in the source repository, not the distribution repository, so this has to be done manually. [^1]

> - [x] Consider adding a .gitattributes file to your repo. This file allows giving extra instructions to Git, such as specifying line endings and listing files not required for your asset to function with the export-ignore directive. This directive removes such files from the resulting ZIP file, preventing them from being downloaded by the asset library users. [...]

GALT will automatically create a `.gitattributes` file in the distribution repository to comply with godot's line endings and to exclude non-essential files.

[^1]: GALT will not modify the source repository or the copy of it inside the distribution repository.
