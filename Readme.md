# Goal

- produce a label matrix with output
- evaluate efficacy

## Ground Truth

- Ground truth will be stored in files named anXXXXX_YYYY_MM_DD_fov_NNNNN_rois.mat ( where all repeated capital letters are decimal digits with XXXXX indicates the animal, YYYY_MM_DD indicates the date in year month day format, and NNNNN represents a field of view ).
- These files will contain a group called `roi`. Inside of that group will be the following fields.
	- `mask` - An array where each index represents a different ROI. All other indices represent spatial coordinates.
	- `centroid_xy` - A matrix where the first index will represent the relevant ROI. The last will represent which axis of the centroid is being represented.
	- `burst_rate` - A vector where the index represents the relevant ROI.
- In addition, the raw data will be supplied in TIFFs named Image_Registration_4_anXXXXX_YYYY_MM_DD_main_FFF.tif ( where all repeated capital letters are decimal digits with XXXXX indicates the animal, YYYY_MM_DD indicates the date in year month day format, and FFF represents the frame )

## Evaluating Efficacy

Two metrics will be used.

1. Distance between centroids of detected and ground truth ROIs (i.e. as measured by the L<sub>2</sub> or Euclidean norm).
2. Percentage overlap of detected and ground truth ROIs (i.e. mask intersection divided by union).

The results will be broked down into 3 categories. The determination of which category they fall into will dependent on a chosen acceptance threshold for the relevant metric.

1.	True Positives - How many matches are there between detected and ground truth ROIs
2.	False Negatives - How many ground truth ROIs are missed?
3.	False Positives - How many detected ROIs are incorrect (i.e. do not correspond to one in the ground truth).

After assessing both metrics, the next relevant question is how does activity/noise affect detectability? This will require plots of these categories against the burst rate.

Finally, these metrics must be stored in some readable format for future use.

## Notes

Data is almost always 2 channel. Only use the green channel (1st one).
