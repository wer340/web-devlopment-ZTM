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
