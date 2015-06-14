# The ShowRoom

The ShowRoom is a web app that allows bar owners to display posts, specials, and 
band showtimes, along with pictures and video uploads.

## Domain Model
(All models include `timestamps`)


### User

Represents any user than can log in.

* email:string
* password_digest:string

* has_many :user_roles


### UserRoles

A User can have any number of roles, like admin, poster, moderator, etc

* name:string

* belongs_to :user


### Venue

A bar that may or may not have a stage for bands

* name:string
* address_line_1:string
* address_line_2:string
* city:string
* state:string
* zip:string

* has_many :owners, class: 'User'
* has_many :posts
* has_many :specials
* has_many :bands


### Sale Specials

A drink or food special that runs for a limited time

* name:string (optional)
* description:string
* starts_at:datetime
* ends_at:datetime


### Bands

* name:string
* contact_phone:string
* website:string

* belongs_to :venue
* has_one :show_schedule


### ShowSchedule

A schedule is a collection of showtimes with start and end datetimes.

* has_many show_times


### ShowTime

* name:string
* starts_at:datetime
* ends_at:datetime

* belongs_to show_schedule
