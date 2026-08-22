# NMR Sample Manager for TopSpin

[![Documentation](https://img.shields.io/badge/docs-online-blue)](https://nmrsamples.github.io/topspin/)
[![DOI](https://zenodo.org/badge/1073026274.svg)](https://doi.org/10.5281/zenodo.17427482)

A lightweight sample metadata management system for Bruker TopSpin (v3+), built using the internal Jython interface.

![Screenshot - Sample editing](assets/screenshot.png)
![Screenshot - Experimental timeline](assets/screenshot-timeline.png)
![Screenshot - Sample catalogue and search](assets/screenshot-catalogue.png)


## Overview

NMR workflows focus on data acquisition and processing, but sample tracking has been a longstanding blind spot. Bruker TopSpin manages *experiments* effectively, but provides no systematic way to record or retrieve information about *samples* -- e.g. protein concentrations, buffer compositions, isotopic labelling schemes, chemical shift referencing, NMR tube types. This often causes problems when looking back over old data or preparing data for repository submission.

This tool provides a GUI for recording sample metadata as JSON files within experiment directories.

### Part of the NMR Samples Ecosystem

This TopSpin integration is part of a broader metadata management system:
- **Schema definition**: [github.com/NMRSamples/schema](https://github.com/NMRSamples/schema)
- **Documentation & tools**: [nmrsamples.github.io](https://nmrsamples.github.io)

## Features

- **TopSpin Integration**: Runs natively within TopSpin with auto-navigation to current dataset
- **Form-based GUI**: Schema-driven metadata entry with validation
- **Timeline View**: Chronological visualization of samples and experiments
- **Sample Lifecycle**: Track creation, modification, and ejection timestamps
- **Schema Versioning**: Automatically handles schema updates

## Installation

1. Clone this repository (not within `/opt/topspin...`):
   ```bash
   git clone https://github.com/NMRSamples/topspin.git
   ```

2. In TopSpin, use `setres` to add the `src` directory to Python paths.

3. Commands are now available: `samples`, `ija`, `eja`

4. To update:
   ```bash
   cd /path/to/topspin
   git pull
   ```

## Usage

### Main Commands

- **`samples`** - Launch the main sample manager GUI
  - Opens GUI and navigates to current dataset
  - If already open, brings window to front and updates directory

- **`ija`** - Inject-and-Annotate (create new sample with auto-eject of previous)
  - Creates new sample entry with current timestamp
  - Automatically ejects any previously active sample

- **`eja`** - Eject-and-Annotate (mark current sample as ejected)
  - Adds ejection timestamp to active sample
  - Placeholder for physical ejection integration

### GUI Features

- **Directory Navigation**: Browse folders or jump to current dataset
- **Sample Management**: Create, edit, duplicate, eject, and delete samples
- **Status Badge**: ACTIVE (green), EMPTY (grey), or DRAFT (amber)
- **Timeline View**: Chronological display with experiment color-coding (1D/2D/3D)
- **Double-click**: Open experiments in TopSpin

## Data Model

Sample metadata is stored as JSON files following the [NMR Sample Schema](https://github.com/NMRSamples/schema), with filenames like `2025-10-09_143022_MyProtein.json`.
