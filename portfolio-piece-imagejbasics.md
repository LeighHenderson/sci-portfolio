<!DOCTYPE html>
<html lang="en">

<head>

  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
  <meta name="description" content="A portfolio of science writing samples">
  <meta name="author" content="Leigh Henderson">

  <title>Science Writing Portfolio</title>

  <!-- Bootstrap core CSS -->
  <link href="vendor/bootstrap/css/bootstrap.min.css" rel="stylesheet">

  <!-- Custom fonts for this template -->
  <link href="vendor/fontawesome-free/css/all.min.css" rel="stylesheet" type="text/css">
  <link href="https://fonts.googleapis.com/css?family=Montserrat:400,700" rel="stylesheet" type="text/css">
  <link href='https://fonts.googleapis.com/css?family=Kaushan+Script' rel='stylesheet' type='text/css'>
  <link href='https://fonts.googleapis.com/css?family=Droid+Serif:400,700,400italic,700italic' rel='stylesheet' type='text/css'>
  <link href='https://fonts.googleapis.com/css?family=Roboto+Slab:400,100,300,700' rel='stylesheet' type='text/css'>

  <!-- Custom styles for this template -->
  <link href="css/agency.min.css" rel="stylesheet">

</head>

<body id="page-top">

  <!-- Navigation -->
  <nav class="navbar navbar-expand-lg navbar-dark fixed-top" id="mainNav">
    <div class="container">
      <a class="navbar-brand js-scroll-trigger" href="#page-top">Leigh Henderson's Science Writing</a>
      <button class="navbar-toggler navbar-toggler-right" type="button" data-toggle="collapse" data-target="#navbarResponsive" aria-controls="navbarResponsive" aria-expanded="false" aria-label="Toggle navigation">
        Menu
        <i class="fas fa-bars"></i>
      </button>
      <div class="collapse navbar-collapse" id="navbarResponsive">
        <ul class="navbar-nav text-uppercase ml-auto">
          <li class="nav-item">
            <a class="nav-link js-scroll-trigger" href="#services">Services</a>
          </li>
          <li class="nav-item">
            <a class="nav-link js-scroll-trigger" href="#portfolio">Portfolio</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <!-- Header -->
  <header class="masthead">
    <div class="container">
      <div class="intro-text">
        <div class="intro-lead-in">ImageJ Basics</div>
        <div class="intro-heading text-uppercase">It's Nice To Meet You</div>
        <a class="btn btn-primary btn-xl text-uppercase js-scroll-trigger" href="#services">Tell Me More</a>
      </div>
    </div>
  </header>

<p>
Have you ever wanted to quantify something from an image? For example:

- The number of stars in a photo of the nighttime sky
- The number of cells under a microscope, and the area of each
- The distance between two points on a map

ImageJ is image-processing software specially made for scientific measurements. It is free to download at [imagej.nih.gov] and has a large online [wiki].

ImageJ excells in *automating* image quantification. For example, counting hundreds of stars in 10+ images of the nightime sky. Someone could do this manually, but the star count can be less biased and more accurate (not to mention less tedious!) when automated. 

Experienced ImageJ users can skip ahead to [automation with macros](#automation-with-macros), [extending macros to automate quantification of all images in a folder](#extending-macros), or [to my example macros].
</p>

<h1>Easy example</h1>

<p>Let's count the stars in an image of the nighttime sky:</p>

<ol>
<li>Save the image below to your device (see image credit below). File > Open.

<img src="/assets/ImageJ_StarsToCount.jpg" alt="Practice image for counting stars." style="width:400px">
</li>

<li>Edit > Options > Point tool. Use options: add to overlay and label points.

<img src="/assets/Screencap_ImageJ_StarCounting_PointToolOptions.jpg" alt="Screencap. Point tool options in ImageJ." style="width:400px">
</li>

<li>From the toolbar, select the Point tool. Click on each star to be counted. If you make a mistake, click on the unwanted point and press *delete*.

<img src="/assets/Screencap_ImageJ_StarCounting_PointToolCount.jpg" alt="Screencap. Stars counted with the point tool." style="width:400px">
</li>
</ol>

<h1>Removing bias in quantification through thresholding</h1>

<p>In the star counting example, someone might count more than 9 stars. Or fewer. The person counting brings a certain bias as to what a star should look like. To remove bias, let's define exactly what a star looks like. That way, different people analyzing this image will arrive at the same star count. Here's how:</p>

<ol>
<li>File > Open. Open the original image.</li>

<li>Image > Type > 8 bit. Reduce the color profile to 8-bit.</li>

<li>Image > Adjust > Threshold > Apply. Use Threshold options: Intermodes, Red, and Dark background. Intermodes is one of many mathematical models for automated thresholding; it is the best option for this particular image. 

<img src="/assets/Screencap_ImageJ_StarCounting_Threshold.jpg" alt="Screencap. Stars thresholded in ImageJ." style="width:400px"></li>

<li>Analyze > Analyze particles > OK. Use Analyze particles options: Show outlines, Clear results, Summarize, and Exclude on edges.

<img src="/assets/Screencap_ImageJ_StarCounting_AnalyzeParticles.jpg" alt="Screencap. Use analyze particles to count stars in a thresholded image in ImageJ." style="width:400px">
</li>
</ol>

<p>Nine stars are counted.</p>

<img src="/assets/Screencap_ImageJ_StarCounting_CountAfterThreshold.jpg" alt="Screencap. Nine stars have been counted after thresholding." style="width:400px">

<h1>Automated quantification with macros</h1>
<a id="automation-with-macros"></a>

<p>With thresholding, counting 100 stars is as easy as counding 9 stars. However, threshold counting stars in dozens of images would be tedious because of the need to click through the menus. ImageJ macros can automate the click through. Let's make a macro to count the stars:</p>

<ol>
<li>File > Open. Open the original image. </li>

<li>Open the Macro recorder. Edit the name of the macro, ex. "CountStars.ijm" (Note- .ijm is the ImageJ Macro extension).</li>

<li>Click through all the steps for threshold counting. The steps will be recorded.
    <ol>
    <li>Image > Type > 8 bit</li>
    <li>Image > Adjust > Threshold > Apply. Use Threshold options: Intermodes, Red, and Dark background.</li>
    <li>Analyze > Analyze particles > OK. Use Analyze particles options: Show outlines, Clear results, Summarize, and Exclude on edges.

<img src="/assets/Screencap_ImageJ_StarCounting_MacroRecorder.jpg" alt="Screencap. The Macro Recorder shows each of the menu options that have been clicked." style="width:400px">
    </li>
    </ol>
</li>

<li>In the recoder window, click *create*. A new .ijm window will open. Save the macro to the ImageJ > macros folder.</li>

<li>Close all windows.</li>

<li>File > Open. Open the original image.</li>

<li>Plugins > Macros > Open. Open CountStars.ijm.</li>

<li>Click on the .ijm window. New menu options will appear. Macros > Run macro. Nine stars are counted, just as if the menus were clicked through by hand.</li>

<li>Test the macro on another star image. 
    <ol>
    <li>File > Open. Open the second image (use the one below).

    <img src="/assets/ImageJ_StarsToCount2.jpg" alt="Second practice image for counting stars." style="width:400px">
    </li>

    <li>Plugins > Macros > Open. Open CountStars.ijm.</li>
    <li>Click on the .ijm window. Macros > Run macro. Thirty two stars are counted.

<img src="/assets/Screencap_ImageJ_StarCounting_CountAfterThreshold2.jpg" alt="Screencap. Thirty two stars are counted in the second image." style="width:400px">
    </li>
    </ol>
</li>
</ol>

<h1>Extending macros to automate quantification of all images in a folder</h1>
<a id="extending-macros"></a>

<p>If you have hundreds of images to process, the clicks required to open and close each image become tedious. Adding a few lines to a macro can automate opening each image, running the macro, saving the results, and closing each image. Here's how:</p>

<ol>
<li>Download the third example star image, below. Save all of three example images (StarsToCount 1, 2, and 3) into one folder. Put nothing else in this folder. 

<img src="/assets/ImageJ_StarsToCount3.jpg" alt="Third practice image for counting stars." style="width:400px">
</li>

<li>In ImageJ, Plugins > Macros > Edit. Open CountStars.ijm.</li>

<li>File > Save As. Save the macro as "CountStarsInFolder.ijm"</li>

<li>Add the following text to the macro (or copy-past from a [PDF]({{ site.url }}/assets/ImageJ-MACRO-CountStarsInFolder.pdf) of the finished macro):
    <ol>
    <li>Before the rest of the text in the macro window, add instructions to choose an input folder and an output folder (folders are called "directories" in ImageJ):

            dirInput = getDirectory("Choose  Directory "); 
            dirOutput = getDirectory("Choose  Directory ");
    </li>

    <li>Add instructions to process each image, or "file," in the folder:
        <code> <!--To display <,>, or & as text use &lt;, &gt;, or &amp--> 
        list = getFileList(dirInput); 

        setBatchMode(true); 
        for (i=0;i&lt;list.length;i++) { 
            open(dirInput+ list[i]);
        }
        </code>
    </li>

    <li>At the end of the macro, add instructions to save the thresholded image and close the open windows.

            saveAs("Jpeg", dirOutput + File.nameWithoutExtension + "_Threshold");
            close();
            }
    </li>
    </ol>
</li>

<li>File > Save.</li>

<li>Macros > Run macro.</li>

<li>A dialogue box will open. Select the folder in which your images are stored.</li>

<li>A second dialogue box will open. Select a different folder in which thresholded images will be placed. Do not make a new folder inside the folder from step 7.</li>

<li>The macro will run. Star counts will appear in the Summary window (9, 32, and 19 stars in images 1, 2, and 3, respectively). Thresholded images will appear in the folder selected. </li>

</ol>

<h1>Editing macros</h1>

<p>Edit the contents of "CountStarsInFolder.ijm" to improve the accuracy of counting, or completely rework the contents to perform your own image quantification tasks. 

- On the accuracy front, you may have noticed that there is a mistake made on "StarsToCount2.jpg": two stars appear so close together that they are counted as one. This type of error can be dealt with by adding a watershed step (LINK TO PAGE). 

- On your own star images, you may notice that the stars aren't counted properly. You'll find the problem by examining the saved thresholded images: thresholding is failing. Thresholding takes the overall brightness and contrast of an image into account. Therefore, pictures taken with differet settings or at different times/locations often require different thresholds. Consider chaning the threshold to the one that works best for your images. Note that using different thresholds on images in a set can alter count results; controlling for camera settings and time/location in batches of images is the best way to avoid threshold bias.

- Test the star counting macro on images of other objects to be counted. For example, try counting cell nuclei that have been stained with DAPI. As discussed above, the threshold may need to be changed.

- Set a scale for the image and then report the area of each star. See my ImageJ protocols for an example.

The sky's the limit on macros [pun intended]. To infinity and beyond!

See my [ImageJ protocols for quantifying lipid droplets] for inspriation. </p>

<h2>Starry sky image credit</h2>
<p>Thanks to Davide De Martin for the [starry sky image] from the ESO/Digitized Sky Survey 2. All smaller sky images were cropped from the original.</p>


<!--
[//]: #(These are references used above, to be processed by Jekyll)
[imagej.nih.gov]:<https://imagej.nih.gov/ij/download.html>
[wiki]:<http://imagejdocu.tudor.lu/>
[ImageJ protocols for quantifying lipid droplets]:<{{ site.url }}/PROTOCOL-quantifying-images-with-ImageJ/>
[starry sky image]:<http://www.eso.org/public/images/eso1337b/>
-->

<!-- Bootstrap core JavaScript -->
  <script src="vendor/jquery/jquery.min.js"></script>
  <script src="vendor/bootstrap/js/bootstrap.bundle.min.js"></script>

  <!-- Plugin JavaScript -->
  <script src="vendor/jquery-easing/jquery.easing.min.js"></script>

  <!-- Custom scripts for this template -->
  <script src="js/agency.min.js"></script>

</body>

</html>
