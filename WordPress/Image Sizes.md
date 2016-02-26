# Image Sizes in WordPress

WordPress is great at managing your images, it even allows for you to define the cut you want a given image to be available. this is called registering an image size via the [`add_image_size`](https://developer.wordpress.org/reference/functions/add_image_size/) function. It's an amazing thing and saves a lot of bandwidth by serving smaller images, making your clients and users happy (especially if they are coming to you from a mobile device).

However, every time you register an image you increase the server load for every uploaded original. When an image is uploaded to the site, WordPress now has to resize and cut each of the specified image sizes, generating the appropriate thumbnails for you to use. Also, you will loose the advantage of browser caching, as all your images will be similar, but not the same, resulting in increased page loads and unhappy users. Those similar images may be so close in size and aspect ratio, that using just one or two of those dimensions would suffice.
There is also the issue of massive bloat, with dozens of images for each original file, making your disk space occupied with, well, useless cuts of the same image.

## Naming Image Sizes

To avoid having more thumbnails than we need, we created a naming system that allows us to see if any of the already registered sizes could be used on a new situation. The name is a string with two pieces of information. First a qualitative dimension name (like `medium` or `large`) followed by the aspect ratio.

```
[qualitative-size]_[aspect-ratio]
```

### Qualitative dimension

This must be one of the following 4:
* `small`: less than `300px`
* `medium`: more than `300px` and less than `800px`
* `large`: more than `800px` and less than `1300px`
* `huge`: more than `1300px`

**Note:** The dimension of reference is the largest for the image size. If an image size is to be `400x300px` the largest size is the with with `400px` and the qualitative dimension should be `medium`.

### Aspect

The aspect ratio relates an image's width with its height. In this case it also serves as a indicator of the images orientation (an image with a `4:3` ratio will have a bigger with than height and will be an "horizontal" image).
Because the image size slug is also used as a class by WordPress we don't specify the ratio with a colon separator. Instead, we use the word `by`. So `4:3` would actually be `4by3`.

A few guidelines on ratios:
* Try to hit a nice number to factorize like `4by3`, `16by9` and `21by9` (all video standards). Use the inverse for vertical images.
* If the image is square don't omit the ratio, use `1by1`.

### Examples

```php
/**
 * See the WordPress documention for more information on the 'add_image_size' function.
 * https://developer.wordpress.org/reference/functions/add_image_size/
 */

/**
 * Image size: 780x585px
 * Reference size: 780px (biggest dimension, the width)
 * Qualitative dimension: medium
 * Size name: 'medium_4by3'
 */
add_image_size( 'medium_4by3', $width, $height, $crop );

/**
 * Image size: 180x320px
 * Reference size: 320px (biggest dimension, the height)
 * Qualitative dimension: small
 * Size name: 'small_9by16'
 */
add_image_size( 'medium_5by13', $width, $height, $crop );
```

## General guidelines

* To reduce the number of cuts, for the reasons stated at the top of this document, try to use an existing image in the same dimension space (`small`, `medium`, `large` or `huge`) as the one you would like to have.
* If the aspect ratio your image has is not equal to any of the others, make some calculations to determine how much you would be reducing or increasing the image in the layout if you used some of the closest aspect rations already there.
* If there is no image registered in the same dimension space as the one you need, don't add it without checking if there is any aspect ratio that would bring you the same look and feel (see previous point).
