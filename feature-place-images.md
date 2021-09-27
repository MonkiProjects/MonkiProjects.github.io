# Feature: Place images

> Created by Rémi Bardon on 27/09/2021.  
> Copyright © 2021 Monki Projects. All rights reserved.

## Introduction

This feature refers to [Places](./feature-places.md), you should probably read it first.

## Feature description

Place images should have:

* An import date
* An original date
* A description (called `alt` in Swift code to avoid conflict with the reserved keyword)
  * Users should be able to describe what’s on the picture. This would:
    * Allow accessibility tools to explain the picture.
    * Improve Monki Map app’s and website’s scores in search engines.
    * Allow the system to process or tag images more easily in the future.
  * If users dont’t describe a picture, we should manually do it until it gets out of control.
