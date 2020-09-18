# 2020 Google Summer of Code with Joplin


### What got done

The project consisted of three parts:
1. Make search better by introducing additional search filters. (e.g., tags, notebook, type)
2. Make the ranking of search results better by implementing the [Okapi BM25](https://en.wikipedia.org/wiki/Okapi_BM25) relevance function.
3. Make fuzzy search possible.


### Code contributions

1. [**All: Add search filters**](https://github.com/laurent22/joplin/pull/3213)  
    Joplin's search had been using the Full-Text Search(FTS) offered by SQLite directly. So though it was fast, it was not versatile. For example, we can't restrict the search scope to a particular notebook or search based on tags.

    The current search implementation fixes most of these problems. It provides a better abstraction over FTS, supporting many new filters. The documentation for the new search filters can be found [here.](https://github.com/laurent22/joplin#searching)

2. [**All: Weigh notes using Okapi BM25 score**](https://github.com/laurent22/joplin/pull/3454)   
	Joplin used a ranking function based on the number of times the search query occurs in the note and how close they are.

	But there are better ways to rank notes, considering not just the number of times a word appears, but how common it is. Words like "the" is in most notes, while words like "zebra" are not common and should be considered more relevant.

    The new search implementation uses [Okapi BM25](https://en.wikipedia.org/wiki/Okapi_BM25) as the ranking function. It ranks a set of documents based on the query terms appearing in each document, regardless of their proximity. 
3. [**Desktop: Fuzzy search**](https://github.com/laurent22/joplin/pull/3632)  
    We've added support for fuzzy search. It doesn't replace the need to put * at the end if you want to do a prefix search. But it does let you be a bit more relaxed about the exact spelling. Searching for "tomatos" will also give you results for "tomatoes". (This feature isn't released yet, but will be soon)
    
It was a pleasure working with [Laurent](https://github.com/laurent22) and [Caleb](https://github.com/CalebJohn). They did an excellent job as mentors.
