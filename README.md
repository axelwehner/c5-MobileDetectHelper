# c5-MobileDetectHelper

This Helper helps you to identify mobile devices in your concrete5 templates. It is completly based on the PHP class "[PHP Mobile Detect](http://mobiledetect.net/)" by Serban Ghita and Victor Stanciu. I just added a few lines of code, so that you can easily load it in your concrete5 templates.

## Installation

[Download](https://github.com/axelwehner/c5-MobileDetectHelper/zipball/master) or clone a copy of the c5-MobileDetectHelper, extract it and put the `mobile_detect.php` file in your site's `helpers` directory. That's it.

## Load the MobileDetectHelper in your concrete5 template

Open your `/themes/*/elements/header.php` and add the following code:

`
<?php
$md = Loader::helper('mobile_detect');
?>
`

## Usage Examples

### Add a CSS class (computer, mobile or tablet) to the ´body´ element 

Open your `/themes/*/elements/header.php` and add the following code below the line ´defined('C5_EXECUTE') or die("Access Denied.")´:

´
$md = Loader::helper('mobile_detect');
$bodyClass = 'computer';

if ($md->isMobile()) {
	$bodyClass = 'mobile';
} elseif ($md->isTablet()) {
	$bodyClass = 'tablet';
}
´

Then replace your ´<body>´ element with ´<body class="<?php echo $bodyClass; ?>">´ 



