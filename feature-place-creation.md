# Feature: Place creation

> Created by Rémi Bardon on 27/09/2021.  
> Copyright © 2021 Monki Projects. All rights reserved.

## Introduction

This feature refers to [Places](./feature-places.md), you should probably read it first.

## Feature description

To create a place, the user can:

### Hit (+)

Choices:

* “On my location”
  * If location is available, use it
  * Otherwise, ask for one-time location
  * If denied, set no location
* “In the middle of the map”
* “Choose a location”
  * This opens the location choosing sheet
* “Take a picture”
  * If location is available, use it
  * Otherwise, try to use the picture’s location
    * If used, notify the user
  * If no location can be found in the picture’s EXIF data, ask for one-time location
  * If denied, set no location
* “Import pictures”
  * Import multiple pictures from gallery
  * Get locations from pictures
  * Compute and use the locations’ centroid
    * If used, notify the user
  * If no locations available, set no location

This creates a place with:

* Optional coordinate
* A default name that is the creation date/time
* No caption
* A creation date
* Possibly some pictures
* No kind of category

### Long press (+)

* Allows to choose a location and enter a caption.
* Does not open the editing sheet.
* Sets the place as draft.
* Doesn’t set a place kind (or category).

Haptic feedback:

* Light on long press
* Success on release (location chosen)
* Error or light on cancel (to try)
