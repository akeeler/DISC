DISC: Dual-energy Image Synthesizer for Cone-beam CT
==========

DISC is an open-source platform for quickly synthesizing, viewing, assessing, and optimizing dual-energy cone-beam CT (CBCT) images.
Users can load CBCT image volumes for either conventional polychromatic scans or decomposed basis material volumes.  DISC can compute,
in near real time, several dual-energy based images from these loaded images.

Image types
=========
Blended : Blended images are computed by taking a linear combination of the input low-energy and high-energy scans, which can be useful
for noise suppression and contrast enhancement.  If this image type is selected, a slider controlling the blending ratio is enabled so
the user can adjust the blending ratio manually.  Currently only constant blending ratio is supported.

Virtual Monoenergetic (VM) : Virtual monoenergetic images (VMIs) depict an object as if it were imaged using a single, well-defined photon
energy instead of a polychromatic x-ray spectrum produced by a conventional x-ray source.  VMIs can provide images at energies lower than 
could typically be obtained using physical x-ray tubes due to photon starvation, which can provide enhancement in image contrast.  VMIs
also can suppress artifacts due to beam hardening, removing the need for spectrum correction during scan preprocessing.  If this image 
type is selected, a slider controlling the energy of the VMI, ranging from 20 to 150 keV in 1 keV increments, is enabled so the user can 
adjust the VMI energy manually.  The optimize dropdown is also enabled so the user can automatically determine and display the VMIs that 
best display the desired behavior (contrast-to-noise ratio (CNR), absolute contrast, and uniformity).

Image Analysis
============
Regions of Interest (ROIs) : Up to two ROIs can be drawn on a displayed image in several geometries, including circular, rectangular, 
polygonal, and freehand.  Once and ROI is drawn, DISC automatically computes and displays the average pixel value, standard deviation, and 
signal-to-noise ratio (SNR) within the ROI.  If two ROIs are drawn, DISC also displays the CNR between the two ROIs.  ROIs are automatically 
redrawn when the image is changed, allowing for easy comparison between various image types.

Optimize : When viewing VMIs, several automated optimization procedures are enabled.  Each can be performed by selecting the appropriate
option from the dropdown and then pressing the optimize button.  Each will take a few seconds to assess the image quality at each VMI energy
and display the optimal image as well as popping out a plot showing that metric as a function of VMI energy.

Maximize CNR : If this optimization procedure is selected, DISC will compute and display the VMI that maximizes the CNR computed between two
selected ROIs.  Two ROIs must be drawn in order to perform this optimization procedure.

Minimize Contrast : If this optimization procedure is selected, DISC will compute and display the VMI that minimizes the absoluted contrast 
in pixel value between two selected ROIs.  Two ROIs must be drawn in order to perform this optimization procedure.

Uniformity : This procedure is similar to the Minimize Contrast option above, but is designed specifically to replicate the uniformity 
assessment carried out on the Catphan 500/600 quality assurance phantoms.  5 circular ROIs are drawn and the maximum deviation of each ROI 
from the average of all 5 ROIs is computed.  This procedure will work best if the active slice of the image volume is of a uniform material, 
such as the uniformity module of the Catphan phantom.
