# c5-MobileDetectHelper

This Helper allows you to serverside detect mobile devices in your concrete5 templates. It is completly based on the PHP class "[PHP Mobile Detect](http://mobiledetect.net/)" by Serban Ghita and Victor Stanciu. I just added a few lines of code, so that you can easily load and use it in your concrete5 templates.


## Installation

[Download](https://github.com/axelwehner/c5-MobileDetectHelper/zipball/master) or clone a copy of the c5-MobileDetectHelper, extract it and put the `mobile_detect.php` file in your site's `helpers` directory. That's it.


## Load the MobileDetectHelper in your concrete5 template

Open your `/themes/*/elements/header.php` and add the following code:

    <?php
    $md = Loader::helper('mobile_detect');
    ?>


## Usage Examples


### Add a CSS class to the `<body>` element 

With a CSS class (in this example: computer, mobile or tablet) in your `<body>` element, you're able to use device secific style's for mobile visitors.
Open your `/themes/*/elements/header.php` and add the following code below the line `defined('C5_EXECUTE') or die("Access Denied.");`:

    $md = Loader::helper('mobile_detect');
    $bodyClass = 'computer';
    
    if ($md->isMobile()) {
        $bodyClass = 'mobile';
    } elseif ($md->isTablet()) {
        $bodyClass = 'tablet';
    }

Then replace your `<body>` element with `<body class="<?php echo $bodyClass; ?>">`

Now you can declare device secific style's in your CSS file. For example hide your `<div id="footer"></div>` element on smartphones:

    body.mobile div#footer {
        display: none;
    }


### Redirect to a mobile website when visiting with a mobile device

Add the following code in the very first line of your `/themes/*/elements/header.php`.
It is important that there is no output sent to the client before executing this code.

    $md = Loader::helper('mobile_detect');
    if ($md->isMobile) {
       header('Location:http://mobile.example.com');
       die();
    }