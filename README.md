

# Cytoskeleton and Cell Morphology Analysis (BBBC018)

**Karp Chapter 9: The Cytoskeleton and Cell Motility**

**Student ID:** [202303495]\
**Dataset:** BBBC018 - Human HT29 Colon-Cancer Cells\
**Selected Phenotype:** Anaphase/telophase (visual classification) **Image-Field ID:** 19467

---

## Introduction

The cytoskeleton helps cells keep their shape, resist mechanical stress, and reorganize when they change form or divide. In this activity, fluorescence images of HT29 human colon-cancer cells from the BBBC018 dataset were examined to observe F-actin distribution and cell shape.

The selected phenotype was Anaphase/telophase, chosen by visually comparing the image field with the examples on the BBBC018 page. Five cells were measured in ImageJ.JS (browser version of ImageJ), and the measurements were analyzed in R to compare cell area, circularity, aspect ratio, and mean actin fluorescence intensity.

---

## Dataset and Selected Images

The fluorescence images were obtained from the Broad Bioimage Benchmark Collection (BBBC018).

- **Dataset:** [BBBC018](https://bbbc.broadinstitute.org/BBBC018)
- **Download:** [BBBC018_v1_images.zip](https://data.broadinstitute.org/bbbc/BBBC018/BBBC018_v1_images.zip)
- **Phenotype:** Anaphase/telophase (visual classification, not a verified annotation)
- **Image-field ID:** 19467
- **Actin filename:** `19467-actin.DIB`
- **DNA filename:** `19467-DNA.DIB`

The actin channel was used to examine F-actin staining and trace cell boundaries, while the DNA channel served as a guide for locating nuclei and telling neighboring cells apart.

---

## Methods

### Image Analysis

- The `.DIB` actin and DNA images were converted to `.tiff` and opened in ImageJ.JS, then set to 8-bit grayscale (Image > Type > 8-bit).
- Five cells with distinguishable boundaries were selected on the actin image.
- Area, Mean gray value, Shape descriptors, and Display label were enabled under Set Measurements.
- The Freehand Selection tool was used to trace each cell, and each outline was measured with Analyze > Measure.
- The Results table was saved as `data/fiji_results.csv`.
- The annotated image showing the five labeled cells was saved as `figures/measured_cells.png`.
- Note: because the images were converted to 8-bit TIFF, mean gray values are on a 0 to 255 scale and may differ from values measured on the original `.DIB` files.

### R Analysis

- The measurements were imported into RStudio (Posit Cloud) using `scripts/analyze_cells.R`.
- The mean cell area, circularity, aspect ratio, and actin fluorescence intensity of the five cells were calculated.
- Two graphs were generated to compare cell area versus circularity and the mean actin fluorescence intensity of the five cells.

---

## Results

The following figures present the cell morphology analysis. Five HT29 cells from image field 19467 were examined to determine their cell area, circularity, aspect ratio, and mean F-actin fluorescence intensity.

### Five Measured HT29 Cells

Five cells with distinguishable boundaries were traced on the actin image with the Freehand Selection tool and measured one at a time. The annotated image shows the five numbered outlines.

<img width="1060" height="1117" alt="IMG_3240" src="https://github.com/user-attachments/assets/3873c0f0-78ca-4d50-98bf-dbc24b140652" />


**Figure 1.** F-actin fluorescence image of HT29 cells from field 19467, showing the five selected cells outlined and numbered.

### Cell Area versus Circularity

A scatter plot was generated in RStudio to examine the relationship between cell area and circularity among the five selected cells.

<img width="900" height="650" alt="IMG_3251" src="https://github.com/user-attachments/assets/225ce46c-cde7-4624-af86-e05b680f694e" />


**Figure 2.** Scatter plot showing the relationship between cell area and circularity among the five measured HT29 cells.

The cells had areas ranging from 591 to 3230 pixels², with Cell 1 having the largest area. Circularity values ranged from 0.818 to 0.971 with a mean of 0.8992. This indicates that the measured cells were mostly rounded, although Cell 1 was noticeably less circular (0.818) than the others. There was no clear relationship between cell area and circularity: Cell 1 was the largest and least circular, but Cell 2, the second largest, was the most circular (0.971), and the two smallest cells (Cells 3 and 4) had intermediate values of 0.901 and 0.876. With only five cells, no trend can be concluded.

### Mean Actin Fluorescence Intensity

A bar graph was also generated to compare the mean F-actin fluorescence intensity of the five measured cells.

<img width="900" height="650" alt="IMG_3252" src="https://github.com/user-attachments/assets/6e1252f4-3c5b-4d82-9ba9-392b9cd310b2" />


**Figure 3.** Bar graph comparing the mean F-actin fluorescence intensity of five HT29 cells from image field 19467.

Cell 2 showed the highest mean F-actin fluorescence intensity at 92.161 AU, while Cell 5 had the lowest at 78.216 AU. The average intensity across all five cells was 85.343 AU. The differences between cells were modest, about 14 units on the 0 to 255 scale of the 8-bit image, which suggests fairly similar actin staining among the measured cells within the same image field.

---

### Cell Measurement Summary

The table below presents the average measurements of the five selected HT29 cells obtained in ImageJ.JS and analyzed in RStudio.

| Measurement                  | Mean Value  |
| ---------------------------- | ----------- |
| Cell area                    | 1471.6 pixels² |
| Circularity                  | 0.8992      |
| Aspect ratio                 | 1.3118      |
| Actin fluorescence intensity | 85.3434 AU  |

The five measured cells had an average area of 1471.6 pixels², with a wide spread in size (591 to 3230 pixels²). The mean circularity of 0.8992 suggests the cells were generally rounded, and the mean aspect ratio of 1.3118 suggests slight elongation on average, driven mostly by Cell 1 (aspect ratio 1.788). The average actin signal of 85.3434 AU is on an 8-bit scale and should not be compared directly with other image fields.

---

## Guide Questions

***1. Which specific phenotype did you choose, and what visible features support that choice?***

I chose the Anaphase/telophase phenotype based on the visual appearance of the selected image field. The rounded cell shapes and the DNA channel were used to examine possible signs of cell division. However, the separation of genetic material into two distinct groups was not clearly verified in every cell. Therefore, the phenotype classification was based on visual comparison with the BBBC018 reference images rather than confirmed identification of individual cells undergoing anaphase or telophase.

***2. Were your five cells mostly round or elongated? Refer to your circularity and aspect-ratio results.***

The five cells were mostly rounded, with an average circularity of **0.8992** and an average aspect ratio of **1.3118**. Four of the five cells had circularity of 0.876 or higher and aspect ratios between 1.076 and 1.305, while Cell 1 was the exception, with a lower circularity of 0.818 and an aspect ratio of 1.788, meaning it was noticeably more elongated.

***3. What role does actin play in maintaining cell shape and in cell movement (Karp Chapter 9)?***

Actin filaments help maintain cell shape by forming a supportive network beneath the plasma membrane. They also contribute to cell movement through continuous assembly and disassembly of filaments. This process produces structures such as lamellipodia and filopodia, which help cells extend their membranes, attach to surfaces, and move. Therefore, actin is important in both maintaining cell structure and allowing cells to change shape during movement.

***4. Why can a single fixed fluorescence image NOT show how fast a cell moves?***

A single fixed fluorescence image captures only the appearance and position of cells at one specific moment. It does not provide information about changes in their positions over time. Measuring cell movement requires multiple images taken at different time points so that the distance traveled and the time elapsed can be compared. Therefore, a single image can reveal cell morphology and actin distribution but cannot determine cell movement speed.

## Conclusion

The analysis of five HT29 cells from field 19467 showed that the selected cells were mostly rounded, with large differences in size (591 to 3230 pixels²) and only modest differences in F-actin fluorescence intensity (78.216 to 92.161 AU). Their mean circularity of 0.8992 and aspect ratio of 1.3118 supported the observation that most cells had rounded shapes, with Cell 1 being the most elongated. The phenotype was assigned by visual comparison, and the images were converted to 8-bit TIFF in a browser version of ImageJ, so the intensity values are relative. Taken together, the activity demonstrated how fluorescence microscopy and image analysis software can be used to examine cell morphology and actin organization.

---

## References and Data Sources

Broad Bioimage Benchmark Collection. (n.d.). *BBBC018: Human HT29 colon-cancer cells (diverse phenotypes).* Broad Institute. [https://bbbc.broadinstitute.org/BBBC018](https://bbbc.broadinstitute.org/BBBC018)

Ljosa, V., Sokolnicki, K. L., & Carpenter, A. E. (2012). Annotated high-throughput microscopy image sets for validation. *Nature Methods, 9*(7), 637. [https://doi.org/10.1038/nmeth.2083](https://doi.org/10.1038/nmeth.2083)

### Data Credit and Image License

**Data Credit:** We used image set BBBC018v1 from the Broad Bioimage Benchmark Collection (Ljosa et al., Nature Methods, 2012).

**Image License:** Creative Commons Attribution-NonCommercial-ShareAlike 3.0 (CC BY-NC-SA 3.0).



