# Feature: Places

> Created by Rémi Bardon on 06/09/2021.  
> Copyright © 2021 Monki Projects. All rights reserved.

## Terminology

For a human-readable description, see [Terminology for users > Places](./terminology-for-users.md#places). For a developer-oriented description, see [Monki Projects Docs > Monki Map Models > Place](https://docs.monkiprojects.com/monki-projects-model-swift/monki-map-model/Place/).

## Feature description

<!-- TODO -->

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

## Ideas

### Places as maps

> By Rémi Bardon on 06/09/2021

Places could be seen as maps, because it can contain other [elements](./terminology-for-users.md#place-elements).
Displaying a place could then show a scoped map with markers for each element creating it,
as maps show places it contains.

In [GeoJSON](https://geojson.org), that would mean a place is
a [`FeatureCollection` object](https://datatracker.ietf.org/doc/html/rfc7946#section-3.3),
not just a [`Feature` object](https://datatracker.ietf.org/doc/html/rfc7946#section-3.2).

## Trials and tests

<!-- TODO -->
