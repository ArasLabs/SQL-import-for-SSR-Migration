# SQL Import Tool

This pacakge imports an Action which allows you to take a SQL query and convert it into a Query Definition (QD). It also has functionality to generate a report based on the generated Query Definition.

The intended use of this is to migrate Self Service Reports (SSR) to the new Reporting capability. Instructions on how to export your SSRs as SQL queries will be included in the usage instructions below.

## Project Details

**Built Using:** C# .NET

> Please note that each release of this project is version-dependent. To avoid potential errors, please ensure that you download the release of this project corresponding to your installed version of Aras Innovator.

## History
Release | Notes
--------|--------
[V1.0](https://github.com/ArasLabs/toc-search-bar/releases/tag/R31) | First release.

#### Supported Aras Versions

Project | Aras
--------|------
[v1.0]()| Releases 28-31

## Installation

#### Important!
**Always back up your code tree and database before applying an import package or code tree patch!**

### Pre-requisites

1. Aras Innovator installed (Releases 28-31)

### Install Steps

1. Backup your code tree
	* This project makes modifications to core files, so it is highly recommended that you backup your files first
2. Open the `Method-config.xml` file within your `Innovator/Server` folders.
3. In the `<ReferencedAssemblies>` tag, add the following line: `<name>$(binpath)/Microsoft.SqlServer.TransactSql.ScriptDom.dll</name>`
4. Within the CSharp Template (around line 300) add the following Using directive to the collection at the top `using Microsoft.SqlServer.TransactSql.ScriptDom;`
5. Reset IIS

You are now ready to login to Aras and try out this TOC Search Bar.

## Usage

This tool is intended to be used to take the exported SQL of a Self Service Report and transform that into a Query Definition and Report. 

NOTE: The export process is only possible for instances where you have access to Izenda libraries, meaning you can not export your SQL from 31+. 

To export your SSR as a SQL Statement:

1. Log into Aras as a user who can edit the SSR you wish to export.
2. Open and Edit the desired SSR.
3. In the upper toolbar, select the `Export to SQL` option. This button only shows up when the SSR is in edit mode.
4. The SSR has been exported to a local txt file on your machine. The export could be broken up into a few sections. We only care about the `Detail` portion of this file. 
5. Copy everything under `Detail`

To import your SQL into your new Query Definition:

1. Log in to Aras as admin. If you want to generate Reports, make sure admin has that permission.
2. Click your User Icon in the top right of the screen.
3. Under `Actions` click `Import S would for Report Generation`
4. Paste the SQL excerpt from the previous section into the SQL text area, set a name for your QD, and select whether or not you would like a Report to be generated as well.  
5. Click the Submit button to create your QD and Report!

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request

For more information on contributing to this project, another Aras Labs project, or any Aras Community Project, shoot us an email at araslabs@aras.com.

## Credits

Project created by Aras Development and AJ Sebastian at Aras Labs. @asebastian-aras

## License

Aras Labs projects are published to Github under the MIT license. See the [LICENSE file](./LICENSE.md) for license rights and limitations.