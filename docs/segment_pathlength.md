## Measure Path Length of Segments 

Measure the geodesic distance of segments. 

**plantcv.morphology.segment_path_length**(*segmented_img, objects*)

**returns** labeled_image  

- **Parameters:**
    - segmented_img - Segmented image (output either from [plantcv.morphology.segment_skeleton](segment_skeleton.md)
    or [plantcv.morphology.segment_id](segment_id.md)), used for creating the labeled image. 
    - objects - Segment objects (output from either [plantcv.morphology.prune](prune.md),
    [plantcv.morphology.segment_skeleton](segment_skeleton.md), or
    [plantcv.morphology.segment_sort](segment_sort.md)).
- **Context:**
    - Calculates the geodesic distance of each segment. Users can pass only 
    leaf objects (returned from [plantcv.morphology.segment_sort](segment_sort.md)) to only collect lengths of leaves only.
    Path lengths are automatically stored to the [outputs class](outputs.md).
- **Output data stored:** [Summary of Output Observations](output_measurements.md#summary-of-output-observations)

**Reference Image:** segmented_img 

![Screenshot](img/documentation_images/segment_path_length/segmented_img_mask.jpg)


```python

from plantcv import plantcv as pcv

# Set global debug behavior to None (default), "print" (to file), 
# or "plot" (Jupyter Notebooks or X11)
pcv.params.debug = "print"

labeled_img = pcv.morphology.segment_path_length(segmented_img=segmented_img, 
                                                 objects=obj)

```

*Labeled Image*

![Screenshot](img/documentation_images/segment_path_length/labeled_path_lengths.jpg)
