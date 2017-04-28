# Playwaze Open Data

## Open Data Endpoint
https://playwaze.com/Webservices/Playwazeservice.svc/Groupplay/GetOpenActiveData - a feed of the data from the Playwaze app
You can also add a sport parameter if you only want to return courses and sessions for one particular sport e.g. 
https://playwaze.com/Webservices/Playwazeservice.svc/Groupplay/GetOpenActiveData?sport=Tennis

## Standards
The data is published to conform to [Openactive Realtime Paged Data Exchange 0.2.3](https://www.openactive.io/realtime-paged-data-exchange/0.2.3/).

## Issues, Questions and Comments
Please raise any issues, questions or comments as a [new issue in this repository](https://github.com/playwaze/opendata/issues).

## Data structure
The Playwaze data feed returns two types of data item: Course and Session. Both are bookable items. Both have a header Group Play node which provides the summary data for the course or session. Courses are made up of multiple occurences e.g. multiple days / times / locations. Sessions are individually bookable, but can also be "joined" at the Group Play node level. In the latter instance the user is not booking onto a specific session but joining the Sessions group (on the Playwaze app) and can then book directly onto individual sessions there.

## Data Fields for Courses
A Course is treated as a single bookable activity containing one or more occurences i.e. dates the course runs on. Users cannot book onto the individual occurences - they may only book onto the whole course.

### Group Play Node (Course)
| Data Field | Example Value | Description |
|---|---|---|
| activity_description | "A beginners course for all ages"  | Course description | 
| activity_name | "Tennis Introductory Course"  | Course name |
| community_description | "A friendly tennis club in Guildford"  | Description of the club/group/coach running the course | 
| community_name | "Acme Tennis Club"  | Name of the club/group/coach running the course |
| community_id | "CommunityDocuments/tg45hdgqsiki"  | Internal ID of the community in Playwaze | 
| currency | "£"  | The currency the price is set in |
| image_url | URL | An image for the Course |
| join_url | URL  | The booking link for a Course | 
| max_participants | 12  | Maximum number of participants on the Course |
| places_booked | 3  | Number of places already booked on the Course |
| price | 10  | Price of the Course | 
| sport | "Tennis"  | Sport or activity type | 

### Data Node (Course)
| Data Field | Example Value | Description |
|---|---|---|
| currency | null | Will always be null for a Course as it is specified in the Group Play node | 
| start_date | "2017-04-22T10:00:00Z"  | The start date/time of the first occurence in this Course |
| end_date | "2017-04-24T14:00:00Z"  | The end date/time of the last occurence in this Course |
| facility | null  | Will always be null for a Course as it is specified in each occurence node | 
| location | null  | Will always be null for a Course as it is specified in each occurence node |
| image_url | null  | Will always be null for a Course as images are specified in the Group Play node (for the whole course) or each individual occurence node (for each session within the Course) |
| join_url | null  | Will always be null for a Course as it is specified in the Group Play node | 
| lat | null  | Will always be null for a Course as it is specified in each occurence node |
| lng | null  | Will always be null for a Course as it is specified in each occurence node |
| organizer_name | null  | Will always be null for a Course as it is specified in each occurence node | 
| organizer_email | null  | Will always be null for a Course as it is specified in each occurence node | 
| organizer_tel | null  | Will always be null for a Course as it is specified in each occurence node | 
| max_participants | null  | Will always be null for a Course as it is specified in the Group Play node |
| places_booked | null  | Will always be null for a Course as it is specified in the Group Play node |
| price | 0  | Will always be 0 for a Course as it is specified in the Group Play node | 
| url | null  | Will always be null for a Course as it is specified in each occurence node |
| notes | null  | Will always be null for a Course as it is specified in each occurence node | 

### Occurence Node (Course)
| Data Field | Example Value | Description |
|---|---|---|
| start_date | "2017-04-22T10:00:00Z"  | The start date/time of this course occurence |
| end_date | "2017-04-24T14:00:00Z"  | The end date/time of this course occurence |
| facility | "Courts 1- 4"  | The facility where the occurence will take place |
| location | "54 High Street, Swindon"  | The geographical location of this course occurence | 
| lat | 51.306975  | The latitude coordinate of this course occurence |
| lng | -0.5783936  | The longitude coordinate of this course occurence |
| id | "6fv3j8apzbs"  | Internal ID of the course occurence in Playwaze |
| image_url | URL  | An image for the course occurence |
| notes | "Please bring your own racquet"  | Notes for this course occurence | 
| organizer_name | "Joe Bloggs"  | The name of the organizer for this course occurence | 
| organizer_email | "jbloggs@playwaze.com"  | The email address of the organizer for this course occurence | 
| organizer_tel | "01234 567890"  | The telephone number of the organizer for this course occurence | 
| url | URL  | A link to some info about this course occurence |

## Data Fields for Sessions
Sessions are contained within a Group Play and can be booked individually or joined as a whole at the Group Play level.

### Group Play Node (Session)
| Data Field | Example Value | Description |
|---|---|---|
| activity_description | "Mixer sessions for anyone under 16 years old"  | Description of the sessions | 
| activity_name | "Junior Badminton Mixer"  | Name of the sessions |
| community_description | "A friendly badminton club in Richmond"  | Description of the club/group/coach running the sessions | 
| community_name | "Acme Badminton Club"  | Name of the club/group/coach running the sessions |
| community_id | "CommunityDocuments/tg45hdgqsiki"  | Internal ID of the community in Playwaze | 
| currency | null  | Will always be null for a Session as it is specified in the data node |
| image_url | URL | An overall image for all the sessions linked to this Group Play |
| join_url | URL  | A join up link which enables people to sign up to the sessions schedule (they can join each one through the Playwaze app) | 
| max_participants | null  | Will always be null for a Session as it is specified in the data node |
| places_booked | 0  | Will always be 0 for a Session as it is specified in the data node |
| price | 0  | Will always be 0 for a Session as it is specified in the data node | 
| sport | "Badminton"  | Sport or activity type | 

### Data Node (Session)
| Data Field | Example Value | Description |
|---|---|---|
| currency | "£" | The currency the price is set in | 
| start_date | "2017-04-22T10:00:00Z"  | The start date/time of this Session |
| end_date | "2017-04-24T14:00:00Z"  | The end date/time of this Session |
| facility | "Courts 1- 2"  | The facility where the session will take place |
| location | "54 High Street, Richmond"  | The geographical location of this Session |  
| image_url | URL  | An image for the Session |
| join_url | null  | The booking link for this Session | 
| lat | 51.306975  | The latitude coordinate of this Session |
| lng | -0.5783936  | The longitude coordinate of this Session |
| organizer_name | "Joe Bloggs"  | The name of the organizer for this Session | 
| organizer_email | "jbloggs@playwaze.com"  | The email address of the organizer for this Session | 
| organizer_tel | "01234 567890"  | The telephone number of the organizer for this Session | 
| max_participants | 20  | Maximum number of participants on this Session |
| places_booked | 14  | Number of places already booked on this Session |
| price | 8  | Price of the Session | 
| url | URL  | A link to some info about this Session |
| notes | "Two hour basics session with Joe Bloggs"  | Notes for this Session occurence |
| occurence | null  | Will always be null for a Session |

## Changelog

| Date | Changes |
|---|---|
| 20/04/2017 | Initial version published |

