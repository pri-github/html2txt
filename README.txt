********************************************************************
                     D R U P A L    M O D U L E
********************************************************************
Name: html2txt module
Author: Robert Castelo <services at cortextcommunications dot com>
Drupal: 4.6.x
********************************************************************
DESCRIPTION:

This module converts HTML into plain text.

- It is a library of functions for use by other modules.

- Don't install it unless another module asks you to, or if you need this 
  functionality in a module you are developing.

Features include:

H1, H2, H3 text is converted to uppercase
* is added to list items
Links can be listed at the bottom of the text or (inline like this)
Local relative links converted to absolute
HR line is converted to dashed line '---------------------'
HTML entities converted to plain text equivalent, e.g. (c) 



********************************************************************
INSTALLATION:

Note: It is assumed that you have Drupal up and running.  Be sure to
check the Drupal web site if you need assistance.  If you run into
problems, you should always read the INSTALL.txt that comes with the
Drupal package and read the online documentation.

1. Place the entire html2txt directory into your Drupal modules/
   directory.

2. Enable the html2txt module by navigating to:

     administer > modules
     
  Click the 'Save configuration' button at the bottom to commit your
  changes.
  
  
********************************************************************
USAGE (API):

In your module:

$plain_text = html2txt_convert($html, $width, $links_inline, $allowed_tags);

INPUTS:

$html : 
     String
     The HTML string to be converted to plain text
     
$width (optional): 
     Integer
     The length lines should be wrapped to, default is no wrap
     
$links_inline (optional): 
     Boolean
     
     TRUE
     Show links in text body, example: 
     "blagh blagh linked text (http://www.url.com) blagh"
     
     FALSE
     Show links as an annotated list, example:
          Body: 
               "blagh blagh linked text[1] blagh, different linked text[2] blagh"
          Links:
               [1] http://www.url.com
               [2] http://www.other-url.com
               
     Default is FALSE
     
$strip_tags (optional):
     String
     
     A string containing any tags to be left in the text, example:
          '<pre><hr><blockquote><img>'
          
     Default is no tags allowed

OUTPUTS:

     Object
     
     $plain_text->text
          Plain text converted version of the HTML string
          
     $plain_text->links
          If $links_inline = FALSE, this contains list of annotated links.
          If $links_inline = TRUE, this is empty (do not use).


