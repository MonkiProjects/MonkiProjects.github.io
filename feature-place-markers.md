# Feature: Place markers

> Created by Rémi Bardon on 06/09/2021.  
> Copyright © 2021 Monki Projects. All rights reserved.

## Introduction

This feature refers to [Places](./feature-places.md),
you should probably read it first.

## Feature description

Places can be shown on maps. To make those maps easier to understand,
we decided to think about ways to differenciate them at a glance.

We decided to create [place kinds](./terminology-for-users.md#place-kinds) and [place categories](./terminology-for-users.md#place-categories).

For now, markers have a color defined by the place category,
and a glyph defined by the place kind.

## Ideas

### Coloring styles for places on the map

> By Rémi Bardon on 06/09/2021

Something that could be useful would be to allow a user to select different coloring styles
to match their needs.
For example, we could have a style which shows badly rated places as red, going to green
for great places.
We could have different styles based on the rated value (diversity, quietness, dangerousness, cleanliness…).
We could also have a style that reflects the fact that a place is locally downloaded or not,
if it's shared or not, or if it's one of the user's personal places or not.

This would require a special coloring code architecture, which we will try to implement as soon as possible.

### Custom coloring styles for places on the map

> By Rémi Bardon on 06/09/2021

After [predefined coloring styles for places on the map](#coloring-styles-for-places-on-the-map),
we could add a way for users to create a custom coloring style.

This coloring style could be based on user-defined rules.
The user could set a color for each map, but this would require special handling
of places in multiple maps. For a good example, see [Mapstr](https://mapstr.com).
