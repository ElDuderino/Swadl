Swadl
=====

Swagger-styled wadl documentation viewer.

This project uses xslt stylesheets to massage auto-generated wadls into human
readable documentation. It was built off the efforts of:


* Mark Nottingham: http://github.com/mnot/wadl_stylesheets/tree/master
* Mark Sawers: https://github.com/ipcsystems/wadl-stylesheet
* Swagger: http://swagger.wordnik.com/


This software is available under the MIT license, and can be used in any way
you see fit.


Usage
-----

To get started, download the project and view wadl.html in your favorite local
web server. You should see something that looks like this:

> http://ehearty.github.io/Swadl/wadl.html

Edit the name and location of the xmlDoc variable at the top of the header
section to point to your wadl. The variable currently points to test.wadl as a
working example. 


### Breakdown

* screen.css - Edit this to change the style, format, whatever...you'll
  probably want to change the logo :-)
* wadl.xsl - The wadl transform stylesheet. Generates the document fragment
  that contains the wadl definition.
* wadl.html - Where the magic happens. Contains javascript that should
  probably be moved into an official controller.
* xsd.xsl - This file processes secondary grammar files associated with
  the wadl. Class definitions are injected into the document *after* wadl.xsl
  has finished processing.
* js/ - Directory containing jquery library...and future home of the
  controller library.
* application.wadl/ - Directory containing the grammar file associated with
  test.wadl. Only for test purposes.
* test.wadl - Sample hello world wadl file with associated grammar. This wadl
  was generated with Jersey's extended wadl annotations (which allow you to
  add additional documentation to your service).

### Recommendations

Swadl works best when deployed as part of your web service. Point it to the
auto-generated wadl and you'll always have up-to-date documentation.

Use Jersey's extended wadl annotations. They're great, and use plain vanilla
javadoc, which you should probably be using anyway :-)

### Notes

Q: Don't want to show the search bar on top of the page? 

  A: Update #header in screen.css with display:none.



Q: Nothing loads when I use the search bar?! 

  A: This might be due to several reasons:
* The transform sheet wasn't able to parse the wadl that you provided.
      That's probably my fault, and I'd be happy to fix the bug if you let me
      know.
* There might be a cross domain restriction on the page. These are a
      pain to address, imho, and it's why I suggest hosting Swadl on the same
      domain as your wadl resources.
* The page might not be able to reach the link (maybe it's on a
      vpn...or you fat-fingered the url). 


Q: What do I do if I find a problem?
  
A: Submit an issue in Git. Better yet, fork the repo, fix the bug, and send
  me a pull request ;-)
