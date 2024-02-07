---
layout: single
title:  "Offline Ray Tracer"
date:   2022-01-24 00:57:03 -0500
tags: code classwork graphics cpp
carousels: [ 
    images: [
        image: /assets/images/rayTracingCarousel/monkey.png,
        image: /assets/images/rayTracingCarousel/cubeRayTracer.png,
        image: /assets/images/rayTracingCarousel/spheresWithoutPerspective.png,
        image: /assets/images/rayTracingCarousel/spheresWithBlur.png,
        image: /assets/images/rayTracingCarousel/output1.png

    ],
    images: [
        image: /assets/images/raytracingvolumes/volume_fallout.png,
        image: /assets/images/raytracingvolumes/volume_homogenous_overlap.png,
        image: /assets/images/raytracingvolumes/volume_chaos.png,
        image: /assets/images/raytracingvolumes/volume_disk.png,
        image: /assets/images/raytracingvolumes/volume_detailed_noise_octaves.png,
        image: /assets/images/raytracingvolumes/scene.png
    ]
]
---
Built an offline ray tracer in C++ 17 that produced rendered, ray-traced ppm images, which supports rendering objects of different material types, as well as volume rendering.
<hr> 
### *Tools, libraries, and languages used: C++, VSCode*
<hr>

{% include carousel.html height="50" unit="%" duration="7" number="1" %}

{% include carousel.html height="50" unit="%" duration="7" number="2" %}

### Code Walkthrough

If you're interested in a walkthrough and explanation of the final project code, see the video below!

<iframe width="560" height="315" src="https://www.youtube.com/watch?v=j4tECzsy0CE" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## The Project
Throughout the semester for my Advanced Offline Rendering Techniques class, I had worked on building an offline ray tracer based on (of course) Peter Shirley's Ray Tracing guides, specifically *Ray Tracing in One Weekend* and *Ray Tracing the Next Week*. I implemented a variety of features, including:

<ul>
<li>Variety of material types, including matte, reflective, and transparent</li>
<li>Positionable camera and defocus blur</li>
<li>.obj model parser and ability to render complex meshes</li>
<li>Bounding volumes for optimization</li>
<li>Volume rendering to create cloud-like effects</li>
</ul>

### Volume Rendering (aka... clouds)

The final part of the project was to implement the volume rendering mentioned above. I looked for a few tutorials to reference, and found a great guide from <a href="https://www.scratchapixel.com/lessons/3d-basic-rendering/volume-rendering-for-developers/intro-volume-rendering.html">scratchapixel.com</a>. I also used Ken Perlin's noise function to generate the randomized spheres (references: <a href="https://solarianprogrammer.com/2012/07/18/perlin-noise-cpp-11/">solarianprogrammer.com</a> and <a href="https://www.redblobgames.com/maps/terrain-from-noise/">redblobgames.com</a>). 

*Code available upon request for academic integrity purposes.*
