## Segment Insertion Angles  

Measure leaf insertion angles. 

**plantcv.morphology.segment_insertion_angle**(*skel_img, segmented_img, leaf_objects, stem_objects, size*)

**returns** labeled image 

- **Parameters:**
    - skel_img - Skeletonize image (output from [plantcv.morphology.skeletonize](skeletonize.md)). 
    - segmented_img - Segmented image (output from either [plantcv.morphology.prune](prune.md),
    [plantcv.morphology.segment_skeleton](segment_skeleton.md), or
    [plantcv.morphology.segment_sort](segment_sort.md))., used for creating the labeled debugging image. 
    - leaf_objects - Leaf segment objects (output from [plantcv.morphology.segment_sort](segment_sort.md)).
    - stem_objects - Stem segment objects (output from [plantcv.morphology.segment_sort](segment_sort.md)).
    - size - Size of ends (number of pixels) used to calculate insertion point "tangent" lines
- **Context:**
    - Find "tangent" angles to leaf insertion points in degrees of skeleton segments compared to the stem angle. 
      Use `size` pixels of the inner portion of each leaf to find a linear regression line, and calculate angle between insertion
      angle and the stem. Insertion angles are automatically stored in the [outputs class](outputs.md).        
- **Output data stored:** [Summary of Output Observations](output_measurements.md#summary-of-output-observations)

**Reference Image:** segmented_img 

![Screenshot](img/documentation_images/segment_tangent_angle/segmented_img_mask.jpg)


```python

from plantcv import plantcv as pcv

# Set global debug behavior to None (default), "print" (to file), 
# or "plot" (Jupyter Notebooks or X11)
pcv.params.debug = "print"

# Adjust line thickness with the global line thickness parameter (default = 5)
pcv.params.line_thickness = 3 

labeled_img = pcv.morphology.segment_insertion_angle(skel_img=skeleton,
                                                     segmented_img=leaves_segment, 
                                                     leaf_objects=leaf_obj,
                                                     stem_objects=stem_objs,
                                                     size=20)

```

*Labeled Image*

![Screenshot](img/documentation_images/segment_insertion_angle/insertion_angle_img.jpg)
