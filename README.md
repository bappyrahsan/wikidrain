wikidrain
===================================================================================

A PHP wrapper for the WikiMedia API centralized around querying Wikipedia articles.

There are many php classes, indeed complete frameworks, dedicated to the WikiMedia
API. But none of them are easy to implement, are accessible to those just learning
PHP, or focus on simply querying data from Wikipedia.  The goal of the wikidrain 
project is to develop a production-quality PHP library dedicated to easy, simple, 
and efficient querying of Wikipedia articles.

Wikidrain currently returns all data as XML, but that is easily changed, to say JSON,
by editing the $_apiURL property.


Usage:
===================================================================================

wikidrain is very simple to use, just make a new instance of wikidrain:

    <?php
    $wiki = new wikidrain();
    ?>

To search wikipedia for articles, use the Search($query) method:

    <?php
    $wiki = new wikidrain();
    $result = $wiki->Search('API');
    ?>

To get the sections of a wikipedia page, use the getSections($title) method:

    <?php
    $wiki = new wikidrain();
    $result = $wiki->getSections('API');
    ?>

NOTE: wikidrain does not include any error checking/verification that the article
      exists, so be sure to only request the sections/text of articles that were
      returned by the Search($query) method...

To get the text of a section from a wikipedia page, use the getText($title, $section)
method.

    <?php
    $wiki = new wikidrain();
    $result = $wiki->getText('API', '0');
    ?>

NOTE: again, wikidrain does not include any error checking/verification to determine
      if an article or section exists, so make sure to only request data from pages/
      sections returned by the Search($query) and getSections($title) methods...

TODO:
===================================================================================

Currently, the objectives are as follows:

1. Inclusion of a method to pull the "See Also" as an array, not just as a a section
   accessible by the getSection method

2. An integrated class (or method) to parse the XML and return just text [In the works]

3. An integrated class (or method) to parse the WikiText and pull an array of the
   linked articles

4. Anything to put less strain on the wikipedia servers

5. A method to return the wikipedia donation banner