# Data for asimov

This repository contains additional data for asimov, which is intended to help simplify the process of creating analyses, and recreating analyses on published gravitational wave events.

**Note** While we've made a best effort to ensure that the information contained in these files is accurate, and accurately reflects the settings used in the various analyses in published catalogues, they have not been thoroughly reviewed, and caution should be employed if using them to set up a new analysis.

## Using the data

The data provided in this repository are in the form of `asimov` blueprint files.
These allow settings to be directly applied to an `asimov` project, for example, to add GW150914 to your project you should run 
```
$ asimov apply -f /path/to/this/repository/events/gwtc-2-1/GW150914_095045.yaml
```
You can also apply the file directly from the internet, without cloning the repository, by using the "raw" version of the file on gitlab.
For GW150914 you should change the above command to
```
$ asimov apply -f https://git.ligo.org/asimov/data/-/raw/main/events/gwtc-2-1/GW150914_095045.yaml
```
to achieve this.

## Data available

All of the events from GWTC-3 are included in this repository, however these have been subdivided into events from GWTC-2.1, which includes all of the events from the O1, O2, and O3a observing runs, and GWTC-3, which adds the events from the O3b run.
All of the blueprint files for these events can be found in the `events` directory of the repository.
Each blueprint provides information about data channels, frame types, appropriate priors and analysis settings, and information about the event, including the time it occured.
Each event is named with its full gravitational wave GW name.

In addition to event blueprints we provide analysis settings in the `analyses` directory.
The `production-default.yaml` file contains the settings which were used for each event when preparing the GWTC-2.1 and GWTC-3 catalogues' parameter estimation analyses for Binary Black Hole events.
Applying this file to an event in an asimov project will add a `Bayeswave` job to produce an on-source PSD, an `Bilby` analysis using the IMRPhenomXPHM waveform, and a `RIFT` analysis using the `SEOBNRv4PHM` waveform.
Please note, that as these are intended to produce **production quality** analyses, they may take weeks to complete on a large high throughput computing facility.

To reduce the amount of settings which must be set on a per-event or event per-analysis basis this repository contains blueprints which set various defaults for both analyses and priors which are inteded to provide reasonable settings for most analyses, though each of these defaults can be overwritten by an event for all it's analyses, or any individual analysis.
These can be found in the `defaults` directory, with the `production-pe.yaml` blueprint containing the default pipeline settings used for the GWTC-2.1 and GWTC-3 analyses, and `production-priors.yaml` the default priors for BBH events.

## Information about this documentation

+ This documentation was written on 2023-02-01 by Daniel Williams in preparation for the release of `asimov v0.4`.
+ Please [raise an issue](https://git.ligo.org/asimov/data/-/issues) on this repository if you find any errors in the blueprints, or places where clarifications would be helpful.
