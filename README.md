- Repositary pattern
  - Interface between apps domain layer: business layer
  - Persistence layer: interaction with DB
  
  
- Materialize the relation  `to_a`


- Repository: Acts as an interface to working with `Articles` 
  - Methods in a repository return relation instances
  - relations can be chained and composed, but are not objects.
  - Once we finish the chaining of relations, we need to `materialize` the relation using `to_a`.  Materializing
  converts the Relation into `Structs`. Simple value objects that represent each record in the database that only contain
  the data the need.
    - This eliminates N+1 problems by design, since there is no way view can keep querying the db.
- Relations: Repositories work with one or more relations. Each relation is in charge of interaction with the DB.
each relation in charge of one DB table and stores the detailed query logic.

# Benefits
- Layers: clear layers of where tu put what. Relations at the front door, relations for query logic and structs
as instances of records.  Ensures that persistence details don't leak out to the application.
  - As DB grows keeps things organised.
- Narrow fit-for-purpose API: it is our job to explicitly define methods that satisfy each of the read / persistence
requirements of our app. Those methods have a clear place to live: the repository.
- Focus: ROM is focused on persistence only.  Other stuff like validation, callbacks or HTTP form post handling
are better handled in other places of the app with dedicated tools.
  - 
