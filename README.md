The goal of this practice project is to create a fairly simple online study using javascript. 
The online studies we use typically consist of 4 parts: 
informed consent, instructions, trials, debrief/feedback. 
Take a look at some of the studies on [PersonProject](https://personproject-staging.herokuapp.com/) 
and [MySocialBrain](https://mysocialbrain.org/) to see examples of what our studies look like.

You will make a study where participants complete the 
[Emotion Regulation Questionnaire (ERQ)](https://spl.stanford.edu/sites/default/files/english_0.pdf), 
created by [Gross & John (2003)](https://s3.amazonaws.com/academia.edu.documents/30501352/2003_gross-john_jpsp.pdf?AWSAccessKeyId=AKIAIWOWYYGZ2Y53UL3A&Expires=1529094329&Signature=BLyosIv8XeJgtEgmFKNmV%2BaSAhc%3D&response-content-disposition=inline%3B%20filename%3DIndividual_differences_in_two_emotion_re.pdf). 
This survey assesses how people use two different 
emotion regulation strategies: cognitive reappraisal and expressive suppression. 
See the linked paper to learn more about this survey.

To make the ERQ into an online survey, you’ll use html, css, javascript, and jquery. 
You can use Bootstrap if you want, but you’re also welcome to create your own CSS. 
You’ll also need a text editor or IDE to work in. 
I use [WebStorm](https://www.jetbrains.com/webstorm/) (they offer their full suite of tools free of charge for students), 
but [Atom](https://atom.io/) (open source), [Sublime](https://www.sublimetext.com/), 
and [Visual Studio](https://code.visualstudio.com/) are also popular choices. 
You can choose whichever text editor you prefer.

To get started, you’ll need [Node.js](https://nodejs.org/en/) (download the LTS version). 
Node lets you run javascript code on your computer without a browser, 
and is typically used to run server-side code. For our purposes, however, 
we are more interested in its package ecosystem: npm. 
If you’re familiar with python, npm is a little like pip. 
With npm, we can easily install different packages we might need, like jquery, 
and keep track of them within each project.

Once you have node installed and this directory downloaded on your computer,
you can navigate to this directory and type `npm install` to install the packages
currently associated with this project. If you want to download another package
from npm, you can do this by running `npm install --save <package-name>`. This will
download the package into `node_modules`, and add it's information to the `package.json`
file. Whenever you use a package in you html, you can just import it from the 
`node_modules` directory. This keeps your code nice and portable. Another useful
application of npm, is the ability to add scripts. For this project, we'll keep it simple.
You can run `npm start` to serve your project on a local webserver (localhost) to
see your progress (and errors, when they occur) live in your browser.

Now, you should be all set up to start making the study. 
Let’s start with the hardest part: the actual questions. 
First, think about what the final web page will look like. 
It’ll have the 10 ERQ items, each consisting of the item itself, followed by a
7-point likert scale with 3 labels: at the extremes and in the middle.
Open up the erq.js file in the js directory. In this file, you will write a function
that renders the ERQ items by placing them inside the div with id `root`
in index.html. You can build up the study one piece at a time:

1. Use jQuery to inject a div element containing a placeholder for an ERQ question into the root div
2. Expand this injected div to include a container element, a question text element, and a likert scale element
3. Make the likert scale. For the first version, it's fine if you want to just use
radio buttons or a dropdown instead of a horizontal likert. You can come back after
you finish making the whole study to make the scale horizontal.
4. Make a function to keep track of which value is selected for which question.
5. Make a json file with all the ERQ items. Format: 
```
{
"erq_1": "When I want to feel more positive emotion (such as joy or amusement), I change what I’m thinking about.",
"erq_2": "I keep my emotions to myself."
}
```
5. Read in the json file and loop through each item, appending a question with its
own likert scale for each item.
6. Make sure you are keeping track of the selected values for each question in a
javascript object.
7. Add a continue button.
8. Add validation: either disable the continue button until all questions are answered
or (better) highlight unanswered items and ask for confirmation if the user clicks
continue before all questions are answered.
9. Test the page a bunch of times and `console.log()` the data variable to make sure
the data is stored correctly and everything works as expected.
10. Awesome! The hardest part is done.

After you have the ERQ scale itself working, you can add the consent, instructions,
and debrief pages. You can either make these separate html pages that you `window.location.replace()`
to get to, or (better) you can inject them into the index.html root element, just
like the task itself. Look at the consent forms on the person project website to
see what the consent form should contain. The consent page should have validation, such that a participant cannot
continue without checking a box that says they provide informed consent.
The instruction page should just have the instructions provided in the ERQ 
scale document, nicely formatted, with a 'start' button.  The debrief
page, for now, can just say: "Thanks for completing this experiment!"
 
Once you have finished all the parts, make sure you can succesfully go from one to
the other and all pages behave as expected. Also make sure the pages look nice and
the controls are clear and user friendly. When you're satisfied, you're done with this project!
