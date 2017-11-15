---
layout: post
title:  "How to map Equirectangular projection to Rectilinear projection"
date:   2017-06-12 03:05:00
author: Nitish S. Mutha
categories: Equirectangular 360degree
tags:	360degreevideos equirectangular gnomonic
cover:  "/assets/posts/bgs/bg13.jpg"
comments: true
---

## What is Equirectangular Projection?  

The projection obtained by a sphere mesh un-wraped on a flat rectangular plane surface
is known as equirectangular projection of the sphere (Weisstein [9]). It is the
direct mapping of the sphere latitude and longitude on the horizontal and vertical
coordinate system respectively. It is also called as “non-projection” or “rectangular
projection” as no scaling or transformation are applied. The resulting frame
obtained by equirectangular projection appears to be distorted. The objects at the
center are spatially compressed and towards the top and bottom are stretched as
seen in the figure below Top and bottom regions represents zenith and nadir respectively.
Equirectangular frame is of the ratio 2:1. It covers 360° horizontally and
180° vertically. The standard resolution is of the dimension 4096x2048 for UHD
resolution.  

<a href="/assets/posts/post002/0003.jpg" data-lightbox="falcon9-large" data-title="equirectangular image">
  <img src="/assets/posts/post002/0003.jpg" title="equirectangular image">
</a>  

## What is Rectilinear (Gnomonic) Projection?  

Rectilinear projection displays the image just like an what an human percieves the world as (undistorted). It has a restricted fiew of view, approximately 114°. Straight lines stay straight, hence making it undistorted.  

<a href="/assets/posts/post002/3.jpg" data-lightbox="falcon9-large" data-title="gnomonic image">
  <img src="/assets/posts/post002/3.jpg" title="gnomonic image">
</a>  

## How to obtain Gnomonic Projection?

The Gnomonic projection is a map projection which can be achieved by projecting
the ray of light from center of the sphere through the surface of the sphere at point
P1, which touches on a plane at point P. where the plane is tangent to the sphere
at point S as shown in the figure below. This mapping of point from P1 to P on the
surface is called Gnomonic map projection.  

At the tangent point there is zero distortion, but it increase as we go away from
it. It projects great circles on straight lines. It can project a hemisphere of the sphere
on the plane.  

The Gnomonic projections are used for extracting a NFoV from an equirectangular
image. Since an equirectangular image is an unwrapped version of the sphere,
the definition and mathematics of Gnomonic projection states the same.

<a href="/assets/posts/post002/gnomo.png" data-lightbox="falcon9-large" data-title="gnomonic image trick">
  <img src="/assets/posts/post002/gnomo.png" title="gnomonic image trick">
</a>  
  
<br/>

#### Graphical illustration of the mapping equirectangular/spherical image on to rectilinear image:

<a href="/assets/posts/post002/equirectangular4.png" data-lightbox="falcon9-large" data-title="Equirectangular to rectilinear">
  <img src="/assets/posts/post002/equirectangular4.png" title="Equirectangular to rectilinear">
</a>  

## Mathematics for plane transformation equations  

Let us consider the point S in the Figure above to have the central latitude and central
longitude of (lambda_0;phi_1) = (0; 0) which is on the equator and also the center of the plane.  

The transformation equations of the plane coordinates are given by,  
 <a href="/assets/posts/post002/eq1.JPG" data-lightbox="falcon9-large" data-title="equation">
  <img src="/assets/posts/post002/eq1.JPG" title="equation">
</a>  


where c is angular distance of point (x;y) from the center of the projection given as,  
<a href="/assets/posts/post002/eq2.JPG" data-lightbox="falcon9-large" data-title="equation">
  <img src="/assets/posts/post002/eq2.JPG" title="equation">
</a>  


While the inverse equations to map the point (x;y) in plane to the sphere are,  
<a href="/assets/posts/post002/eq3.JPG" data-lightbox="falcon9-large" data-title="equation">
  <img src="/assets/posts/post002/eq3.JPG" title="equation">
</a>  


## Code for the projection mapping

The complete code for mapping eqirectangular to gnomonic/rectilinear projection can be found at [https://github.com/NitishMutha/equirectangular-toolbox](https://github.com/NitishMutha/equirectangular-toolbox).  

#### Features of the toolbox
- A tool to extract a normal field of view of any given center point from any given equirectangular image/frame.  
- Highly optimized implementation to compute every pixel projection mapping at once, with bilinear interpolation for smoother image.


## Code Requirements  
* Python 3.5  
* Numpy  






{% if page.comments %}
<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/

var disqus_config = function () {
this.page.url = "{{site.url}}{{page.url}}";  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = "{{page.id}}"; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};

(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://nitishmuthagithub.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
                                           
{% endif %}