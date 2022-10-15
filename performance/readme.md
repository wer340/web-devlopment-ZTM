# performance 
make the website faster\

### introduction
All big companies prioritize fast user experience because they know that people of today are used to not waiting around \
 there are infinite ways to make your code more performant  one second delay  six billon dollar cost \
 assume your visitor expect your side to load within two second and half of them will leave if it take more than three second now  each second of delay decreases customer satisfaction and possibly money \
 just to recap   there are **three places** where work needs to happen when displaying website\
1️⃣ make GET request to website like www.superfresh.com\
so theres some work that goes there to transfer that request to the back end or server and \
2️⃣then server does a bit of work there and maybe returned the file finds it and returns it or maybe needs to talk to a database and retrieves some data there  we then have to **send that information again through the wires** and then finally\
3️⃣in our browser  do some work so that we can display the page to the user

### 5network
internet    submarine cable land wire satellite signal tower that allows us to connect to all the computer\
 every time open browser and load site we sent to request\
  #### shrunk the file 
Minimize text `css,js,html` , minimize image `svg,jpg,gif,png`\
[uglify js](https://skalman.github.io/UglifyJS-online/)   removing space  removing byte \
the primary way for reduce size of image  change file format ,pick the file format that is the best for the job\
**jpg** use complex color and  you cant do that  to have a transparent background you must use something like png or gif\
**gif** use limit the number of total colors that you can use in a gif and reducing the color count leads to huge falls saving thats really good for small animation\
**png** usually limit the number of colors you can use and they tend to be a lot smaller in size than jpg the cool thing is that you can add transparency to them which you cannot do in jpg \
**svg** completely different category   they are actually something called vector graphics \
these are file that designers usually work with on adobe illustrator or something like sketch \
### what you can do with svg is that you can expand an svg to several times its original size and it will be just sharp and clear as the original was 
incredibly small what they do\
new image format that have come out recently   like jpg2000 , jpg Exer\
## Browser support for these new types? its still not completely there yet 
### [Image file formats: when to use each file type](https://99designs.com/blog/tips/image-file-types/)
### [See How Images Affect Your Page Speed](https://pageweight.imgix.com/)
### [GIF, PNG, JPG or SVG. Which One To Use?](https://www.sitepoint.com/gif-png-jpg-which-one-to-use/)

## optimize image
want transparency use a png/
want animation use a gif/
want colorful image use a jpg/
want simple icon logos illustration use a svg/
reduce png with [TinyPNG](https://tinypng.com/)\
reduce jpg with [jpeg-optimizer](https://jpeg-optimizer.com/)\
try to choose simple illustrations over highly detailed photographs \
always lower jpeg image quality (30-60%)\
**resize image based on size it will be displayed** \
display different sized images for different backgrounds\
use CDNs like [imigx](https://imgix.com/)\
**remove image metadata use [verexif](https://www.verexif.com/en/)**

## css media query  display different sized images 
media query [cheat-sheet](https://gist.github.com/bartholomej/8415655) and [media query resource](https://css-tricks.com/snippets/css/media-queries-for-standard-devices/)
```css
body{
background:yellow;
}
@media screen and (min-width:900px){
  body{
    background:url('./large-background.jpg' ) no-repeat center center fixed;
    background-size:cover;
  }}


  @media screen and (max-width:500px){
  body{
    background:url('./large-background.jpg' ) no-repeat center center fixed;
    background-size: ;
  }}
@media print and (min-width:900px){}

```
media query is simple  using success you can actually deliver a different background image for the various size that your site provides\
this mean that you must save your images in different file size for them to work \
 
## delivery optimization
so far talked about   i shrunk the file reducing the size of those downloads by compressing images minify css and js
but there s a more fundamental approach in addition to just reducing download size \
lets also consider reducing download frequency the traveling delivery man\
reducing the number of components that a page requires proportionally **reduce the number http  request** it has to make . it doesn't mean remove component it mean more efficient \
## less trip
this doesnt mean omitting content with less trip ideally while we are minimizing our files but also we are not sending every single file down the wire ,**only the ones that we need** \

just have less files and dont make the deliverymen work so hard now you must be asking yourself?/
can we just tell them to carry all the file at once ?\
whats the big deal?\
thanks to http protocol our  browser will only simultaneously download a set maximum number of file
from a  demand of time . and this [ranges 2-6](https://stackoverflow.com/questions/985431/max-parallel-http-connections-in-a-browser) [from two to six]depending on your browser  be carful **it also has limits on the total size it can carry**\
so again we want to minimize file and we want to limit the strips that the delivery man makes  so perhaps we can combine our access files into one , combine our javascript file into one 
  
## recap
Minimize all text  
Minimize all images  
Media query 
Minimize all files\  
attach:[minifier](https://www.minifier.org/)

### you analyze  your performance  go to inspect element and leave  **3g speed** and **disable cache load**  , then do hard loading and see how many time load website /

## simulate file to browser
when html file arrive to browser  it start creating something called **the document object model** and browser parses or read html incrementally generates this tree model of the html tags .DOM  describes the contents of page  but then just as its about to start doing that it encounters a style link to grab the css so it asks for the css file from the server and then the css file arrives and it gets back to working  and it gets back to working on the DOM creating the structure of the web site now  once the browser receives all the css it also starts generating a tree model called css on and this  css object model has the styling information attached to the tree nodes and this tree describes how the content is styled  and its working and its  working and is building this tree and then all of a  sudden it sees a javascript tag a script tag so it grabs it from the server and the javascript derives but its also going to read javascript file and this javascript file is read by the browser and executes any changes that it might want onto the DOM and the css . \
now once all thats done the browser combine the DOM and the cssOM into a render tree\
render tree has both information from a html and the styling and layout information of css by combing the DOM and the success on the browser constructs this render tree so knows exactly what to render on the page so now browser uses this render tree to figure out the layout is going to forget about all these files and then its going to figure out the layout where should i position these items in one location what width what height and wants is figure that out is going to paint all the pixels in guess what at the end of all of that \
we finally have our webpage and then download image  and loaded \
## Critical Render Path 
when a user request a page for your site the page html start streaming to the browser as soon as a browser encounter tags for an external image a script a successful , it will start downloading that file simultaneously \
 when the browser receives our html it does something called **parsing it** its breaking it down into a vocabulary it understands after understanding the document  this what it does  it starts creating the dom as we have mentioned the document object model and again as its building that as soon as it sees an external resource , it goes ahead and starts downloading all of  those and **usually the css in java script files take high priority** and other file like image take lower priority\
 how do we optimize this process?\
 the first thing you want to do is to load style that has  case file as soon as possible and scripts that is javascript files as late as possible with a few exceptions here and there\
 why?\
 well one of the main principle of excess performance is to get the excess to the browser as soon as possible \
 javascript requires the html and access parsing to finish before it can be run that s step 4 over here(image)\
 this way we give style  ample time to create the css object model (CSSOM)\
 if you put javascript in the head tag and html the problem with that positioning ,if its above the top , is that it blocks page rendering. \
 scripts historically blocked additional resources from  being downloaded more quickly  by replacing them at the bottom or by placing them at the bottom you are style content and media  could start downloading more quickly given the perception of improved performance.\
 the best way to demonstrate this is through an example \
 ```html
 <!-- HTML
#1 Load <style> in <head>
#2 Load <script> right before /body 
-->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Critical Render Path</title>
    <!-- External css -->
    <link rel="stylesheet" href="style.css">
</head>
<body>
<h1>How fast?</h1>
<button>Click me</button>
<!-- #2 Render blocking aand parser blocking JS -->
<script>alert("check")</script>
</body>
</html>
```
and open network tab  then click refresh  \
i see that my index file and style dot successful is well it looks like its loaded and because we have an alert here its blocking the rendering of the page \
the javascript is running right now and we will get to why that is in the later videos \
 but for now i want you to see that that the index and css file where both downloaded\
### if script tag up  above the stylesheet \
  ```html
 <!-- HTML
#1 Load <style> in <head>
#2 Load <script> right before /body 
-->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Critical Render Path</title>
  <!-- #2 Render blocking aand parser blocking JS -->
  <script>alert("check")</script>
    <!-- External css -->
    <link rel="stylesheet" href="style.css">
</head>
<body>
<h1>How fast?</h1>
<button>Click me</button>
</body>
</html>
```
and now  i refresh page  we see that the stylesheet is now pending if i click ok it then starts downloading it and we see over here 

## recap
**HTML**\
load style tag in the <head> \
load script right before </body>\

## second step
css is called render blocking because in order to construct the render tree and print something the screen , we are waiting for the system to complete and combine it with the DOM to create the render tree so **css is render blocking**\
so with that in mind it makes sense that we want to make them as lightweight as possible so that the user sees something as soon as possible \

## recap
**css**\
only load whatever is needed\
above the fold loading\
media attributes\
less specificity\

only needed  for style write in css\
webpage  was scrollable   maybe we had images underneath or it was a one of those one page website that i can keep scrolling down on . there is more and more information\
i technically **don't need to see that until i start scrolling**\
so the priority is to see whatever is above the fold the main page , if we are able to optimize this and just load what we need above the fold.\
 

