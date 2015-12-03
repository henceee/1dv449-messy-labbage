# 1dv449-messy-labbage

#Messy_Labbage Rapport

##Preformance and Optimization
The key to faster sites and web applications is through Front End Optimization. In understanding what this entails, one must first gain an understanding of where the front end and back end are in a web service, or any technological system. For a web service, the front end is where the browser downloads and presents content to the user and the back-end is on the server-side of the service provider where the requests from the user are handled according to the definition provided by Technopedia [1].
As much of the response time of a user request lies on the front-end, somewhere between 80-91%, according to estimates from Yahoo Developer Network[2] and Souders [3] respectively, one should reflect upon how the response time can be reduced. 

###Javascript and Stylesheets
To minimize the number of HTTP request without affecting the content of the page, one can combine multiple scripts into a single script and combine multiple style sheets into one, as well as using so called sprites to minimize the number of background images for the CSS [4].

In its current state, the site contains 5 external JavaScript files and 4 external stylesheets, which results in just as many requests – one for each resource. The site also contains one JavaScript script, and one CSS style inlined in the HTML document. In order to increase load-time, one should always make CSS and JavaScript external, rather than entwined in the HTML document, as these external files are cached by the browser [5].

When the browser parses HTML, the Document Object Model (DOM) is created parallel to the CSSOM, which is constructed from the rules specified in the stylesheet. Together they comprise the render tree, which enables the browser to render content to the user. 
In constructing the DOM and CSSOM objects, the DOM must await the execution of JavaScript, which is reliant upon the CSSOM object. This intertwined relationship can create load-time issues, especially if the stylesheet(s) are not included in the top of the page, and the script file(s) are not included in the bottom[6].

Seemingly complex browser architecture aside, what is important is that scripts and stylesheets are loaded externally, by putting them in a text file, and including the CSS in the header and the JavaScript at the very bottom of the body tag. It is therefore problematic that 4 scripts are currently found in the head of the page, mixed in with the stylesheets.
On a brighter note, CSS expressions are not used, in accordance to Souders’ 7th rule. CSS expressions are ill advised, since these expressions are based on the execution of JavaScript code embedded within the stylesheet, and are evaluated quite frequently, and reduce the load-time [7].

However, only 3 out of 5 scripts used in the application are minified. Souders recommends that JavaScript files are compressed to reduce the size of the file, by minification, which means stripping unnecessary characters such as tabs, new lines, white space and so on. By doing this, the size of the file can be reduced with around 20% [8]. 
Although it might seem like a lot of things to think about, the solution is quite easy. Simply get rid of the inline CSS and put all the CSS in a combined stylesheet, and link it in the pages header. Accordingly, the inline script should be removed as well, and put with the rest of the scripts in a combined script file. The script file should then be minimized, in order to reduce the size of the file. 

###Compression with GZIP
While on the topic of reducing file size, it is also recommended by Souders to GZIP components. So what is GZIP, you might ask? GZIP was developed by the GNU project, and standardized by RFC 1952. It is probably the most widespread compression format out there. For more information, visit the Gzip homepage [9]. GZIP further reduces the file size, thereby reducing the amount of data to be transferred over the network. It is recommended that text files are compressed, such as the HTML document, scripts, stylesheets, XML and JSON files.  By using the GZIP data size can be reduced with around 70 % [10]. 


###Decreasing Response time with CDN
As of now, the application is not extensive, nor will it be burdened with extensive traffic, as it is intended only for internal use, within the company. However, to reduce the load time further one can also use a Content Delivery System (CDN), which means a collection of servers at different location that enable a more efficient delivery of content, based on proximity and response time. Yahoo recomend CDN services provied by companies such as Akamai Technologies, EdgeCast or level3 for cost efficiency[11]. As of now, on its current state, the cost would probably be to great, and bring very little value. The knowlage of how to optimize a site for improved response time when dealing with greater scale, can still be most valuble though.



###References

 [1] “Front-End Optimization (FEO)”, Techopedia, 2015 [Online] Available: [Technopedia] (https://www.techopedia.com/definition/1515/front-end-optimization-feo [Downloaded: 3 December, 2015].)
 
[2] “Best Practices for Speeding Up Your Web Site" Yahoo Developer Network [Online] Available: [Yahoo Developer Network] (https://developer.yahoo.com/performance/rules.html#num_http=)  [Downloaded: 3 December, 2015]

[3] S. Souders, “High Preformance Websites”,Communications of the AMC, . vol,2008, Vol. 51 Issue 12, p.36,December 2008. [Online] Available: [OneSearch] (http://eds.b.ebscohost.com.proxy.lnu.se/eds/detail/detail?vid=4&sid=57778c72-0d7c-4867-9509-d6effdd1f1bb%40sessionmgr114&hid=108&bdata=Jmxhbmc9c3Ymc2l0ZT1lZHMtbGl2ZSZzY29wZT1zaXRl#AN=35609277&db=buh) [Downloaded: 3 december, 2015].

[4] S. Souders, “High Preformance Websites”,Communications of the AMC, . vol,2008, Vol. 51 Issue 12, p.37-38,December 2008. [Online] Available: [OneSearch] (http://eds.b.ebscohost.com.proxy.lnu.se/eds/detail/detail?vid=4&sid=57778c72-0d7c-4867-9509-d6effdd1f1bb%40sessionmgr114&hid=108&bdata=Jmxhbmc9c3Ymc2l0ZT1lZHMtbGl2ZSZzY29wZT1zaXRl#AN=35609277&db=buh) [Downloaded: 3 december, 2015].

[5] “Best Practices for Speeding Up Your Web Site" Yahoo Developer Network [Online] Available: [Yahoo Developer Network](https://developer.yahoo.com/performance/rules.html#num_http=)  [Downloaded: 3 December, 2015]

[6] I. Grigorik, “High Preformance Browser Networking”, O'Reilly Media, 2013. [E-Bok] Available: [Chimera] (http://chimera.labs.oreilly.com/books/1230000000545/index.html) [Downloaded: 3 december, 2015].

[7] [4] S. Souders, “High Preformance Websites”,Communications of the AMC, . vol,2008, Vol. 51 Issue 12, p.39,December 2008. [Online] Available: [OneSearch] (http://eds.b.ebscohost.com.proxy.lnu.se/eds/detail/detail?vid=4&sid=57778c72-0d7c-4867-9509-d6effdd1f1bb%40sessionmgr114&hid=108&bdata=Jmxhbmc9c3Ymc2l0ZT1lZHMtbGl2ZSZzY29wZT1zaXRl#AN=35609277&db=buh) [Downloaded: 3 december, 2015].

[8] [4] S. Souders, “High Preformance Websites”,Communications of the AMC, . vol,2008, Vol. 51 Issue 12, p.39,December 2008. [Online] Available: [OneSearch] (http://eds.b.ebscohost.com.proxy.lnu.se/eds/detail/detail?vid=4&sid=57778c72-0d7c-4867-9509-d6effdd1f1bb%40sessionmgr114&hid=108&bdata=Jmxhbmc9c3Ymc2l0ZT1lZHMtbGl2ZSZzY29wZT1zaXRl#AN=35609277&db=buh) [Downloaded: 3 december, 2015].

[9] “The GZip HomePage” 2003.[Online] Available:  [GZIP.org](http://www.gzip.org/) [Downloaded: 3 december, 2015].

[10] [4] S. Souders, “High Preformance Websites”,Communications of the AMC, . vol,2008, Vol. 51 Issue 12, p.39,December 2008. [Online] Available: [OneSearch] (http://eds.b.ebscohost.com.proxy.lnu.se/eds/detail/detail?vid=4&sid=57778c72-0d7c-4867-9509-d6effdd1f1bb%40sessionmgr114&hid=108&bdata=Jmxhbmc9c3Ymc2l0ZT1lZHMtbGl2ZSZzY29wZT1zaXRl#AN=35609277&db=buh) [Downloaded: 3 december, 2015].

[11] “Best Practices for Speeding Up Your Web Site" Yahoo Developer Network [Online] Available: [Yahoo Developer Network](https://developer.yahoo.com/performance/rules.html#num_http=)  [Downloaded: 3 December, 2015]
