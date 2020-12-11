# The-SUSTech-SYSU-dataset-for-automated-exudate-detection-and-diabetic-retinopathy-grading
Automated detection of exudates from fundus images plays an important role in diabetic retinopathy (DR) screening and evaluation, for which supervised or semi-supervised learning methods are typically preferred. However, a potential limitation of supervised and semi-supervised learning based detection algorithms is that they depend substantially on the sample size of training data and the quality of annotations, which is the fundamental motivation of this work. In this study, we construct a dataset containing 1219 fundus images (from DR patients and healthy controls) with annotations of exudate lesions. In addition to exudate annotations, we also provide four additional labels for each image: leftversus- right eye label, DR grade (severity scale) from three different grading protocols, the bounding box of the optic disc (OD), and fovea location. This dataset provides a great opportunity to analyze the accuracy and reliability of different exudate detection, OD detection, fovea localization, and DR classification algorithms. Moreover, it will facilitate the development of such algorithms in the realm of supervised and semi-supervised learning.

## Data records

This dataset is publicly available at https://drive.google.com/file/d/1QKM05fYr_S5lh4v0r-jL7HLrxqphNpoe/view?usp=sharing and https://figshare.com/s/792d1b02f65be0c08214, 
which is stored as a zip file. In the unzipped folder, all the raw fundus images, the exudate annotations, the DR 
grading labels, and the OD and fovea location annotations are stored in three subfolders, namely "originalImages", 
"exudateLabels", and "odFoveaLabels". In the "originalImages" folder, files are saved in the JPG format and named 
as "n.jpg", with n ranging between 0001 and 1219 indicating the n^th sample. In that folder, we also 
provide a comma-separated-values (CSV) file named "drLabels.csv", wherein the first column indicates the file 
name, the second column indicates the left-versus-right eye categories with 0 representing left eyes and 1 right 
eyes, the third column indicates the DR category assessed via the International Clinical DR Severity Scale (0 to 5, 
with 0 representing normal healthy, and 1 to 5 respectively representing mild non-proliferative DR, moderate 
non-proliferative DR, severe non-proliferative DR, proliferative DR, and DR with laser spots or scars), the fourth 
column indicates the DR grade assessed via the American Academy of Ophthalmology protocol, and the fifth 
column indicates the DR grade assessed via the Scottish DR grading protocol. Another CSV file named 
"c5_DR_reclassified.csv" provides the DR labels for images belonging to category 5 assessed via the three 
protocols. The exudate detection labels, OD bounding box's coordinates, as well as fovea location's coordinates
 are saved in the XML format stored at the corresponding folders (namely "exudateLabels" and "odFoveaLabels"), 
following the same specifications as the Pascal Voc dataset \cite{everingham2015pascal}. Hard and soft exudates 
are labeled separately in this dataset. In the XML files, "ex" stands for hard exudates and "se" for soft exudates.

## Usage Notes

After copying all images from the "originalImages" folder to the "exudateLabels" and "odFoveaLabels" folders, 
users can directly open the provided fundus images and the corresponding exudate detection labels, OD bounding 
box's coordinates, as well as fovea location's coordinates using Labelimg (a graphical image annotation tool, which 
can be accessed at https://github.com/tzutalin/labelImg). This tool provides functions of visualizations and 
modifications of annotations (according to research needs). Please note in order to display directly in Labelimg, 
the fovea location's coordinates are transformed into a small box (F_x,F_y,F_{x+1},F_{y+1}).

For fundus image processing and analysis using this dataset, we recommend applying, for example, CLAHE or 
gamma correction as preprocessing steps to enhance contrast and correct illumination. As for relatively blurry images 
or images with artifacts, recent quality-enhancement methods, such as those make use of generative adversarial 
networks or other types of deep neural networks, may be beneficial.

For the BBR-Net, it was initially employed in one of our previous works. As its name suggests, it is mainly utilized to 
refine coarse or inaccurate bounding boxes. It was not specifically designed for a specific type of lesion. Our previous 
paper only took hemorrhages as an example. In practice, users only need to use it when the object detection 
bounding boxes are not accurate. Because our exudate labels provided in this work had been re-checked/corrected 
by a third ophthalmologist at the final step, they can be used directly without using BBR-Net any more.

## Citation
Lin, L., Li, M., Huang, Y., Cheng, P., Xia, H., Wang, K., ... & Tang, X. (2020). The SUSTech-SYSU dataset for automated exudate detection and diabetic retinopathy grading. Scientific Data, 7(1), 1-10.
