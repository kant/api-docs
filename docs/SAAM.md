<!-- The SAAM API -->
# American Art API

!> WARNING! The American Art API has been depreciated. The endpoints will no longer be accessible at the end of March 2020.

The American Art API exposes art & artists from the [Smithsonian American Art Museum's](https://americanart.si.edu) collection. The API is follows [{JSON:API}](http://jsonapi.org/) specs.  
> All requests to the American Art API are prefixed with `/saam/v1/`

## Headers
> Each api request should include the following headers: 
> ```
>  X-Api-Key: {{YOUR_API_KEY}}
>  Accept: application/vnd.api+json
> ```

## Resources

The following resources are available:

| Resource | Endpoint | Description |
| :------- | :------- | :---------- |
| [Artworks](#artworks) | /saam/v1/node/artwork | Works of art in the SAAM collection |
| [Artists](#artists) | /saam/v1/node/person | Artists related to one or more work of art |
| [Institutions](#institutions) | /saam/v1/node/institution | An organization related to one or more work of art |
| [Exhibitions](#exhibitions) | /saam/v1/node/exhibition  | Museum exhibitions |
| [Books](#books) | /saam/v1/node/publication  | Books about art |

## Common Fields
The following fields are common to all resources in the American Art API.

| Field | Description | type |
| :--------- | :----- | :--- |
| id | The resource uuid | string |
| type | The resource name. | string |
| attributes | Additonal resource fields | object |

### Artworks
`GET /saam/v1/node/artwork` will get a list of artworks.

?> Note: Related Resources, media, and categories are linked to through [relationships](#relationships)

#### Fields

| Field | Description | Type |
| :--------- | :----- | :--- |
| attributes.uuid | The resource uuid | string |
| attributes.title | The resource title | string |
| attributes.path | Information about the URL on americanart.si.edu | object |
| attributes.object_number | The artwork object number | string |
| attributes.is_on_view | Is the artwork on view at the museum | boolean |

#### Example

`GET /saam/v1/node/artwork/{{uuid}}` will get detailed info about a specific artist.

> ```
> https://api.si.edu/saam/v1/node/artwork/dd19ac03-04e8-4d20-bfe9-ecfc238ebd54  
> ```
> Returns the full record for "Electronic Superhighway".

### Artists
Contains information on entities that have some association to works of art in the collection or publications. Associations include artists, sitters, printers, donors, authors, publishers, and more.

`GET /saam/v1/node/person` will get a list of artists.

#### Fields

| Field | Description | Type |
| :--------- | :----- | :--- |
| attributes.uuid | The resource uuid | string |
| attributes.title | The resource title | string |
| attributes.path | Information about the URL on americanart.si.edu | object |
| attributes.field_aka_names | Other names the artist is known as | string |
| attributes.field_alphabetical_name | The artist alphabetical name | string |
| attributes.field_artist_biography | Biographical text | object |

#### Example

`GET /saam/v1/node/person/{{uuid}}` will get detailed info about a specific artist.


> ```
> https://api.si.edu/saam/v1/node/person/4039d113-5302-426d-9c9d-e4bf3db87f7e  
> ```
> Returns the full record for "Nam June Paik".

### Institutions
`GET /saam/v1/node/institution` will get a list of organizations associated with an Artwork.

#### Fields

| Field | Description | Type |
| :--------- | :----- | :--- |
| attributes.uuid | The resource uuid | string |
| attributes.title | The resource title | string |
| attributes.path | Information about the URL on americanart.si.edu | object |
| attributes.field_alphabetical_name | The institution's alphabetical name | string |
| attributes.field_display_date | A public date "label" for the institution | string |

#### Example

`GET /saam/v1/node/institution/{{uuid}}` will get detailed info about a specific institution.


> ``` 
> https://api.si.edu/saam/v1/node/institution/1f2ef80a-897c-46f6-8824-991e6d320e48  
> ```
> Returns the full record for the "U.S. Mint".

### Exhibitions
`GET /saam/v1/node/exhibition` will get a list of museum exhibitions.

#### Fields

| Field | Description | Type |
| :--------- | :----- | :--- |
| attributes.uuid | The resource uuid | string |
| attributes.title | The resource title | string |
| attributes.path | Information about the URL on americanart.si.edu | object |
| attributes.field_location | The museum the event was held | string |
| attributes.field_open_date | The exhibition accession number | string |

#### Example

`GET /saam/v1/node/exhibition/{{uuid}}` will get detailed info about a specific exhibition.


> ```
> https://api.si.edu/saam/v1/node/exhibition/dc4bf972-f39e-44c8-ba14-f44c9fab54c8
> ```
> Returns the full record for "Nam June Paik: Global Visionary".

### Books
`GET /saam/v1/node/publication` will get a list of SAAM books.

#### Fields

| Field | Description | Type |
| :--------- | :----- | :--- |
| attributes.uuid | The resource uuid | string |
| attributes.title | The resource title | string |
| attributes.path | Information about the URL on americanart.si.edu | object |
| attributes.field_blurb_text | The book description | object |
| attributes.field_author | The book author | string |
| attributes.field_isbn_hardcover | ISBN for hardcover | string |
| attributes.field_isbn_softcover | ISBN for softcover | string |
| attributes.field_year_published | The year published | integer |

#### Example

`GET /saam/v1/book/{{uuid}}` will get detailed info about a specific book.


> ```
> https://api.si.edu/saam/v1/node/publication/2ad06661-5b8e-41ae-af2b-ddf7f7e5711e
> ```
> Returns the full record for "The Art of Video Games".

## Sorting 

Sorting results can be done on most fields using a `?sort` parameter with fields as the target. 

?> Read the full [{JSON:API} specification on sorting](http://jsonapi.org/format/#fetching-sorting).                                            

#### Examples

> ```
> https://api.si.edu/saam/v1/node/artwork?sort=-changed
> ```
> Sorting on the `changed` field returns the most recently updated artworks Note that the preceding "minus" sign (-) specifies descending order.

> ```
> https://api.si.edu/saam/v1/node/publication?sort=-field_year_published,field_author
> ```
> Sorting on multiple fields.

## Filtering
Filters are one of the most useful things about the JSON API spec. You can create relatively complex queries using filter parameters.

?> Read the full [{JSON:API} specification on filtering](http://jsonapi.org/format/#fetching-filtering).                                            

#### Examples

> ```
> https://api.si.edu/saam/v1/node/artwork?filter[field-object-number][path]=field_object_number&filter[field-object-number][value]=2002.23
> ```
> Get the artwork where the Object Number is "2002.23".


> ```
> https://api.si.edu/saam/v1/node/artworkartworks?filter[title][path]=title&filter[title][value]=robot&filter[title][operator]=CONTAINS
> ```
> Get artworks where the title contains the word "robot".


> ```
> https://api.si.edu/saam/v1/node/artwork?filter[fitler-group][group][conjunction]=AND&filter[classifications-filter][condition][path]=field_classifications.name&filter[classifications-filter][condition][value]=Painting&filter[classifications-filter][condition][memberOf]=fitler-group&filter[on-view-filter][condition][path]=field_on_view&filter[on-view-filter][condition][value]=1&filter[on-view-filter][condition][memberOf]=fitler-group
> > ```
> Get artworks where the Classification category is "Painting" and the object is currently on view in the museum.


## Paging
Requests that return large numbers of records will be spread across multiple pages. By default, a request returns 20 records per page. Use the `page[limit]` and `page[offset]` parameters to implement paging.

#### Example

> ```shell
> https://api.si.edu/saam/v1/node/artwork?page[limit]=20&page[offset]=1&sort=-changed
> ```
> Get the second page of all artworks sorted by updated date. 

## Relationships
Resources are returned with a `relationships` property which contains links to related media (image and audio files), categories, or other related resources. These related items can be retrieved in a separate API request using the `link`, or can be included in a single request by specifying which relationships to include in the results using the `?include` parameter.

?> Read the full [{JSON:API} specification on relationships](http://jsonapi.org/format/#fetching-relationships).                                            

#### Example

> ```
> https://api.si.edu/saam/v1/node/artwork/dd19ac03-04e8-4d20-bfe9-ecfc238ebd54?include=field_artwork_images,field_artwork_images.field_artwork_image,field_persons,field_classifications,field_highlights,field_on_view_locations
> ```
> Get a specific artwork, and include data for the artwork images and categories.


## Feedback

[Contact](https://github.com/Smithsonian/api-docs/issues) for issues or feedback related to the American Art API

