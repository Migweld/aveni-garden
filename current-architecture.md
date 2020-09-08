# current-architecture

## Frontend

- Relatively static
  - Conforms to ideals of the JAMstack
  - FCP should be relatively quick
- Little or no use of memoisation, lots of waiting on the API
- Little or no use of optimistic updates. Data is up to date but slow given the probability of successful outcome.

### Sources

[JAMstack, do we really need it?](https://www.youtube.com/watch?v=YljH-aqKUFk)

## Backend

- Huge surface area. Difficult to build a mental model of any one system
- API closely-coupled with business logic. Very bloated
- Difficulty in following what does what, especially if the domain logic and nomenclature is specialised
- Well-named handlers aids comprehension but they're massive, lots of logic in one place
- Seems quite WET
- Difficult to test, particularly black-box testing
- Seems to be largely a serverless monolith

## Non-specific architecture

- Difficult to make sense of logs, so much information
