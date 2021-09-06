# Feature: Places

> Created by Rémi Bardon on 06/09/2021.  
> Copyright © 2021 Monki Projects. All rights reserved.

## Terminology

For a human-readable description, see [Terminology for users > Places](./terminology-for-users.md#places).
For a developer-oriented description,
see [Monki Projects Docs > Monki Map Models > Place](https://docs.monkiprojects.com/monki-projects-model-swift/monki-map-model/Place/).

## Feature description

Places are basically a place in the world. They can be anything from a big parkour training spot
to a water fountain to a bench to a parkour park.

> **Note:** See [Terminology for users > Places](./terminology-for-users.md#places) for an explanation
> of the related vocabulary.

Places are categorized by their kind (training spot, calisthenics park…)
and their category (spot, facility…). For more information on places' categorization,
see ["You can easily help us categorize parkour spots, wanna help?" on our blog](https://monkiprojects.com/blog/help-us-categorize-parkour-spots/).

## Technical specs

### Places have IDs starting with `place_`

> By Rémi Bardon on 06/09/2021

We use `UUID`s everywhere, so to distinguish them, we decided to prefix the random values
by a fixed word.
For places it's `place_`, like in `place_03aa0171-0d76-4144-bf5b-bf56654deb5d`.

> **Note:** To make it as performant as regular (Swift) `UUID`s,
> we developed [`Prefixed`](https://github.com/RemiBardon/swift-prefixed-type).

### `Place` is an `enum` type

> By Rémi Bardon on 06/09/2021

`Place` is an `enum` type, and has nested types acting as
[Data Transfer Objects (DTOs)](https://en.wikipedia.org/wiki/Data_transfer_object).
You can [see the docs](https://docs.monkiprojects.com/monki-projects-model-swift/monki-map-model/Place/)
for all details, but for example we have a `Place.Public` DTO used to transfer data
from the web API to the app.

Having this separation between "the idea of place" and "the data structure of `Place`" is necessary,
as we will have other DTOs in the future.
For example, `Place.Public` will be renamed to `Place.Public.Full`,
to explicit the fact that it's a heavy data structure,
and we will create the `Place.Public.Minimal` data structure containing only the minimal data
for representation on a map (where thousands of places can be loaded).

The `.Public` prefix is a general style <!-- TODO: Insert link to doc page here -->
communicating the fact that this DTO can safely be shared.
Sometimes, we might have DTOs prefixed by `.Internal`, and this means they should not be shared.
The `.Private` prefix explicits that this DTO should only be shared to very specific users
(for example if this DTO contains an email address).
Finally, DTOs prefixed by `.Create` or `.Update` are used for "Create" and "Update" operations
when interacting with a [CRUD storage](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete).

### Places are not sent as GeoJSON by default

> By Rémi Bardon on 06/09/2021

For now, our APIs send domain models, but we've considered [GeoJSON].
To make encoding/decoding easier, we decided not to use [GeoJSON] internally.

However, we'd like to support it one day, along with other
[Geospatial formats](https://gisgeography.com/gis-formats/).
It could be
with a [query parameter](https://en.wikipedia.org/wiki/Query_string) (e.g. `format=geojson`),
with a path extension (e.g. `/places/463f577f-ae07-44c8-a4f0-db1901bda5c5.geojson`)
or with a [path component](https://datatracker.ietf.org/doc/html/rfc2396#section-3.3)
(e.g. `/places/463f577f-ae07-44c8-a4f0-db1901bda5c5/geojson`).
We did not decide yet, since it's not the moment to do so.

## Ideas

### Places as maps

> By Rémi Bardon on 06/09/2021

Places could be seen as maps, because it can contain other [elements](./terminology-for-users.md#place-elements).
Displaying a place could then show a scoped map with markers for each element creating it,
as maps show places it contains.

In [GeoJSON], that would mean a place is
a [`FeatureCollection` object](https://datatracker.ietf.org/doc/html/rfc7946#section-3.3),
not just a [`Feature` object](https://datatracker.ietf.org/doc/html/rfc7946#section-3.2).

## Trials and tests

<!-- TODO -->

[GeoJSON]: https://geojson.org
