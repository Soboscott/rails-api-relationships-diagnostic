# Rails API Relationships Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  Describe a reason why a join tables may be valuable.

  ```md
    # < Because it creates a pair of one to many relationships which is easier to
    manage and change than a many to many relationship >
  ```

1.  Provide a database table structure and explain the Entity Relationship that
  describes a many-to-many relationship for `Profiles`, `Movies` and `Favorites`
  (Think of Netflix). A `Profile` has a `given_name`, `surname` and `email` and a
  `Movies` have `title`, `release_date`, and `length` and `Favorites` would be the
  join table with references to `Movies` and `Profiles`.

  ```md
    # <  Movies               Profile
                Favorites
        profiles have many movies through Favorites
        
 >
  ```

1.  For the above example, what needs to be added to the Model files?

  ```rb
  class Profile < ActiveRecord::Base
  class  Favorites Serializer < ActiveRecord::Base
  belongs_to :Profile
  validates :given_name, presence: true
  validates :surname, presence: true
  validates :email,presence: true

  end


  ```

  ```rb
  class Movie < ActiveRecord::Base
  belongs to:Profile
  validates title, presence: true
  validates :relese_date, presence: true
  validates :lenght, presence: true
  end

  end
  ```

  ```rb
  class Favorite < ActiveRecord::Base
  end
  ```

1.  What is the purpose of a serializer? What would our `Profile` serializer look
like to show all movies favorited by a profile on
`http://localhost:3000/profiles/1`

  ```md
    # < it would be a json file that would look like this:
    "profile": {
        "ID": 1,
        }
 >
  ```

  ```rb
  class ProfileSerializer < ActiveModel::Serializer
    attributes :id,
end
  ```

1.  What would the command be to _scaffold_ out a **join table** for Favorites from
the above `Movies` and `Profiles`.

  ```sh
    # < SELECT "moviess".* FROM "Movies" INNER JOIN "Profiles" ON "favorites"."user_id" = "users"."id" >
  ```

1.  What is `Dependent: Destroy` and where/why would we use it?

  ```md
    # < destroy deletes all associated objects.
    you could use it to remove a movie from Favorites>
  ```

1.  Think of **ANY** example where you would have a one-to-many relationship as well
as a many-to-many relationship in an application. You only need to list the
description about the resources and how they relate to one another.

  ```md
    # < one profile has many movies
        many profiles have many movies>
  ```
