<!-- The SAAM API -->
# American Art API

The American Art API exposes art & artists from the [Smithsonian American Art Museum's](https://americanart.si.edu) collection. The API is follows [{JSON:API}](http://jsonapi.org/) specs.  
> All requests to the American Art API are prefixed with `/saam/v1/`

## Accept header
> Make sure you send the accept header: `Accept: application/vnd.api+json`.

## Resources

The following resources are available:

| Resource | Endpoint | Description |
| :------- | :------- | :---------- |
| [Artworks](#artworks) | /saam/v1/artworks | Works of art in the SAAM collection |
| [Artists](#artists) | /saam/v1/artists | Artists related to one or more work of art |
| [Institutions](#institutions) | /saam/v1/institutions | An organization related to one or more work of art |
| [Exhibitions](#exhibitions) | /saam/v1/exhibitions  | Museum exhibitions |
| [Audio](#audio) | /saam/v1/media/audio  | Audio content related to collection objects |
| [Books](#books) | /saam/v1/books  | Books about art |

## Common Fields
The following fields are common to all resources in the American Art API.

| Field | Description | type |
| :--------- | :----- | :--- |
| id | The resource uuid | string |
| changed | The date the content was last updated Date Format: `Y-m-d\TH:i:sO` | string |
| type | The resource name. | string |
| attributes | Additonal resource fields | object |

### Artworks
`GET /saam/v1/artworks/` will get a list of artworks.

?> Note: Related Resources, media, and categories are linked to through [relationships](#relationships)

#### Fields

| Field | Description | Type |
| :--------- | :----- | :--- |
| attributes.uuid | The resource uuid | string |
| attributes.title | The resource title | string |
| attributes.path | Information about the URL on americanart.si.edu | object |
| attributes.description | The artwork description | string |
| attributes.copyright | The artwork description | string |
| attributes.credit_line | The artwork description | string |
| attributes.dated | The artwork description | string |
| attributes.dimensions | The artwork description | string |
| attributes.display_mediums | The artwork description | string |
| attributes.exhibition_label | The artwork description | string |
| attributes.gallery_label | The artwork description | string |
| attributes.hex_color_codes | The artwork description | array |
| attributes.long_title | Complete title if artwork title is longer than the allowed `attributes.title` field | string |
| attributes.luce_center_label | The Luce Center Label | string |
| attributes.luce_object_quote | The Luce Object quote | string |
| attributes.new_acquisition_label | The Acquisition Label | string |
| attributes.is_new_acquistion | Is the artwork a new acquistion | boolean |
| attributes.object_number | The artwork object number | string |
| attributes.ontology | Cross reference terms | array |
| attributes.is_on_view | Is the artwork on view at the museum | boolean |
| attributes.publication_label | The Publication Label | string |

#### Example

`GET /saam/v1/artworks/{{uuid}}` will get detailed info about a specific artist.

> ```
> https://api.si.edu/saam/v1/artworks/dd19ac03-04e8-4d20-bfe9-ecfc238ebd54  
> ```
> Returns the full record for "Electronic Superhighway".

#### Response

```json
{
    "data": {
        "todo": "insert abbreviated response for electronic superhigway"
    }
}
```

### Artists
Contains information on entities that have some association to works of art in the collection or publications. Associations include artists, sitters, printers, donors, authors, publishers, and more.

`GET /saam/v1/artists` will get a list of artists.

#### Fields

| Field | Description | Type |
| :--------- | :----- | :--- |
| attributes.uuid | The resource uuid | string |
| attributes.title | The resource title | string |
| attributes.path | Information about the URL on americanart.si.edu | object |
| attributes.aka_names | Other names the artist is known as | string |
| attributes.alphabetical_name | The artist alphabetical name | string |
| attributes.artist_biography | Biographical text | object |
| attributes.associated_places | Places associated with the artist | array |
| attributes.birth_place | Place the artist was born | string |
| attributes.birth_year | Year the artist was born | string |
| attributes.date_of_birth | Date the artist was born | string |
| attributes.date_of_death | Date the artist died | string |
| attributes.death_place | Place of death | string |
| attributes.death_year | Year the artist died | string |
| attributes.display_date | A public date "label" for the artist | string |
| attributes.firstname | The artist's first name | string |
| attributes.lastname | The artist's last name | string |
| attributes.last_known_place | Last known place of the artist | string |
| attributes.luce_artist_biography | Biographical text from Luce Center | object |
| attributes.name_prefix | The artist's name prefix | string |
| attributes.name_suffix | The artist's name suffix | string |
| attributes.name_title | The artist's name title (i.e. Sir, Mrs., etc.) | string |


#### Example

`GET /saam/v1/artists/{{uuid}}` will get detailed info about a specific artist.


> ```
> https://api.si.edu/saam/v1/artists/4039d113-5302-426d-9c9d-e4bf3db87f7e  
> ```
> Returns the full record for "Nam June Paik".

#### Response

```json
{
    "data": {
        "todo": "insert abbreviated response for artist Nam June Paik"
    }
}
```
### Institutions
`GET /saam/v1/institutions` will get a list of organizations associated with an Artwork.

#### Fields

| Field | Description | Type |
| :--------- | :----- | :--- |
| attributes.uuid | The resource uuid | string |
| attributes.title | The resource title | string |
| attributes.path | Information about the URL on americanart.si.edu | object |
| attributes.alphabetical_name | The institution's alphabetical name | string |
| attributes.display_date | A public date "label" for the institution | string |

#### Example

`GET /saam/v1/institutions/{{uuid}}` will get detailed info about a specific institution.


> ``` 
> https://api.si.edu/saam/v1/institutions/1f2ef80a-897c-46f6-8824-991e6d320e48  
> ```
> Returns the full record for the "U.S. Mint".

#### Response

```json
{
    "data": {
        "todo": "insert abbreviated response for US MINt"
    }
}
```

### Exhibitions
`GET /saam/v1/exhibitions` will get a list of museum exhibitions.

#### Fields

| Field | Description | Type |
| :--------- | :----- | :--- |
| attributes.uuid | The resource uuid | string |
| attributes.title | The resource title | string |
| attributes.path | Information about the URL on americanart.si.edu | object |
| attributes.description | The exhibition description | object |
| attributes.accession_number | The exhibition accession number | string |
| attributes.archive_date | The date archived | string |
| attributes.close_date | The date closed | string |
| attributes.gallery | The location the event was held | string |
| attributes.museum | The museum the event was held | string |
| attributes.open_date | The exhibition accession number | string |
| attributes.permanent_exhibition | The exhibition accession number | boolean |
| attributes.traveling | Is this a traveling exhibition | boolean |
| attributes.travel_begin_date | Date the exhibiton began as a traveling exhibition | string |
| attributes.travel_end_date | Date the exhibiton ended as a traveling exhibition | string |

#### Example

`GET /saam/v1/exhibitions/{{uuid}}` will get detailed info about a specific exhibition.


> ```
> https://api.si.edu/saam/v1/exhibitions/dc4bf972-f39e-44c8-ba14-f44c9fab54c8
> ```
> Returns the full record for "Nam June Paik: Global Visionary".

#### Response

```json
{
    "data": {
        "todo": "insert abbreviated response for paik exhibit"
    }
}
```

### Audio
`GET /saam/v1/audio` will get a list of audio media related to collection objects.

?> Note: Related media are linked to through [relationships](#relationships)

#### Fields

| Field | Description | Type |
| :--------- | :----- | :--- |
| attributes.uuid | The resource uuid | string |
| attributes.title | The resource title | string |
| attributes.path | Information about the URL on americanart.si.edu | object |
| attributes.description | The audio description | object |
| attributes.field_transcription | The audio plaintext transcript | string |

#### Example

`GET /saam/v1/audio/{{uuid}}` will get detailed info about a specific audio entity.


> ```
> https://api.si.edu/saam/v1/audio/8abede9a-b374-4255-9d05-723103cdede1
> ```
> Returns the full record for "Autonomy Cube".

#### Response

```json
{
    "data": {
        "todo": "insert abbreviated response for audio entity"
    }
}
```

### Books
`GET /saam/v1/books` will get a list of SAAM books.

#### Fields

| Field | Description | Type |
| :--------- | :----- | :--- |
| attributes.uuid | The resource uuid | string |
| attributes.title | The resource title | string |
| attributes.path | Information about the URL on americanart.si.edu | object |
| attributes.description | The book description | object |
| attributes.author | The book author | string |
| attributes.author_for_display | An complete byline for output | string |
| attributes.book_title_display | An complete title for output | string |
| attributes.dimensions | Physical dimensions of the book | string |
| attributes.isbn_hardcover | ISBN for hardcover | string |
| attributes.isbn_softcover | ISBN for softcover | string |
| attributes.pages | Number of pages (i.e. "248 pp.") | string |
| attributes.publisher | The publisher name | string |
| attributes.year_published | The year published | integer |

#### Example

`GET /saam/v1/book/{{uuid}}` will get detailed info about a specific book.


> ```
> https://api.si.edu/saam/v1/books/2ad06661-5b8e-41ae-af2b-ddf7f7e5711e
> ```
> Returns the full record for "The Art of Video Games".

#### Response

```json
{
    "data": {
        "todo": "insert abbreviated response for the book"
    }
}
```

## Sorting 

Sorting results can be done on most fields using a `?sort` parameter with fields as the target. 

?> Read the full [{JSON:API} specification on sorting](http://jsonapi.org/format/#fetching-sorting).                                            

#### Examples

> ```
> https://api.si.edu/saam/v1/artworks?sort=-changed
> ```
> Sorting on the `changed` field returns the most recently updated artworks Note that the preceding "minus" sign (-) specifies descending order.

> ```
> https://api.si.edu/saam/v1/books?sort=sort=-year_published,author
> ```
> Sorting on multiple fields.

## Filtering
Filters are one of the most useful things about the JSON API spec. You can create relatively complex queries using filter parameters.

?> Read the full [{JSON:API} specification on filtering](http://jsonapi.org/format/#fetching-filtering).                                            

#### Examples

> ```
> https://api.si.edu/saam/v1/artworks?filter[object-number][path]=object_number&filter[object-number][value]=2002.23
> ```
> Get the artwork where the Object Number is "2002.23".


> ```
> https://api.si.edu/saam/v1/artworksartworks?filter[title][path]=title&filter[title][value]=robot&filter[title][operator]=CONTAINS
> ```
> Get artworks where the title contains the word "robot".


> ```
> https://api.si.edu/saam/v1/artwork?filter[fitler-group][group][conjunction]=AND&filter[classifications-filter][condition][path]=classifications.title&filter[classifications-filter][condition][value]=Painting&filter[classifications-filter][condition][memberOf]=fitler-group&filter[on-view-filter][condition][path]=is_on_view&filter[on-view-filter][condition][value]=1&filter[on-view-filter][condition][memberOf]=fitler-group
> ```
> Get artworks where the Classification category is "Painting" and the object is currently on view in the museum.


## Paging
Requests that return large numbers of records will be spread across multiple pages. By default, a request returns 20 records per page. Use the `page[limit]` and `page[offset]` parameters to implement paging.

#### Example

> ```shell
> https://api.si.edu/saam/v1/artworks?page[limit]=20&page[offset]=1&sort=-changed
> ```
> Get the second page of all artworks sorted by updated date. 

## Relationships
Resources are returned with a `relationships` property which contains links to related media (image and audio files), categories, or other related resources. These related items can be retrieved in a separate API request using the `link`, or can be included in a single request by specifying which relationships to include in the results using the `?include` parameter.

?> Read the full [{JSON:API} specification on relationships](http://jsonapi.org/format/#fetching-relationships).                                            

#### Examples

> ```
> https://api.si.edu/saam/v1/audio/8abede9a-b374-4255-9d05-723103cdede1?include=file
> ```
> Get a specific audio resource, and include the audio file data.


> ```
> http://saam.test/api/v1/collection/artworks/dd19ac03-04e8-4d20-bfe9-ecfc238ebd54?include=artwork_images,artwork_images.artwork_image,artists,classifications,highlights,locations
> ```
> Get a specific artwork, and include data for related images and categories.


## Contact

[Contact](https://americanart.si.edu/about/contact) for issues or feedback related to the American Art API

