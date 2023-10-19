
# IMAGE RECOGNITION WITH IBM CLOUD VISUAL RECOGNITION


Introduction:

Here we are going to see about how the image is recognize and generate the description (codes) of the given image(photo) with the help of IBM Cloud Watson visual recognition and its tools.

Description:

 1.Setting Up The Service On IBM's Website
   We're going to set up the Visual Recognition service on IBM's website. Next, go to the Visual Recognition page and click the "Get Started Free" button 

 2.Playing With The Visual Recognition Tool
You should see the following page if you launched the Visual Recognition Tool.Click the API key button and enter your API Key.


You should see the following if your API key works.
Congrats, your Visual Recognition service is set up on Watson. Sort of. Play with the
webpage, by downloading pictures and loading them into the widgets so that you can
see how the classification works
for exampleIf you drag the pictures into the Visual Recognition service, you'll see something like
the following
As you can see, there are currently three Visual Recognition tools, a General
classifier, a Food classifier, and a Face classifier. Feel free to play with the tool a bit
more, but...we need to actually write some code now.

HERE FOR EXAMPLE:

We take the sample image and test it. Named it as pizza_2Here our base Watson node project is set up. Now we need to actually write some
test code to run this service. We COULD make API calls to the Visual Recognition
endpoint using basic HTTP API requests, but we're going to use Watson's library.
You can see the API reference for making the API calls.

In our "index.js", add the following code:
Source code added

// Copyright www.srcmake.com 2018.

// Require our libraries and our config file.
var watson = require('watson-developer-cloud');
var fs = require('fs');
var config = require('./config');

// Start the visualizer service by authenticating with our API key.
var visual_recognition = watson.visual_recognition(
{
api_key: config.apikey,
version: 'v3',
version_date: '2016-05-20'
});

// Only return classes that are 49% or above likely.
let parameters =
{

// classifier_ids: ["dogs_666724530"],
threshold: 0.49
};

// Our test image.
var params =
{
images_file: fs.createReadStream('./pizza_2.jpg'),
parameters: parameters
};

// Call the classifier.
visual_recognition.classify(params, function(error, response)
{
    
// If there's no error, then Watson's response is...
if (!error)
{
var stringresponse = JSON.stringify(response, null, 2);
console.log(stringresponse);
}
else
{
console.log("Error: " + error);}
});

Run the above code will following command:-
node index.js

Summary:
From this we conclude that image recognition technology helps us to transform the way of processing, analyzing digital images and videos, making it possible to identify objects accurately and effectively.

