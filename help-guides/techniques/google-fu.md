# Google-Fu

_By_ [_Isaac_](/members/members/isaac.md)

As a technical person, as funny as it might sound, there is one skill that is as essential as any other to know if you're to be as successful as possible, and that is being able to google well (or DuckDuckGo well, or... bing well? lol).

One's immediate instinct may be something like "Google well? I can type what I want into a search engine and an answer will usually come up that answers it", and that may be true, but odds are the search term is either inefficient or, more likely, what you want is too specific to reasonably be found in a single search term...

Or so you may think.

There are in fact many different ways you can manipulate a search term to get more precise results, using Google's in-built operator functions. this list will go through a few of them.

Note: Many, but not all of these tips will apply to other browsers (most popularly amongst Hackers, DuckDuckGo), for further information, consult the [Docs](https://help.duckduckgo.com/duckduckgo-help-pages/results/syntax/)

## Standard Advanced Search Operators

Google has an "[Advanced Search](https://www.google.co.uk/advanced_search)" functionality, where a user can input more precised, advanced search terms into a form, and the corresponding search string is spat out and the user is redirected to that search, this section will cover these operators.

- Standard Search: search a link for any instance of any word in the search field, what one would typically imagine a google search to be, for example, `frog and toad` would return all results with the words "frog" "and" and "toad" in, with the most relevant towards the top
- Exact phrase: use `"` operator to find an exact phrase in a google search, e.g `"frog and toad"` would return results with the literal string "frog and toad"
- Any of these words: use the `|` or `OR` operators to return a result including either `term x` or `term y`, e.g `frog | toad` or `frog OR toad`
- None of these words: use the `-` operator *directly* before a term to exclude that term from results, e.g. `frog -toad` will return results containing the word "frog" but explicitly *not* "toad"
- Number range: use `..` between two numerical values to find search results with numbers in that range, e.g. `"born in" 1981..1996` would find results for people who are in the generally accepted range "Milennial"

## Dorking

this cheat sheet found [here](https://gist.github.com/sundowndev/283efaddbcf896ab405488330d1bbc06), with thanks to the author, sundowndev 

| Filter          | Description                                        | Example                              |
| :-------------- |:---------------------------------------------------| :------------------------------------|
| allintext      | Searches for occurrences of all the keywords given. | `allintext:"keyword"` |
| intext      | Searches for the occurrences of keywords all at once or one at a time. | `intext:"keyword"` |
| inurl      | Searches for a URL matching one of the keywords. | `inurl:"keyword"` |
| allinurl      | Searches for a URL matching all the keywords in the query. | `allinurl:"keyword"` |
| intitle      | Searches for occurrences of keywords in title all or one. | `intitle:"keyword"` |
| allintitle      | Searches for occurrences of keywords all at a time. | `allintitle:"keyword"` |
| site      | Specifically searches that particular site and lists all the results for that site. | `site:"www.google.com"` |
| filetype      | Searches for a particular filetype mentioned in the query. | `filetype:"pdf"` |
| link      | Searches for external links to pages. | `link:"keyword"` |
| numrange      | Used to locate specific numbers in your searches. | `numrange:321-325` |
| before/after      | Used to search within a particular date range. | `filetype:pdf & (before:2000-01-01 after:2001-01-01)` |
| allinanchor (and also inanchor)      | This shows sites which have the keyterms in links pointing to them, in order of the most links. | `inanchor:rat` |
| allinpostauthor (and also inpostauthor)      | Exclusive to blog search, this one picks out blog posts that are written by specific individuals. | `allinpostauthor:"keyword"` |
| related      | List web pages that are “similar” to a specified web page. | `related:www.google.com` |
| cache      | Shows the version of the web page that Google has in its cache. | `cache:www.google.com` |

