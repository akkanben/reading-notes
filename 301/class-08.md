Reading Notes 08 - APIs

## APIs

From [API Design Best Practices](https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-design)

### Questions


1. What does REST stand for?
  - REpresentational State Transfer
2. REST APIs are designed around a ... .
  - Designed around client accessible data/object/services via resources.
3. What is an identifier of a resource? Give an example.
  - A resource could be a file like our weather.json files.
4. What are the most common HTTP verbs?
  - GET, PUT, POST, DELETE, PATCH
5. What should the URIs be based on?
  - Typically they should be based on nouns instead of verbs.
6. Give an example of a good URI.
  - `https://akkanben-city-explorer.herokuapp.com/weather`
7. What does it mean to have a ‘chatty’ web API? Is this a good or a bad thing?
  - A chatty API is one with many small resources receiving many requests. It's not great. Bigger resources with fewer requests is likely better.
8. What status code does a successful GET request return?
  - 200
9. What status code does an unsuccessful GET request return?
  - 404
10. What status code does a successful POST request return?
  - 201
11. What status code does a successful DELETE request return?
  - 204

## Regular Expressions

- I can match my name in a number of ways:
  - Just matching the letters b-e-n case insensitive globally `/ben/gi`
  - The letter b-e-n but not in the middle of a word insensitive/global `/\b(ben)\b/gi`

From [RegExr](https://regexr.com/) & [Factorymind Regex Tutorial](https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285) & [Regex101](https://Regex101.com)

## Things I want to know more about

- I wanna be a regex pro, both file globbing and regex are so cool xD
- There is so much more about REST/async/errors/etc that I want practice with.

