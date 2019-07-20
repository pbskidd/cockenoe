# COCKENOE ISLAND CLUB

A demonstration of just how fast a website can be.  This fully responsive and graphical site loads the front page in a single server call at under 200ms* 
All images are encoded directly in the page, as is the extraordinarily spartan JavaScript and CSS. I first mocked up the page using jQuery and Twitter Bootstrap, but then wrote the subset of just functionality I needed by hand so that I could remove them and their overhead on performance. I noticed that SEO--especially at Google was disproportionally rewarded on such an overperforming site.  Since this experiment I have become an evangelist for clean web design. 

The second page incorporates many of the performance features of the first, but branches to demonstrate how easy it is to add basic eCommerce through third-party vendors.  basic product design, and embedding of the fulfillment channels was done in less than a day. Though this is not the most cost-efficient way to sell products on the Internet, it is an excellent way to do a functional mockup in a very short time.


*the favicon is sometimes seen as a second server call ;-P



NOTES ON OPTIMIZATON:

1. Analyze you site with https://gtmetrix.com  performance reports --record down the findings

2. Resave all images at the (maximum) dimensions that they will be displayed

3. Shrink all images tinypng.com (or compressor.io, or both, or multiple passes--if the quality is still acceptable) 

4. in your image tags, set the image width and height so that the page can render while the images are loading

5. If you have access, edit your .httaccess file to compress files with Gzip and to pre-load the content type (beamusup.com/generate-htaccess), also see example below.

6. consider using data URIs for images so that they can be loaded into either the html or (better) the CSS file to reduce server requests and can bE cached by the server (dataurl.net/#dataurlmaker). These make for cumbersome editing of their host files and are actually around 30% larger before Gzip, and are more client intensive to unzip.  They do however reduce server requests.

7. consider using sprit-emaps to combine all your images into one file and a single server request.  Like URIs, this makes re-editing cumbersome. Also, sprite-maps can be difficult to use in responsive images or where you are highly manipulating the images (ex. centered text overlays).

8. Run unCSS (from Python  , search github "unCSS"). Giving it your site url. It will generate a file of what it thinks are just the CSS elements you need. Test thoroughly and then replace your CSS with this.
9. Manually clean up your JavaScript. Remove any unused functions. Intellij might be able to help.  Add an "async" tag to any code that can load and run after the pageload.

10. minify your CSS

11. minify your JavaScript

12. if your CSS is small (under 10k), and you are not going to use a bunch of URIs, load your CSS into the HTML header to skip a server request. Do same for JavaScript.

13. minify your HTML (kangax.github.io/html-minifier) (use settings to take out white space, but leave blank tags) -Test!!

14. minimize your favicon.ico file with (reduceimagesize.org). Not very important since most browsers request it after loading



OTHER:
1. You will need to make changes. Use (unminify.com) to un-minify your compressed html, css, js. (www.dirtymarkup.com) also helps beautify code for editing and usability.

2. Consider converting simpler images to SVG vectors (vectormagic.com), you can then compress them with (compressor.io).

3. A bevvy of other tools and tricks can be found at 
(www.sitepoint.com/terrific-time-saving-css-tools)

4. you can lock your .htaccess with 

5. http://www.htaccesstools.com/htpasswd-generator






#---------------------------------------htacess
# Add Caching.
<FilesMatch ".(ico|jpg|jpeg|png|gif|js|css|swf)$">
    Header set Cache-Control "max-age=15552000"
</FilesMatch>

# Compress text, html, javascript, css, xml:
AddOutputFilterByType DEFLATE text/plain
AddOutputFilterByType DEFLATE text/html
AddOutputFilterByType DEFLATE text/xml
AddOutputFilterByType DEFLATE text/css
AddOutputFilterByType DEFLATE application/xml
AddOutputFilterByType DEFLATE application/xhtml+xml
AddOutputFilterByType DEFLATE application/rss+xml
AddOutputFilterByType DEFLATE application/javascript
AddOutputFilterByType DEFLATE application/x-javascript
AddDefaultCharset utf-8
#----------------------------------------------

