<!-- The SAAM API -->
# American Art API

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
| [Artworks](#artworks) | /saam/v1/artworks | Works of art in the SAAM collection |
| [Artists](#artists) | /saam/v1/artists | Artists related to one or more work of art |
| [Institutions](#institutions) | /saam/v1/institutions | An organization related to one or more work of art |
| [Exhibitions](#exhibitions) | /saam/v1/exhibitions  | Museum exhibitions |
| [Audio](#audio) | /saam/v1/audio  | Audio content related to collection objects |
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
	data: {
		type: "artworks",
		id: "dd19ac03-04e8-4d20-bfe9-ecfc238ebd54",
		attributes: {
			uuid: "dd19ac03-04e8-4d20-bfe9-ecfc238ebd54",
			title: "Electronic Superhighway: Continental U.S., Alaska, Hawaii",
			changed: "2018-06-06T10:43:02-0400",
			path: {
				alias: "/artwork/electronic-superhighway-continental-us-alaska-hawaii-71478",
				pid: 1641318,
				langcode: "en"
			},
			copyright: "© Nam June Paik Estate",
			credit_line: "Gift of the artist",
			dated: "1995",
			dimensions: "approx. 15 x 40 x 4 ft.",
			display_mediums: "fifty-one channel video installation (including one closed-circuit television feed), custom electronics, neon lighting, steel and wood; color, sound",
			exhibition_label: null,
			gallery_label: {
				value: "<p>When Nam June Paik came to the United States in 1964, the interstate highway system was only nine years old, and superhighways offered everyone the freedom to "
				see the U.S.A.in your Chevrolet.
				" Walking along the entire length of this installation suggests the enormous scale of the nation that confronted the young Korean artist when he arrived. Neon outlines the monitors, recalling the multicolored maps and glowing enticements of motels and restaurants that beckoned Americans to the open road. The different colors remind us that individual states still have distinct identities and cultures, even in today's information age.</p> <p>Paik augmented the flashing images "
				seen as though from a passing car " with audio clips from <i>The Wizard of Oz</i>, <i>Oklahoma</i>, and other screen gems, suggesting that our picture of America has always been influenced by film and television. Today, the Internet and twenty-four-hour broadcasting tend to homogenize the customs and accents of what was once a more diverse nation. Paik was the first to use the phrase "
				electronic superhighway,
				" and this installation proposes that electronic media provide us with what we used to leave home to discover. But <i>Electronic Superhighway</i> is real. It is an enormous physical object that occupies a middle ground between the virtual reality of the media and the sprawling country beyond our doors.</p> <p>Exhibition Label, Smithsonian American Art Museum, 2006</p> ",
				format: "full_html",
				processed: "<p>When Nam June Paik came to the United States in 1964, the interstate highway system was only nine years old, and superhighways offered everyone the freedom to "
				see the U.S.A.in your Chevrolet.
				" Walking along the entire length of this installation suggests the enormous scale of the nation that confronted the young Korean artist when he arrived. Neon outlines the monitors, recalling the multicolored maps and glowing enticements of motels and restaurants that beckoned Americans to the open road. The different colors remind us that individual states still have distinct identities and cultures, even in today's information age.</p> <p>Paik augmented the flashing images "
				seen as though from a passing car " with audio clips from <i>The Wizard of Oz</i>, <i>Oklahoma</i>, and other screen gems, suggesting that our picture of America has always been influenced by film and television. Today, the Internet and twenty-four-hour broadcasting tend to homogenize the customs and accents of what was once a more diverse nation. Paik was the first to use the phrase "
				electronic superhighway,
				" and this installation proposes that electronic media provide us with what we used to leave home to discover. But <i>Electronic Superhighway</i> is real. It is an enormous physical object that occupies a middle ground between the virtual reality of the media and the sprawling country beyond our doors.</p> <p>Exhibition Label, Smithsonian American Art Museum, 2006</p> "
			},
			hex_color_codes: [
				"#1D2298",
				"#531E2E",
				"#4467CD",
				"#318025",
				"#AD3942"
			],
			long_title: null,
			luce_center_label: null,
			luce_object_quote: null,
			new_acquisition_label: null,
			is_new_acquistion: false,
			object_number: "2002.23",
			ontology: [
				"Authorities\Attributes\Objects\Subject Specific\Object\written matter\map",
				"Authorities\Attributes\Objects\Subject Specific\Object\furniture\television",
				"Authorities\Attributes\Objects\Subject Specific\Landscape\United States"
			],
			is_on_view: true,
			publication_label: null
		},
		relationships: {
			artwork_images: {
				data: [{
					type: "artwork_images",
					id: "876139cb-4069-4874-a9e0-ab2d9866daef"
				}],
				links: {
					self: "https://api.si.edu/saam/v1/artworks/dd19ac03-04e8-4d20-bfe9-ecfc238ebd54/relationships/artwork_images"
				}
			},
			centuries: {
				data: {
					type: "centuries",
					id: "12b920f4-9054-40b9-8c60-8943cd3a52a0"
				},
				links: {
					self: "https://api.si.edu/saam/v1/artworks/dd19ac03-04e8-4d20-bfe9-ecfc238ebd54/relationships/centuries"
				}
			},
			classifications: {
				data: [{
						type: "classifications",
						id: "f37a2aba-2922-40f5-a90f-a17a5349c6eb"
					},
					{
						type: "classifications",
						id: "6f67133b-50b5-4e4f-a4af-252c4fca9750"
					}
				],
				links: {
					self: "https://api.si.edu/saam/v1/artworks/dd19ac03-04e8-4d20-bfe9-ecfc238ebd54/relationships/classifications"
				}
			},
			highlights: {
				data: [{
						type: "highlights",
						id: "1abfa744-e45b-405f-8310-4cc1984133d7"
					},
					{
						type: "highlights",
						id: "38a632ce-6772-431d-b239-014e8dfeb70a"
					},
					{
						type: "highlights",
						id: "dc6501bd-6216-4509-a67c-e079a39a5c54"
					},
					{
						type: "highlights",
						id: "5f2c09fb-204f-48c5-9d7b-61f014e6bab5"
					}
				],
				links: {
					self: "https://api.si.edu/saam/v1/artworks/dd19ac03-04e8-4d20-bfe9-ecfc238ebd54/relationships/highlights"
				}
			},
			locations: {
				data: [{
						type: "locations",
						id: "5399f8da-066e-4bdf-8bfb-fc22c2ee9c12"
					},
					{
						type: "locations",
						id: "211257e1-027d-49d5-b149-744d59d3ae4e"
					},
					{
						type: "locations",
						id: "a97da2ab-fa83-445f-bb4a-4cd9c7629ef9"
					}
				],
				links: {
					self: "https://api.si.edu/saam/v1/artworks/dd19ac03-04e8-4d20-bfe9-ecfc238ebd54/relationships/locations"
				}
			},
			artists: {
				data: [{
					type: "artists",
					id: "4039d113-5302-426d-9c9d-e4bf3db87f7e"
				}],
				links: {
					self: "https://api.si.edu/saam/v1/artworks/dd19ac03-04e8-4d20-bfe9-ecfc238ebd54/relationships/artists"
				}
			},
			rights_types: {
				data: {
					type: "rights_types",
					id: "b74965ce-6059-4b9a-bd95-4d8104620df8"
				},
				links: {
					self: "https://api.si.edu/saam/v1/artworks/dd19ac03-04e8-4d20-bfe9-ecfc238ebd54/relationships/rights_types"
				}
			}
		},
		links: {
			self: "https://api.si.edu/saam/v1/artworks/dd19ac03-04e8-4d20-bfe9-ecfc238ebd54"
		}
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
	data: {
		type: "artists",
		id: "4039d113-5302-426d-9c9d-e4bf3db87f7e",
		attributes: {
			uuid: "4039d113-5302-426d-9c9d-e4bf3db87f7e",
			title: "Nam June Paik",
			changed: "2018-03-13T16:50:01-0400",
			path: {
				alias: "/artist/nam-june-paik-3670",
				pid: 1651879,
				langcode: "en"
			},
			aka_names: null,
			alphabetical_name: "Paik, Nam June",
			artist_biography: {
				value: "<p class="
				noindent ">Nam June Paik (1932&ndash;2006), internationally recognized as the "
				Father of Video Art,
				" created a large body of work including video sculptures, installations, performances, videotapes and television productions. He had a global presence and influence, and his innovative art and visionary ideas continue to inspire a new generation of artists.</p> <p>Born in 1932 in Seoul, Korea, to a wealthy industrial family, Paik and his family fled Korea in 1950 at the outset of the Korean War, first to Hong Kong, then to Japan. Paik graduated from the University of Tokyo in 1956, and then traveled to Germany to pursue his interest in avant-garde music, composition and performance. There he met John Cage and George Maciunas and became a member of the neo-dada Fluxus movement. In 1963, Paik had his legendary one-artist exhibition at the Galerie Parnass in Wuppertal, Germany, that featured his prepared television sets, which radically altered the look and content of television.</p> <p>After immigrating to the United States in 1964, he settled in New York City where he expanded his engagement with video and television, and had exhibitions of his work at the New School, Galerie Bonino and the Howard Wise Gallery. In 1965, Paik was one of the first artists to use a portable video camcorder. In 1969, he worked with the Japanese engineer Shuya Abe to construct an early video-synthesizer that allowed Paik to combine and manipulate images from different sources. The Paik-Abe video synthesizer transformed electronic moving-image making. Paik invented a new artistic medium with television and video, creating an astonishing range of artworks, from his seminal videotape <i>Global Groove</i> (1973) that broke new ground, to his sculptures <i>TV Buddha</i> (1974), and <i>TV Cello</i> (1971); to installations such as <i>TV Garden</i> (1974), <i>Video Fish</i> (1975) and <i>Fin de Siecle II</i> (1989); videotapes <i>Living with the Living Theatre</i> (1989) and <i>Guadalcanal Requiem</i> (1977/1979); and global satellite television productions such as <i>Good Morning Mr. Orwell,</i> which broadcast from the Centre Pompidou in Paris and a WNET-TV studio in New York City Jan. 1, 1984.</p> <p>Paik has been the subject of numerous exhibitions, including two major retrospectives, and has been featured in major international art exhibitions including Documenta, the Venice Biennale and the Whitney Biennial. The Nam June Paik Art Center opened in a suburb of Seoul, South Korea, in 2008.</p><p>Smithsonian American Art Museum "
				The Smithsonian American Art Museum Acquires the Complete Estate Archive of Visionary Artist Nam June Paik " (Washington, D.C.: Smithsonian American Art Museum, press release, May 1, 2009)</p>",
				format: "full_html",
				processed: "<p class="
				noindent ">Nam June Paik (1932&ndash;2006), internationally recognized as the "
				Father of Video Art,
				" created a large body of work including video sculptures, installations, performances, videotapes and television productions. He had a global presence and influence, and his innovative art and visionary ideas continue to inspire a new generation of artists.</p> <p>Born in 1932 in Seoul, Korea, to a wealthy industrial family, Paik and his family fled Korea in 1950 at the outset of the Korean War, first to Hong Kong, then to Japan. Paik graduated from the University of Tokyo in 1956, and then traveled to Germany to pursue his interest in avant-garde music, composition and performance. There he met John Cage and George Maciunas and became a member of the neo-dada Fluxus movement. In 1963, Paik had his legendary one-artist exhibition at the Galerie Parnass in Wuppertal, Germany, that featured his prepared television sets, which radically altered the look and content of television.</p> <p>After immigrating to the United States in 1964, he settled in New York City where he expanded his engagement with video and television, and had exhibitions of his work at the New School, Galerie Bonino and the Howard Wise Gallery. In 1965, Paik was one of the first artists to use a portable video camcorder. In 1969, he worked with the Japanese engineer Shuya Abe to construct an early video-synthesizer that allowed Paik to combine and manipulate images from different sources. The Paik-Abe video synthesizer transformed electronic moving-image making. Paik invented a new artistic medium with television and video, creating an astonishing range of artworks, from his seminal videotape <i>Global Groove</i> (1973) that broke new ground, to his sculptures <i>TV Buddha</i> (1974), and <i>TV Cello</i> (1971); to installations such as <i>TV Garden</i> (1974), <i>Video Fish</i> (1975) and <i>Fin de Siecle II</i> (1989); videotapes <i>Living with the Living Theatre</i> (1989) and <i>Guadalcanal Requiem</i> (1977/1979); and global satellite television productions such as <i>Good Morning Mr. Orwell,</i> which broadcast from the Centre Pompidou in Paris and a WNET-TV studio in New York City Jan. 1, 1984.</p> <p>Paik has been the subject of numerous exhibitions, including two major retrospectives, and has been featured in major international art exhibitions including Documenta, the Venice Biennale and the Whitney Biennial. The Nam June Paik Art Center opened in a suburb of Seoul, South Korea, in 2008.</p><p>Smithsonian American Art Museum "
				The Smithsonian American Art Museum Acquires the Complete Estate Archive of Visionary Artist Nam June Paik " (Washington, D.C.: Smithsonian American Art Museum, press release, May 1, 2009)</p>",
				summary: ""
			},
			associated_places: [
				"New York, New York, United States"
			],
			birth_place: "Seoul, Korea",
			birth_year: "1932",
			date_of_birth: "1932-07-20",
			date_of_death: "2006-01-29",
			death_place: "Miami Beach, Florida, United States",
			death_year: "2006",
			display_date: "born Seoul, Korea 1932-died Miami Beach, FL 2006",
			firstname: "Nam June",
			last_known_place: null,
			lastname: "Paik",
			luce_artist_biography: null,
			name_prefix: null,
			name_suffix: null,
			name_title: null
		},
		relationships: {
			artworks: {
				data: [{
						type: "artworks",
						id: "c82ead12-49c5-4812-a56c-39990d047d55"
					},
					{
						type: "artworks",
						id: "1880dd22-e0a6-4ea1-b7a3-78f4093722ad"
					},
					{
						type: "artworks",
						id: "a573d419-0884-4e55-bcb8-2363293f3224"
					},
					{
						type: "artworks",
						id: "403f94ae-b6cc-4f13-82df-f6954abe9535"
					},
					{
						type: "artworks",
						id: "b91a6337-53bf-40c5-a7a7-9d554c0203f4"
					},
					{
						type: "artworks",
						id: "e039db23-925b-421b-b75b-e4c5dccf5b5d"
					},
					{
						type: "artworks",
						id: "646236cf-c464-43aa-a340-e7eecd4fbbc6"
					},
					{
						type: "artworks",
						id: "d62ad533-a6eb-4f5e-a550-1bcbfed38909"
					},
					{
						type: "artworks",
						id: "302c3d18-58d3-45b6-bd71-d2ffe2db3d01"
					},
					{
						type: "artworks",
						id: "ea21b748-baac-4957-8f68-6e1f684112dc"
					},
					{
						type: "artworks",
						id: "3b929ab9-f464-48dc-bd5e-97fe4b29bc1e"
					},
					{
						type: "artworks",
						id: "96afab58-12b2-4623-894e-657447b0daae"
					},
					{
						type: "artworks",
						id: "dd19ac03-04e8-4d20-bfe9-ecfc238ebd54"
					},
					{
						type: "artworks",
						id: "65628820-2d2d-4fda-8478-24a60fbb3518"
					},
					{
						type: "artworks",
						id: "e86b3d12-4c6a-4246-b75a-7db019ad2596"
					},
					{
						type: "artworks",
						id: "eba8d5fe-fb45-41ed-a0c5-8c27845f91e2"
					},
					{
						type: "artworks",
						id: "fa82877c-d6ae-4d18-8db2-a3e5cc7558e9"
					},
					{
						type: "artworks",
						id: "1317ca43-5105-468f-b6cf-6af978c6bed2"
					},
					{
						type: "artworks",
						id: "0b57c7ac-ad2a-4e6a-ac37-412fcc8b57af"
					},
					{
						type: "artworks",
						id: "3deadeb2-24e0-46c8-8c93-00455383205f"
					},
					{
						type: "artworks",
						id: "adb77ef5-2dc5-41df-ba82-1e1ad93c70f9"
					},
					{
						type: "artworks",
						id: "d46b7769-a509-432d-b9b1-3b9ff78a749b"
					},
					{
						type: "artworks",
						id: "f794a664-ef2b-4425-9473-7be6711a6bfa"
					},
					{
						type: "artworks",
						id: "9369c820-5c92-425b-9dc3-09e80c64273e"
					},
					{
						type: "artworks",
						id: "808a1cfb-dc77-4b5e-b3f8-062baf3f3269"
					},
					{
						type: "artworks",
						id: "83b201af-f277-4de4-8874-9f0ad93083e6"
					},
					{
						type: "artworks",
						id: "b8562ddc-8441-4cfb-86c6-9fe0b07faad9"
					},
					{
						type: "artworks",
						id: "375c8ff9-7682-4d2a-aaf7-41899e8c2c73"
					},
					{
						type: "artworks",
						id: "5d78b19a-0519-47ef-9713-442f24ce800a"
					},
					{
						type: "artworks",
						id: "939e1b92-d8e5-48ab-8e82-b62db82afb3b"
					},
					{
						type: "artworks",
						id: "8015f91b-2919-4ac9-805e-58d9df3ef7c5"
					},
					{
						type: "artworks",
						id: "4448da5f-7dfd-4e3c-8ae1-425ff239e939"
					},
					{
						type: "artworks",
						id: "894dd73b-75b9-4e98-8099-80840bcad55f"
					},
					{
						type: "artworks",
						id: "9267eae4-29f5-447d-b144-fa3f60a34cd0"
					},
					{
						type: "artworks",
						id: "d6d04dca-d747-4e64-8bff-8cf222861d07"
					},
					{
						type: "artworks",
						id: "d398957c-7f94-4716-a998-35ee89c14c5d"
					},
					{
						type: "artworks",
						id: "46befa70-afd8-48b2-8bbc-602fcf1695c6"
					},
					{
						type: "artworks",
						id: "2f7f183f-66f4-4551-9737-47dfcb3a1757"
					},
					{
						type: "artworks",
						id: "4e8651ab-8c95-4ffd-95e6-d3210977e972"
					}
				],
				links: {
					self: "https://api.si.edu/saam/v1/artists/4039d113-5302-426d-9c9d-e4bf3db87f7e/relationships/artworks"
				}
			},
			nationalities: {
				data: {
					type: "nationalities",
					id: "d0245a03-9f85-4050-a80f-4a444aee1e10"
				},
				links: {
					self: "https://api.si.edu/saam/v1/artists/4039d113-5302-426d-9c9d-e4bf3db87f7e/relationships/nationalities"
				}
			},
			related_books: {
				data: [{
					type: "books",
					id: "c6157886-b371-4253-9217-871195c05daa"
				}],
				links: {
					self: "https://api.si.edu/saam/v1/artists/4039d113-5302-426d-9c9d-e4bf3db87f7e/relationships/related_books"
				}
			},
			us_states: {
				data: [{
					type: "us_states",
					id: "cef3c250-8719-40ea-8572-7e921a5f3a8c"
				}],
				links: {
					self: "https://api.si.edu/saam/v1/artists/4039d113-5302-426d-9c9d-e4bf3db87f7e/relationships/us_states"
				}
			}
		},
		links: {
			self: "https://api.si.edu/saam/v1/artists/4039d113-5302-426d-9c9d-e4bf3db87f7e"
		}
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
	data: {
		type: "institutions",
		id: "1f2ef80a-897c-46f6-8824-991e6d320e48",
		attributes: {
			uuid: "1f2ef80a-897c-46f6-8824-991e6d320e48",
			title: "U.S. Mint",
			created: "2017-06-07T00:45:01-0400",
			path: {
				alias: "/institution/us-mint-27696",
				pid: 1674131,
				langcode: "en"
			},
			alphabetical_name: "U.S. Mint",
			display_date: null
		},
		relationships: {
			artworks: {
				data: [{
						type: "artworks",
						id: "2f462422-4cf8-415c-a7cb-5cb792e7310e"
					},
					{
						type: "artworks",
						id: "450972dd-d796-49ce-93b4-09a6a45ccc01"
					},
					{
						type: "artworks",
						id: "991eb4f8-0621-4bee-8e7c-00ec3ec2a807"
					},
					{
						type: "artworks",
						id: "0cf4315c-96e9-46d3-9a84-3bdf469408e8"
					},
					{
						type: "artworks",
						id: "d34b0b74-4e31-49ef-a9b9-ffdc22c9a570"
					},
					{
						type: "artworks",
						id: "acd952b1-9e0c-44c4-8b98-865aca830eb5"
					}
				],
				links: {
					self: "https://api.si.edu/saam/v1/institutions/1f2ef80a-897c-46f6-8824-991e6d320e48/relationships/artworks"
				}
			},
			nationalities: {
				data: {
					type: "nationalities",
					id: "d0245a03-9f85-4050-a80f-4a444aee1e10"
				},
				links: {
					self: "https://api.si.edu/saam/v1/institutions/1f2ef80a-897c-46f6-8824-991e6d320e48/relationships/nationalities"
				}
			}
		},
		links: {
			self: "https://api.si.edu/saam/v1/institutions/1f2ef80a-897c-46f6-8824-991e6d320e48"
		}
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
	data: {
		type: "exhibitions",
		id: "dc4bf972-f39e-44c8-ba14-f44c9fab54c8",
		attributes: {
			uuid: "dc4bf972-f39e-44c8-ba14-f44c9fab54c8",
			title: "Nam June Paik: Global Visionary",
			changed: "2018-04-11T09:08:58-0400",
			path: {
				alias: "/exhibitions/paik",
				pid: 579029,
				langcode: "en"
			},
			description: {
				value: "<p>The artwork and ideas of the Korean-born artist Nam June Paik were a major influence on late twentieth-century art and continue to inspire a new generation of artists. <em>Nam June Paik: Global Visionary</em> offers an unprecedented view into the artist’s creative method by featuring key artworks that convey Paik’s extraordinary accomplishments as a major international artist as well as material drawn from the Nam June Paik Archive, which was acquired by the Smithsonian American Art Museum from the artist’s estate in 2009.</p> ",
				format: "basic_html",
				processed: "<p>The artwork and ideas of the Korean-born artist Nam June Paik were a major influence on late twentieth-century art and continue to inspire a new generation of artists. <em>Nam June Paik: Global Visionary</em> offers an unprecedented view into the artist’s creative method by featuring key artworks that convey Paik’s extraordinary accomplishments as a major international artist as well as material drawn from the Nam June Paik Archive, which was acquired by the Smithsonian American Art Museum from the artist’s estate in 2009.</p>",
				summary: ""
			},
			accession_number: "2002.23",
			archive_date: "2013-08-11",
			close_date: "2013-08-09T20:00:00-0400",
			display_date: null,
			gallery: "American Art Museum,3rd floor North",
			location: null,
			museum: "American Art Museum",
			offered_for_tour: false,
			open_date: "2012-12-12T19:00:00-0500",
			past_date: null,
			permanent_exhibition: false,
			post_date: "2010-12-07",
			travel_begin_date: null,
			travel_end_date: null,
			traveling: false
		},
		relationships: {
			exhibition_codes: {
				data: [{
					type: "exhibition_codes",
					id: "c5af4424-9bd6-4828-9f40-e140474a0abd"
				}],
				links: {
					self: "https://api.si.edu/saam/v1/exhibitions/dc4bf972-f39e-44c8-ba14-f44c9fab54c8/relationships/exhibition_codes"
				}
			},
			publication: {
				data: [{
					type: "books",
					id: "c6157886-b371-4253-9217-871195c05daa"
				}],
				links: {
					self: "https://api.si.edu/saam/v1/exhibitions/dc4bf972-f39e-44c8-ba14-f44c9fab54c8/relationships/publication"
				}
			}
		},
		links: {
			self: "https://api.si.edu/saam/v1/exhibitions/dc4bf972-f39e-44c8-ba14-f44c9fab54c8"
		}
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
| attributes.transcript | The audio plaintext transcript | string |

#### Example

`GET /saam/v1/audio/{{uuid}}` will get detailed info about a specific audio entity.


> ```
> https://api.si.edu/saam/v1/audio/8abede9a-b374-4255-9d05-723103cdede1
> ```
> Returns the full record for "Autonomy Cube".

#### Response

```json
{
	data: {
		type: "audio",
		id: "8abede9a-b374-4255-9d05-723103cdede1",
		attributes: {
			uuid: "8abede9a-b374-4255-9d05-723103cdede1",
			title: "Autonomy Cube",
			changed: "2018-05-30T14:39:42-0400",
			path: {
				alias: "/media/autonomy-cube-152619",
				pid: 1738628,
				langcode: "en"
			},
			description: {
				value: "<p><strong><em>Autonomy Cube</em></strong>, 2015<br /> Plexiglas cube with computer components<br /> Courtesy of the artist; Metro Pictures, New York; Altman Siegel, San Francisco</p> ",
				format: "basic_html",
				processed: "<p><strong><em>Autonomy Cube</em></strong>, 2015<br /> Plexiglas cube with computer components<br /> Courtesy of the artist; Metro Pictures, New York; Altman Siegel, San Francisco</p>",
				summary: ""
			},
			transcription: "Normally when you use the Internet there's lots and lots of people who can see what you're doing. Advertisers can track your movements across the Internet. Your local Internet service provider can look at the websites that you're visiting, and so on and so forth. The "
			Autonomy Cube " is a sculpture that tries to imagine what the Internet might look like if this were not the case. The creates an open wi-fi network that anybody in the museum can use. But when you connect to this network, it's a very different kind of Internet connection than you might otherwise have. It routs all the traffic over something called the Tor network, which is an infrastructure that sits on top of the Internet and is designed to create anonymity for people using the Internet. It does this by bouncing your Internet traffic through a series of relays around the world. If you use the Autonomy Cube, you might notice that you're being served webpages in Polish or Spanish, French, or German. And the reason for that is because the normal Internet thinks that you're an anonymous user at a random location somewhere else in the world. This Tor network was originally built by the military and by the State department in order to allow other people around the world to circumvent Internet censorship and surveillance in totalitarian countries. "
		},
		relationships: {
			file: {
				data: [{
					type: "files",
					id: "092ee54f-18c9-4ed0-a7e1-02795c2ef9b1",
					meta: {
						display: true,
						description: ""
					}
				}],
				links: {
					self: "https://api.si.edu/saam/v1/audio/8abede9a-b374-4255-9d05-723103cdede1/relationships/file"
				}
			}
		},
		links: {
			self: "https://api.si.edu/saam/v1/audio/8abede9a-b374-4255-9d05-723103cdede1"
		}
	},
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
	data: {
		type: "books",
		id: "2ad06661-5b8e-41ae-af2b-ddf7f7e5711e",
		attributes: {
			uuid: "2ad06661-5b8e-41ae-af2b-ddf7f7e5711e",
			title: "The Art of Video Games",
			changed: "2017-09-03T21:11:38-0400",
			path: {
				alias: "/books/video-games",
				pid: 574827,
				langcode: "en"
			},
			author: null,
			author_for_display: "Chris Melissinos",
			description: {
				value: "<p>In the forty-year history of the video game industry, the medium has undergone staggering development, fueled not only by advances in technology but also by an insatiable quest for richer play and more meaningful experiences. As a testament to the game industry’s stunning evolution, and to its cultural impact worldwide, the Smithsonian American Art Museum and curator Chris Melissinos conceived the 2012 exhibition <em>The Art of Video Games.</em> The exhibition offered a revealing look into the history of the game industry, from early days of <em>Pac-Man</em> and <em>Space Invaders</em> to the vastly more complicated contemporary epics such as <em>BioShock</em> and <em>Uncharted</em>. <em>The Art of Video Games</em> makes a compelling case for games to be viewed not just as mere play, but as richly textured, compelling experiences that have crossed the boundary into culture and art.</p> <p><a class="
				btn btn -
				default " href="
				http: //www.1shoppingcart.com/SecureCart/SecureCart.aspx?mid=86E5CC82-F584-4262-84F3-C331DD7228A1&amp;pid=e9b2764a4b5948eab21158f400109273">Add to Cart</a>&nbsp;Hardcover,&nbsp;<strike>$40.00</strike>&nbsp;$25.00</p> <p>&nbsp;</p> ",
					format: "full_html",
				processed: "<p>In the forty-year history of the video game industry, the medium has undergone staggering development, fueled not only by advances in technology but also by an insatiable quest for richer play and more meaningful experiences. As a testament to the game industry’s stunning evolution, and to its cultural impact worldwide, the Smithsonian American Art Museum and curator Chris Melissinos conceived the 2012 exhibition <em>The Art of Video Games.</em> The exhibition offered a revealing look into the history of the game industry, from early days of <em>Pac-Man</em> and <em>Space Invaders</em> to the vastly more complicated contemporary epics such as <em>BioShock</em> and <em>Uncharted</em>. <em>The Art of Video Games</em> makes a compelling case for games to be viewed not just as mere play, but as richly textured, compelling experiences that have crossed the boundary into culture and art.</p> <p><a class="
				btn btn -
				default " href="
				http: //www.1shoppingcart.com/SecureCart/SecureCart.aspx?mid=86E5CC82-F584-4262-84F3-C331DD7228A1&amp;pid=e9b2764a4b5948eab21158f400109273">Add to Cart</a>&nbsp;Hardcover,&nbsp;<strike>$40.00</strike>&nbsp;$25.00</p> <p>&nbsp;</p> ",
					summary: ""
			},
			book_title_display: "The Art of Video Games",
			dimensions: "10 1/2 x 10 1/3 in.",
			isbn_hardcover: "978-1-59962-110-4",
			isbn_softcover: null,
			pages: "260 pp.",
			publisher: null,
			year_published: 2012
		},
		relationships: {
			images: {
				data: [{
					type: "images",
					id: "836cca46-559a-4a44-83be-333d3e568395"
				}],
				links: {
					self: "https://api.si.edu/saam/v1/books/2ad06661-5b8e-41ae-af2b-ddf7f7e5711e/relationships/images"
				}
			}
		},
		links: {
			self: "https://api.si.edu/saam/v1/books/2ad06661-5b8e-41ae-af2b-ddf7f7e5711e"
		}
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
> https://api.si.edu/saam/v1/artworks/dd19ac03-04e8-4d20-bfe9-ecfc238ebd54?include=artwork_images,artwork_images.artwork_image,artists,classifications,highlights,locations
> ```
> Get a specific artwork, and include data for the artwork images and categories.


## Feedback

[Contact](https://github.com/Smithsonian/api-docs/issues) for issues or feedback related to the American Art API

