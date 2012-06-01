# SEOstats: SEO data library for PHP

SEOstats is a powerful open source tool to get a lot of SEO relevant data such as detailed backlink analyses, keyword and traffic statistics, website trends, page authority, the Google Pagerank, the Alexa Trafficrank and much more. 

SEOstats offers over 50 different methods to request SEO relevant data for websites and gathers data from Google, Yahoo, Bing, SEOmoz, Alexa, Facebook and Twitter.

## Note

The dev branch code is a work in progress. To get the latest stable release, use the master branch https://github.com/eyecatchup/SEOstats/tree/master or the downloads tab https://github.com/eyecatchup/SEOstats/downloads.

## Usage

### Brief Example of Use
You have several methods to define the URL to request data for.
```php
<?php
try {
  $url1 = "http://www.nahklick.de";
  $url2 = "http://www.bing.com";
  $url3 = "http://www.google.com";

  // Set a URL using the constructor function.
  $SEOstats = new SEOstats($url1);  
  print $SEOstats->Google()->getPageRank(); // prints 4

  // Set a URL using the `setUrl` function (overwrites any previously set URL). Eg:
  $SEOstats = new SEOstats($url1);
  $SEOstats->setUrl($url2);
  print $SEOstats->Google()->getPageRank(); // prints 8

  // Set a URL using optional parameter calls (overwrites any previously set URL). Eg:
  $SEOstats = new SEOstats($url1);
  $SEOstats->setUrl($url2); 
  print $SEOstats->Google()->getPageRank($url3); // prints 9  
} 
catch (SEOstatsException $e) {
  die($e->getMessage());
}
```

## SEOstats Google Methods

### Google Toolbar PageRank
 
```php
<?php  
  //  Returns the Google Toolbar PageRank.
  print $SEOstats->Google()->getPageRank();
```

### Google Pagespeed Service
 
```php
<?php   
  // Returns an array, containing the resultset for a 'Google Pagespeed' analysis. 
  print_r( $SEOstats->Google()->getPagespeedAnalysis() );

  // Returns the 'Google Pagespeed' analysis' total score.
  print $SEOstats->Google()->getPagespeedScore();
```

### Google Websearch Index
 
```php
<?php    
  // Returns the total amount of results for a Google site-search for the object URL.
  print $SEOstats->Google()->getSiteindexTotal();
 
  // Returns the total amount of results for a Google link-search for the object URL.
  print $SEOstats->Google()->getBacklinksTotal();
  
  // Returns the total amount of results for a Google search.
  print $SEOstats->Google()->getSearchResultsTotal("keyword");
```

## License

(c) 2012, Stephan Schmitz eyecatchup@gmail.com   
License: MIT, http://eyecatchup.mit-license.org   
URL: https://github.com/eyecatchup/SEOstats   
