---
layout: default
---

# AnitoCrosshatch: A 3D Editor Tool for Cross Hatch Rendered 3D Environments

AnitoCrosshatch is a 3D editor tool designed to create and edit 3D environments rendered in a cross-hatch style. It provides a user-friendly interface for artists and developers to manipulate 3D models, textures, and lighting to achieve the desired aesthetic.

Our application can perform real-time rendering with the stylized shaders, and can produce a variety of different crosshatching styles with the available parameters of our crosshatching system.

## Gallery

**[Paper](https://yeunnn.github.io/AnitoCrossHatch/)** \| **[Source](https://github.com/Zerithe/CrossHatchEditor)**

<div class="gallery-container">
  <a href="#img1"><img src="./assets/img/main1.png" alt="main1" /></a>
  <a href="#img2"><img src="./assets/img/main2.png" alt="main2" /></a>
  <a href="#img3"><img src="./assets/img/main3.png" alt="main3" /></a>
  <a href="#img4"><img src="./assets/img/main4.png" alt="main4" /></a>
  <a href="#img5"><img src="./assets/img/main5.png" alt="main5" /></a>
  <a href="#img6"><img src="./assets/img/main6.png" alt="main6" /></a>
</div>

<!-- Lightbox popups -->
<div id="img1" class="lightbox">
  <a href="#">×</a>
  <img src="./assets/img/main1.png" alt="main1 full" />
</div>
<div id="img2" class="lightbox">
  <a href="#">×</a>
  <img src="./assets/img/main2.png" alt="main2 full" />
</div>
<div id="img3" class="lightbox">
  <a href="#">×</a>
  <img src="./assets/img/main3.png" alt="main3 full" />
</div>
<div id="img4" class="lightbox">
  <a href="#">×</a>
  <img src="./assets/img/main4.png" alt="main4 full" />
</div>
<div id="img5" class="lightbox">
  <a href="#">×</a>
  <img src="./assets/img/main5.png" alt="main5 full" />
</div>
<div id="img6" class="lightbox">
  <a href="#">×</a>
  <img src="./assets/img/main6.png" alt="main6 full" />
</div>

[Explore More Images](./more-gallery.md)

### Watch Our Trailer!
[![AnitoCrossHatch](https://img.youtube.com/vi/tr6x6hXhuC4/sddefault.jpg)](https://www.youtube.com/watch?v=tr6x6hXhuC4)

## Performance Benchmark

We performed qualitative testing by conducting a comparative analysis of our framework against Blender and Unity to evaluate the technical capabilities of AnitoCrosshatch relative to standard 3D engine software. Benchmarking was conducted using standard 3D scenes, with evaluation criteria focused on frames per second (FPS) and memory usage. These scenes were selected from McGuire's (2017) archive, a well-established dataset used in prior rendering studies. Scene selection was based on object count and geometric complexity.

Scenes such as “Crytek Sponza”, “Conference Room”, “Rungholt”, and “Powerplant” feature numerous objects, while “Bedroom” and “Gallery” contain intricate geometry based on real-world scanned environments.

#### **Figure 1.0** – Standard 3D Scenes Rendered in AnitoCrosshatch  
![Scenes Rendered](./assets/img/chapter5_perf_figuretechnical.png)  
*From left to right: Crytek Sponza ©2010 Frank Meinl, Crytek; Conference Room ©Anat Grnyberg and Greg Ward; Powerplant ©1999 University of North Carolina; Rungholt ©Kescha; Gallery ©2017 The Hallwyl Museum; Bedroom ©fhernand.*

#### **Figure 1.1** – Triangle Count of Each Scene  
![Triangle Count](./assets/img/chapter5_perf_trianglecount.png)  
*Geometry triangle count for the selected standard 3D scenes.*

#### **Figure 1.2** – Test Device Specifications  
![Device Specs](./assets/img/chapter5_perf_performancetest.PNG)  
*Computer specifications used for the performance tests.*

Different rendering pipelines were used for Blender and Unity to match the capabilities of our real-time rendering pipeline. Blender utilized the EEVEE engine with rendered viewport shading, while Unity used the Universal Rendering Pipeline (URP), suitable for real-time applications in both games and animations.

#### **Figure 1.3** – Rendering Pipelines for Each Engine  
![Pipelines](./assets/img/chapter5_perf_renderingpipeline.PNG)  
*Rendering pipeline setup for AnitoCrosshatch, Blender, and Unity.*

To measure performance, we captured FPS over 1,000 frames with a cap at 144 FPS due to vertical synchronization (VSync). The FPS and memory usage were measured using platform-specific methods:
- **AnitoCrosshatch:** Built-in benchmarking functionality
- **Blender:** Python script for FPS and memory
- **Unity:** C# runtime script and built-in profiler

#### **Figure 1.4** – Expected FPS Measurements  
![Expected FPS](./assets/img/chapter5_perf_expected.PNG)  
*Targeted FPS performance expectations for each engine.*

Figure 1.5 summarizes the comparative technical performance. AnitoCrosshatch demonstrated stable and efficient rendering with consistent FPS and lower memory usage. Blender showed variable FPS, with averages as low as 88.23 and minimums dropping to 13.32 FPS. Unity maintained stable FPS but consumed significantly more memory due to its larger engine overhead.

#### **Figure 1.5** – FPS and Memory Usage Results  
![FPS Results](./assets/img/chapter5_perf_fpsresult.PNG)  
*FPS and memory usage over 1,000 frames. AnitoCrosshatch is abbreviated as AC.*

#### **Figure 1.6** – Technical Line Graph for Powerplant Scene  
![Line Graph](./assets/img/chapter5_perf_technicallinegraph.png)  
*FPS measured over 100 frames for the Powerplant scene with 12M+ triangles.*

AnitoCrosshatch emerged as the most balanced engine, offering consistent real-time performance and minimal memory consumption, confirming its potential as a lightweight alternative for stylized rendering.


## Image Quality and Similarity

### Perceptual-Based Metrics

We conducted a quantitative evaluation of images rendered by AnitoCrosshatch and Blender using perceptual-based metrics, given that comparisons were made against a reference dataset rather than 1:1 ground-truth images.

We used the following metrics:
- **LPIPS** (Learned Perceptual Image Patch Similarity) – Zhang et al., 2018
- **DISTS** (Deep Image Structure and Texture Similarity) – Ding et al., 2020

Each rendered image R<sub>i</sub> was compared to all reference dataset images D<sub>j</sub> using the above metrics. We then averaged the similarity scores to assess how close the rendered output was to comic-style illustrations.

The dataset used for comparison included 50 scanned comic pages and panels featuring crosshatching. Which follows the methodology of Vivoli et al. (2023), in which all images were left untreated to preserve original artistic qualities. Before evaluation:
- White areas (speech bubbles, gutters) were masked.
- The same mask was applied to both rendered and reference images.
- A **Canny Edge Detection** step was added to focus on line-based crosshatching characteristics (Agrawal & Desai, 2024).

#### **Figure 2.0** – Samples from the Crosshatching Reference Dataset  
![Dataset Samples](./assets/img/chapter5_perceptual_dataset.PNG)  
*Examples of raw, unaltered comic pages with crosshatching used in evaluation.*

#### **Figure 2.1** – Perceptual Metrics Results (LPIPS + DISTS)  
![Metrics Table](./assets/img/chapter5_perceptual_results.PNG)  
*Cross-hatched image results using LPIPS (masked + canny) and DISTS (masked + canny). Best values are bolded. AC = AnitoCrosshatch.*

#### **Figure 2.3** – Tested Rendered Images  
![Rendered Samples](./assets/img/chapter5_perceptual_renderedimages.png)  
*Rendered outputs compared across metrics. A = AnitoCrosshatch, B = Blender, C = Baseline (non-crosshatched).*

Results (Figure 2.1) show that AnitoCrosshatch (AC) consistently performed better in **DISTS**, indicating higher structural similarity with comic panels. LPIPS results were more mixed, with AC typically outperforming Blender, though in some cases baseline images performed comparably.

These results affirm the stylistic relevance of AnitoCrosshatch’s outputs while highlighting areas for refinement. The relatively high LPIPS scores suggest that perceptual realism is still lacking in some aspects. Enhancements to the pipeline could further bridge the perceptual gap between stylized renderings and authentic comic panels.


### Human Perceptual Evaluation

To complement our quantitative image similarity metrics, we conducted a human perceptual evaluation to assess how well **AnitoCrosshatch**’s cross-hatching output resembles actual comic book panels. This evaluation aimed to capture subjective quality judgments that automated metrics might miss, particularly regarding the artistic authenticity of the cross-hatching technique.

#### **Figure 3.0** – Reference and Rendered Image Pairs for Evaluation  
![Reference vs. Rendered Panels](./assets/img/chapter5_humansurvey.png)  
*Top: Reference comic book panel images. Bottom: Rendered images from AnitoCrosshatch.*

Each participant evaluated all 5 test images, providing ratings based on their perception of how closely the rendered cross-hatching matched the style and quality found in professional comic book panels.

#### **Figure 3.1** – Human Perceptual Evaluation Table  
![Evaluation Table](./assets/img/chapter5_humanperceptualtable.jpg)  
*Tabulated results of the perceptual evaluation for AnitoCrosshatch (n = 9 participants).*

#### **Figure 3.2** – Human Perceptual Evaluation Graph  
![Evaluation Graph](./assets/img/chapter5_perceptiontestgraph.png)  
*Graphical overview of human ratings on cross-hatching quality generated by AnitoCrosshatch.*

The survey results reinforce our quantitative findings that AnitoCrosshatch produces cross-hatching of **moderate quality** compared to professional comic art. This suggests that while the system successfully generates the basic visual elements of cross-hatching, further refinements to the rendering algorithm may be needed to achieve higher artistic fidelity.

Future improvements could focus on enhancing the **naturalness and variability** of the cross-hatching patterns to better match the organic quality found in hand-drawn comic illustrations.

<br><br><br>

* * *

Text can be **bold**, _italic_, or ~~strikethrough~~.

[Link to another page](./another-page.html).

There should be whitespace between paragraphs.

There should be whitespace between paragraphs. We recommend including a README, or a file with information about your project.

# Header 1

This is a normal paragraph following a header. GitHub is a code hosting platform for version control and collaboration. It lets you and others work together on projects from anywhere.

## Header 2

> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.

### Header 3

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
