## Measure Tangent Angles of Segments  

Measure tangent angles of segments as a way to quantify leaf behavior. 

**plantcv.morphology.segment_tangent_angle**(*segmented_img, objects, size*)

**returns** labeled image 

- **Parameters:**
    - segmented_img - Segmented image (output either from [plantcv.morphology.segment_skeleton](segment_skeleton.md)
    or [plantcv.morphology.segment_id](segment_id.md)), used for creating the labeled image. 
    - objects - Segment objects (output from either [plantcv.morphology.prune](prune.md),
    [plantcv.morphology.segment_skeleton](segment_skeleton.md), or
    [plantcv.morphology.segment_sort](segment_sort.md)).
    - size - Size of ends (number of pixels) used to calculate "tangent" lines
- **Context:**
    - Find 'tangent' angles in degrees of skeleton segments. Use `size` pixels on either end of
      each segment to find a linear regression line, and calculate angle between the two lines
      drawn per segment. Users can pass only leaf objects (returned from [plantcv.morphology.segment_sort](segment_sort.md)) 
      to only collect angles of leaves. Tangent angles are automatically stored to the [outputs class](outputs.md). 
- **Output data stored:** [Summary of Output Observations](output_measurements.md#summary-of-output-observations)

**Reference Image:** segmented image 

![Screenshot](img/documentation_images/segment_tangent_angle/segmented_img_mask.jpg)


```python

from plantcv import plantcv as pcv

# Set global debug behavior to None (default), "print" (to file), 
# or "plot" (Jupyter Notebooks or X11)
pcv.params.debug = "print"

# Adjust line thickness with the global line thickness parameter (default = 5)
pcv.params.line_thickness = 3 

labeled_img = pcv.morphology.segment_tangent_angle(segmented_img=leaves_segment, 
                                                   objects=leaf_obj,
                                                   size=15)

```

*Labeled Image*

![Screenshot](img/documentation_images/segment_tangent_angle/tangent_angle_img.jpg)
