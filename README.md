# PicoXLSX ![PicoXLSX](https://rabanti-github.github.io/PicoXLSX/icons/PicoXLSX.png)![nuget](https://img.shields.io/nuget/v/picoXLSX.svg?maxAge=86400)
![license](https://img.shields.io/github/license/rabanti-github/picoXlsx.svg)[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Frabanti-github%2FPicoXLSX.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Frabanti-github%2FPicoXLSX?ref=badge_shield)

 PicoXLSX is a small .NET library written in C#, to create Microsoft Excel files in the XLSX format (Microsoft Excel 2007 or newer) in an easy and native way

* **No dependencies** (\*
 * No need for an installation of Microsoft Office
 * No need for Office interop libraries
 * No need for 3rd party libraries
 * No need for an installation of the Microsoft Open Office XML SDK (OOXML)

**Please have a look at the successor library [NanoXLSX](https://github.com/rabanti-github/NanoXLSX) for reader support.**

Project website: [https://picoxlsx.rabanti.ch](https://picoxlsx.rabanti.ch)
 
See the **[Change Log](https://github.com/rabanti-github/PicoXLSX/blob/master/Changelog.md)** for recent updates.


# What's new in version 2.x
* Complete replacement of the old style handling
* Added asynchronous methods to save workbooks as files or streams
* Added appending of styles for an easier composition of complex styles
* Added more options to assign styles to cells
* Added Shortener (property WS) to reduce the code overhead
* Added static methods for the most important formulas (round, floor, ceil, min, max, average, median, sum, vlookup)
* Added Save option to save the XLSX file as stream
* Added an option for sanitizing of worksheet names
* Replaced specific exception classes with general exceptions (e.g. StyleException, FormatException or WorksheetException)
* Added functions to retrieve stored data and the current cell address
* Many internal optimizations and additional documentation

# Requirements
PicoXLSX was created with .NET version 4.5. Newer versions like 4.6.1 are working and tested. Older versions like 3.5 and 4.0 may also work with minor or no changes. However, this was not tested yet.

\*) The only requirement to compile the library besides .NET is the assembly **WindowsBase**. This assembly is a **standard component in all Microsoft Windows systems** (except Windows RT systems). If your IDE of choice supports referencing assemblies from the Global Assembly Cache (**GAC**) of Windows, select WindowsBase from there. If you want so select the DLL manually and Microsoft Visual Studio is installed on your system, the DLL can be found most likely under "c:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll", according to this [MSDN Blog entry](http://blogs.msdn.com/b/dmahugh/archive/2006/12/14/finding-windowsbase-dll.aspx). Otherwise you find it in the GAC, under "c:\Windows\Microsoft.NET\assembly\GAC_MSIL\WindowsBase".


If you want to compile the documentation project (folder: Documentation; project file: shfbproj), you need also the **[Sandcastle Help File Builder (SHFB)](https://github.com/EWSoftware/SHFB)**. It is also freely available. But you don't need the documentation project to build the PicoXLSX library.

# Installation

## Using Nuget
By Package Manager (PM): 
```sh 
Install-Package PicoXLSX
```
By .NET CLI: 
```sh 
dotnet add package PicoXLSX
```
## As DLL
Simply place the PicoXLSX DLL into your .NET project and add a reference to it. Please keep in mind that the .NET version of your solution must match with the runtime version of the PicoXLSX DLL (currently compiled with 4.5).
## As source files
Place all .CS files from the PicoXLSX source folder into your project. You can place them into a sub-folder if you wish. The files contains definitions for workbooks, worksheets, cells, styles, meta-data, low level methods and exceptions.

# Usage
## Quick Start (shortened syntax)
```c#
 Workbook workbook = new Workbook("myWorkbook.xlsx", "Sheet1");         // Create new workbook with a worksheet called Sheet1
 workbook.WS.Value("Some Data");                                        // Add cell A1
 workbook.WS.Formula("=A1");                                            // Add formula to cell B1
 workbook.WS.Down();                                                    // Go to row 2
 workbook.WS.Value(DateTime.Now, Style.BasicStyles.Bold);               // Add formatted value to cell A2
 workbook.Save();                                                       // Save the workbook as myWorkbook.xlsx
```

## Quick Start (regular syntax)
```c#
 Workbook workbook = new Workbook("myWorkbook.xlsx", "Sheet1");         // Create new workbook with a worksheet called Sheet1
 workbook.CurrentWorksheet.AddNextCell("Some Data");                    // Add cell A1
 workbook.CurrentWorksheet.AddNextCell(42);                             // Add cell B1
 workbook.CurrentWorksheet.GoToNextRow();                               // Go to row 2
 workbook.CurrentWorksheet.AddNextCell(DateTime.Now);                   // Add cell A2
 workbook.Save();                                                       // Save the workbook as myWorkbook.xlsx
```

## Further References
See the full **API-Documentation** at: [https://rabanti-github.github.io/PicoXLSX/](https://rabanti-github.github.io/PicoXLSX/).


The [Demo project](https://github.com/rabanti-github/PicoXLSX/tree/master/Demo) contains 14 simple use cases. You can find also the full documentation in the [Documentation-Folder](https://github.com/rabanti-github/PicoXLSX/tree/master/docs) (html files or single chm file) or as C# documentation in the particular .CS files.

See also: [Getting started in the Wiki](https://github.com/rabanti-github/PicoXLSX/wiki/Getting-started)


## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Frabanti-github%2FPicoXLSX.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Frabanti-github%2FPicoXLSX?ref=badge_large)