## Acute vertex

Perform a heuristic search for sharp angles given an object contour and user specified parameters. The acute (sharp)
angles are often associated with object tip points. Outputs a python list of points that meet criteria specified in parameters.

**plantcv.acute_vertex**(*img, obj, window, thresh, sep*)

**returns** list of points that meet specified criteria, image with points selected

- **Parameters:**
    - img - A copy of the original image
    - obj - A contour of the plant object (this should be output from the object_composition.py fxn)
    - window - The pre and post point distances on which to calculate angle of focal point (a value of 30 worked well for a sample image) on which to calculate the angle
    - thresh - Threshold to set for acuteness; keep points with an angle more acute than the threshold (a value of 15 worked well for sample image)
    - sep - The number of contour points to search within for the most acute value
- **Context:**
    - Used to identify tip points based upon the angle between focal pixel and reference points on contour. 
- **Output data stored:** [Summary of Output Observations](output_measurements.md#summary-of-output-observations)
    
**Input plant contour**

![Screenshot](img/documentation_images/acute_vertex/av_example_image.jpg)

```python
from plantcv import plantcv as pcv

# Set global debug behavior to None (default), "print" (to file), 
# or "plot" (Jupyter Notebooks or X11)

pcv.params.debug = "print"

# Identify acute vertices (tip points) of an object
# Results in set of point values that may indicate tip points
list_of_acute_points, points_img = pcv.acute_vertex(img, obj, 30, 15, 100)

```

**Image of points selected**

![Screenshot](img/documentation_images/acute_vertex/av_output.jpg)
