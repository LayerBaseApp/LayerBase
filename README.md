# LayerBase

### Every File. Every Print. Every Setting. One Searchable Database.

LayerBase is a local, searchable library for organizing, comparing, rating, and understanding your 3D-printing files.

It was created primarily for OrcaSlicer-generated G-code, but LayerBase can also organize STL files and other supporting files associated with your prints.

> **Project status:** LayerBase is currently under active development and is being released for testing. Features, database structures, and installation procedures may change before the first stable release.

---

## Why LayerBase Exists

3D-printer calibration is an iterative process.

You change a setting, print a test, inspect the result, make another adjustment, and repeat. After several iterations, it can become difficult to remember:

* Which settings changed between prints
* Which file produced the best result
* Whether a problem started after a specific adjustment
* Whether gradual “parameter creep” has moved a once-reliable profile away from its original settings
* Which retraction, pressure advance, speed, temperature, or acceleration values were used months ago
* Why an older print looked better than the same model printed today

The information may still exist inside your G-code files, but manually comparing thousands—or hundreds of thousands—of lines of G-code is time-consuming and difficult to interpret.

File names alone rarely tell the full story. Notes get lost, slicer profiles change, and older G-code files are eventually overwritten or forgotten.

**LayerBase was created to solve that problem.**

LayerBase extracts useful settings and metadata from your G-code files and places them into a searchable, readable database. Instead of opening files individually or trying to remember which settings were used, you can search, compare, tag, rate, and organize them from one interface.

LayerBase turns a folder full of G-code into a history of your printing decisions.

---

## What LayerBase Does

### Compare G-code Settings

Select multiple G-code files and compare their settings side by side.

LayerBase can help identify changes involving:

* Filament and material settings
* Nozzle and bed temperatures
* Flow ratio
* Pressure advance
* Maximum volumetric flow
* Retraction and deretraction
* Wipe settings
* Z-hop
* Layer height and line width
* Wall and shell counts
* Infill
* Print speeds
* Acceleration
* Supports
* Seam settings
* Other settings exported by OrcaSlicer

Differences are presented in a readable format so you do not have to search through raw G-code manually.

This makes it easier to answer questions such as:

* What changed between these two calibration prints?
* Why did this older file print better?
* When did my retraction settings change?
* Which file used the lower outer-wall acceleration?
* Did I accidentally change a setting while tuning something unrelated?

---

### Search Your Printing History

Search your library using file information, extracted settings, ratings, tags, and other metadata.

Examples include:

* Find every file printed with ASA
* Find files using a specific filament brand
* Find files with a particular layer height
* Find files within a range of retraction values
* Find files sliced for a specific printer
* Find highly rated files
* Find files that have never been rated
* Find older files that used a particular pressure-advance value
* Find files by name, tag, source, or location

Advanced searches can be saved and reopened later. Multiple searches can remain open at the same time, allowing you to investigate different groups of files without repeatedly rebuilding your filters.

---

### Rate Your G-code

A file that printed successfully is more valuable than a file that simply exists.

LayerBase lets you rate G-code files so you can quickly identify files and settings that produced good—or poor—results.

Ratings can include an overall score along with more detailed print-quality observations, such as:

* Warping
* Stringing
* Layer shifting
* Over-extrusion or under-extrusion
* First-layer adhesion
* Surface quality
* Dimensional accuracy

This creates a connection between the settings contained in a file and the real-world result produced by those settings.

---

### Tag and Organize Files

Create your own tags and apply them to G-code or STL files.

Possible tags might include:

* Calibration
* Final
* Needs retuning
* Good surface finish
* Dimensional test
* Customer project
* Replacement part
* High-speed profile
* Known-good settings

Tags make it possible to organize files according to your own workflow rather than relying entirely on filenames or folders.

---

### Create Lists

Save important files to custom lists.

Lists can be used for:

* Favorite G-code
* Known-good calibration files
* Frequently printed models
* Files to print again
* Files that need testing
* Files associated with a particular printer or project

Your files can belong to more than one list, allowing you to organize the same file in different ways without creating duplicate copies.

---

### Organize STL Files

Comparative G-code analysis was the original goal of LayerBase. However, once a searchable file library existed, it made sense to expand its purpose.

LayerBase can also be used to organize STL files.

You can:

* Search for STL files
* Tag them
* Rate them
* Add them to lists
* Associate them with projects or categories
* Keep them alongside the G-code files created from them

LayerBase does not attempt to replace a dedicated CAD program or slicer. It provides a central place to organize the files involved in your printing workflow.

It is your library—organize it in the way that works best for you.

---

## What LayerBase Is Not

### LayerBase Is Not a 3D-Printer Dashboard

LayerBase is intentionally not a printer-control dashboard.

Klipper interfaces such as Fluidd and Mainsail already provide excellent tools for:

* Controlling printers
* Monitoring temperatures
* Starting and stopping prints
* Viewing webcams
* Running macros
* Managing active print jobs

Other mature printer-management platforms provide similar capabilities.

LayerBase is not intended to duplicate those tools, and it will not evolve into a replacement for Fluidd, Mainsail, KlipperScreen, or another printer dashboard.

**LayerBase is a database and file-management tool.**

Its purpose is to preserve, organize, compare, and search the information associated with your prints.

Limited printer integration may be included where it directly supports that purpose—for example, identifying which printer a file came from or sending a previously saved file back to a printer. However, active printer control is outside the scope of the project.

### LayerBase Is Also Not:

* A slicer
* A CAD application
* A replacement for Klipper or Moonraker
* A cloud-printing service
* A substitute for properly backing up your files and database

---

## Core Design Principles

### Local First

LayerBase is designed to run on hardware you control. Your G-code, STL files, ratings, tags, and print history remain on your own system.

### Searchable

Important information should not remain buried inside filenames, folders, slicer profiles, or raw G-code.

### Printer Independent

LayerBase is designed to organize files from more than one printer and more than one storage location.

### Focused

LayerBase should complement existing slicers and printer dashboards rather than trying to replace them.

### Useful Over Time

The value of LayerBase grows as your library grows. A single file contains settings; a collection of files can reveal trends, successful combinations, and unintended changes.

---

## Current File Support

The initial parser and comparison tools are being developed around G-code generated by **OrcaSlicer**.

Other slicers may place settings and metadata in different locations or use different naming conventions. Files from other slicers may be stored in the library, but complete setting extraction should not be assumed unless that slicer is specifically listed as supported.

STL files can be cataloged and organized, but they do not contain the same print-setting information as sliced G-code.

A formal compatibility list will be maintained as additional slicers and file formats are tested.

---

## System Requirements

### Recommended Minimum Hardware

For the initial release, the recommended minimum system is:

* A dedicated Raspberry Pi 3 B+ or better
* A reliable microSD card or SSD
* A wired or wireless network connection
* Enough storage for the G-code and STL library
* A supported Linux operating system
* A modern web browser on the device used to access LayerBase

A Raspberry Pi 4, Raspberry Pi 5, mini PC, home server, or similar Linux computer should provide improved responsiveness, particularly with large libraries, complex searches, and multiple simultaneous users.

### Lower-Powered Devices

LayerBase may run on lower-powered Linux single-board computers, such as a Raspberry Pi Zero 2 W, but performance may be reduced. Large scans, comparisons, STL previews, and complex searches may take longer.

These configurations should be considered experimental until they have been tested more extensively.

### Raspberry Pi Pico Is Not Supported

A Raspberry Pi Pico or Pico W is a microcontroller, not a Linux single-board computer. It cannot run the Linux, Python, Flask, database, and web-server environment required by LayerBase.

### Other Linux Computers

LayerBase should also run on other Linux-based computers, including:

* Desktop computers
* Laptops
* Mini PCs
* Home servers
* Virtual machines
* Compatible NAS or container hosts

The exact supported operating systems and architectures will be documented as testing expands.

---

## Running LayerBase on a Printer’s Existing Raspberry Pi

A dedicated device is recommended.

LayerBase has not yet been thoroughly tested on the same Raspberry Pi that is actively running Klipper, Moonraker, Fluidd, Mainsail, KlipperScreen, webcam streaming, or timelapse rendering.

Running LayerBase on the printer’s existing host may be possible, but it could introduce additional CPU, memory, storage, or disk-I/O load. This is especially important on older Raspberry Pi models.

Users who choose this configuration should proceed cautiously and monitor:

* CPU usage
* Memory usage
* CPU temperature
* Storage capacity
* Undervoltage warnings
* Klipper timing warnings
* Webcam and timelapse performance
* Print reliability during library scans or database operations

Until more testing has been completed, a dedicated Raspberry Pi 3 B+ or better is the safer configuration.

---

## Storage Considerations

The application itself should require relatively little storage. The size of the complete installation will depend primarily on:

* The number and size of G-code files
* The number and size of STL files
* Whether files are copied into the LayerBase library or indexed in their existing locations
* Stored previews or thumbnails
* Archived files
* Database backups
* Future print-history images or attachments

Users with large STL collections may benefit from using an SSD or network storage rather than relying entirely on a small microSD card.

Regular backups of both the database and file library are strongly recommended.

---

## Network and Security Considerations

LayerBase is initially intended for use on a trusted local network.

Until authentication, permissions, and remote-access security have been fully reviewed, LayerBase should not be exposed directly to the public internet.

For remote access, a private networking solution such as a VPN or secure mesh network is preferable to opening the LayerBase port directly through a router.

Users are responsible for securing the host operating system, network access, backups, and any external storage locations used by LayerBase.

---

# Installation

> The following section describes the intended installation process. Final commands and automated installation scripts will be added when the release build is ready.

## Installation Overview

The planned installation process will include the following steps.

### 1. Prepare the Host

Install a supported 64-bit Linux operating system.

Raspberry Pi users will most likely use a current Raspberry Pi OS Lite installation. A desktop environment should not be required because LayerBase is accessed through a web browser.

The host should have:

* Network access
* A configured username and password
* SSH access, if the installation will be performed remotely
* Correct date and time settings
* Sufficient free storage

### 2. Update the Operating System

Before installing LayerBase, update the operating system and installed packages.

This reduces the likelihood of dependency conflicts and ensures that current security updates are installed.

### 3. Install Required System Packages

The final installation guide will provide the required packages.

These are expected to include:

* Git
* Python 3
* Python virtual-environment support
* Python package-management tools
* Required database libraries
* Required image or file-processing libraries
* A production web server
* Any system libraries needed for STL previews or metadata extraction

### 4. Download LayerBase

Clone or download the LayerBase repository from GitHub into a dedicated installation directory.

The final guide will include:

* The recommended installation path
* The stable-release branch or tag
* Instructions for updating an existing installation
* Instructions for returning to a previous version if an update fails

### 5. Create the Python Environment

LayerBase will use an isolated Python environment so its dependencies do not interfere with system Python packages or other applications installed on the host.

The final installer will create this environment and install the versions listed in the project’s dependency file.

### 6. Configure LayerBase

Initial configuration will include items such as:

* Database location
* G-code library folders
* STL library folders
* Archive location
* Temporary-file location
* Application port
* Printer names
* Source names
* File-scan behavior
* Backup location
* Optional printer connections

Configuration should be possible through either an initial setup process or clearly documented configuration files.

### 7. Initialize the Database

LayerBase will create its database and required tables during installation or first launch.

Future releases will include a migration process so the database can be updated without requiring users to rebuild their library after every software update.

### 8. Scan Existing Files

After configuration, LayerBase will scan the selected folders and add supported files to the database.

The first scan may take longer depending on:

* Library size
* Storage speed
* Device performance
* Number of settings extracted from each G-code file
* Number and size of STL files

Files should remain in their original locations unless the user specifically chooses to import, copy, move, or archive them.

### 9. Install the Background Service

The production installation will run LayerBase as a system service.

This will allow LayerBase to:

* Start automatically when the host boots
* Restart after a failure
* Run without an open terminal
* Write application logs to a predictable location
* Be managed using standard Linux service tools

### 10. Open the Web Interface

After installation, LayerBase will be accessed from a web browser using the host’s IP address or local hostname and the configured application port.

The first-run process may ask the user to:

* Confirm library folders
* Name the installation
* Add printers
* Select visible settings
* Perform the first library scan
* Configure backup preferences

### 11. Connect Printer File Locations

Printer G-code folders may be added using methods such as:

* A network share
* Syncthing
* A mounted remote folder
* A scheduled synchronization process
* A manually copied directory
* A future supported Moonraker connection

Synchronization tools are separate from LayerBase. Their setup and security requirements will be documented independently where appropriate.

### 12. Verify the Installation

The final installation guide will include a verification checklist covering:

* Web-interface access
* Database status
* Folder permissions
* File scanning
* G-code parsing
* STL detection
* Search
* Comparison
* Logging
* Automatic startup
* Backup creation

---

## Updating LayerBase

A stable update process will be documented before the final release.

The update process should:

1. Stop the LayerBase service.
2. Back up the database and configuration.
3. Download the selected release.
4. Update application dependencies.
5. Apply any required database migrations.
6. Restart LayerBase.
7. Verify the application version and library status.

Users should avoid updating during active database scans or file operations.

Pre-release testers should review release notes before installing an update because database structures and settings may change between development versions.

---

## Backing Up LayerBase

A complete LayerBase backup should include:

* The LayerBase database
* Configuration files
* User-created tags
* Ratings
* Lists
* Saved searches
* Printer and source definitions
* Archived files
* Any locally managed G-code or STL files
* Optional previews, images, or print-history attachments

Backing up only the program files is not sufficient.

The final release will document recommended manual and automated backup procedures.

---

## Uninstalling LayerBase

The final uninstall procedure will explain how to remove:

* The LayerBase service
* Application files
* Python dependencies
* Logs
* Temporary files

The database, configuration, and file library should be preserved by default unless the user explicitly chooses to delete them.

---

## Testing and Feedback

LayerBase is looking for testers with different:

* Printer configurations
* OrcaSlicer versions
* G-code libraries
* Library sizes
* Raspberry Pi models
* Linux distributions
* Browsers
* Storage configurations
* Multi-printer workflows

Useful testing feedback includes:

* G-code files that do not parse correctly
* Settings that are missing or incorrectly labeled
* Searches that produce unexpected results
* Comparison fields that are unclear
* Performance issues with large libraries
* Installation failures
* Permission problems
* Browser-layout problems
* Database migration issues
* Suggestions that remain consistent with LayerBase’s role as a searchable file and print-settings database

When reporting a problem, please include:

* LayerBase version
* Host hardware
* Operating system and version
* Browser and version
* Slicer and version
* Number of files in the library
* Relevant log output
* Steps required to reproduce the problem
* Screenshots where helpful
* A sample G-code file when it can be shared safely

Before uploading G-code publicly, review it for filenames, paths, printer names, network details, or other information you may not wish to share.

---

## Roadmap

Potential future work includes:

* Expanded OrcaSlicer setting support
* Support for additional slicers
* Improved multi-file comparisons
* Database migration and recovery tools
* Automated backups
* Better duplicate detection
* Print-history tracking
* File archiving
* Optional printer-file synchronization
* Resending saved G-code to a printer
* Additional STL organization and preview tools
* Import and export tools
* Performance improvements for very large libraries
* Additional search and reporting options

Roadmap items are not guaranteed and may change based on testing, reliability, and project scope.

Any new feature should support LayerBase’s central purpose: making 3D-printing files, settings, and results easier to find, compare, and understand.

---

## Contributing

Contributions, bug reports, testing, and documentation improvements are welcome.

Before submitting a major feature, please open a discussion or issue describing:

* The problem being solved
* How the feature relates to LayerBase’s purpose
* Whether it changes the database
* Whether it affects existing installations
* How it would be tested
* Whether it duplicates functionality already provided by a slicer or printer dashboard

Code contributions should include appropriate documentation and testing whenever practical.

---

## License

LayerBase will be released under the **[LICENSE NAME]** license.

See the `LICENSE` file for the complete terms.

---

## Final Summary

LayerBase began as a way to compare calibration files and understand how slicer settings changed between print iterations.

It grew into something more useful: a searchable history of your files, settings, decisions, and print results.

## Interested in Testing?

LayerBase is approaching its first public testing release.

Potential testers are invited to follow or star this repository for future release announcements. Testing will initially focus on Raspberry Pi and Linux installations using G-code generated by OrcaSlicer.

Source code and installation instructions will be added when the first testing build is ready.

Instead of asking, “What did I change?” or “Why did this print look better six months ago?” LayerBase helps you find the answer.

**Every File. Every Print. Every Setting. One Searchable Database.**

