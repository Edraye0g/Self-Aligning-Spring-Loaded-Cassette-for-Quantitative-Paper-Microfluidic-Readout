# Self-Aligning-Spring-Loaded-Cassette-for-Quantitative-Paper-Microfluidic-Readout

# Self-Aligning Spring-Loaded Cassette for Quantitative Paper Microfluidic Readout


## Description
Paper microfluidic test strips ($\mu$PADs) are exceptionally cheap and portable, but reading them by eye or with a handheld smartphone introduces massive human error. A microfluidic reader bridges the gap between cheap paper strips and lab-grade quantitative diagnostic data.

Standardizing Sample Fluid Flow: Paper channels rely on passive capillary action. If a user presses down on the strip unevenly, the microscopic pore structure squishes, altering fluid flow speed and reagent mixing rates. A mechanical reader applies uniform clamping pressure across the strip to ensure fluid wicked identically every time.  

Eliminating Optical & Lighting Noise: Taking a photo of a test strip with a smartphone introduces shadows, ambient light glare, and camera tilt. An optical reader acts as an enclosed mini-darkroom that holds the camera at a fixed focal distance and lighting angle, eliminating outside interference. Converting Qualitative Results to 

Quantitative Data: A basic paper test (like a home pregnancy test) only provides a qualitative "yes/no" answer based on a visible line. A microfluidic reader uses image processing algorithms to measure precise color intensity changes (RGB/HSV values), calculating exact analyte concentrations (such as glucose, protein, or toxin levels).  

Field-Ready Point-of-Care (POC) Testing: Traditional benchtop spectrophotometers cost thousands of dollars, require trained technicians, and need external electrical power. A passive mechanical reader allows healthcare workers in remote or low-resource settings to run high-precision diagnostics using basic smartphones. 

## Problem Statement
Paper-based microfluidic analytical devices (µPADs) enable low-cost point-of-care diagnostics, but manual sample application and inconsistent ambient light lead to high variance in colorimetric intensity measurements. Existing commercial readers are expensive, while manual phone imaging lacks positional and compression standardization.

## Project Objective & Novelty
Design and build a 3D-printed, completely passive mechanical cassette that applies uniform clamping pressure across a hybrid paper microfluidic strip while fixing a smartphone camera at a constant focal length and lighting angle.

Mechanical Novelty: A dual-stage spring compression mechanism that meters fluid volume by mechanical clamping while simultaneously locking an optical shroud into place over a phone lens.

## Targets

The proposed paper microfluidic reader acts as a passive diagnostic adapter that turns standard paper test strips and a personal smartphone into a standardized point-of-care reader. 

Applies Uniform Mechanical Clamping: Uses calibrated springs to deliver a constant ~15 kPa compression across the paper strip, eliminating flow rate variations caused by uneven manual handling.  

Blocks Ambient Light Noise: Functions as an enclosed optical darkroom that excludes >98% of ambient light and glare while using a frosted acrylic sheet to diffuse the smartphone's LED flash evenly across the strip.  

Locks Camera Alignment: Uses a universal sliding corner-clamp to align the smartphone camera lens at a fixed 45 mm focal distance with sub-0.5 mm alignment variance.  

Enables Quantitative Readouts: Works with a lightweight Python/OpenCV script to extract RGB/HSV color intensity values from captured images, reducing signal measurement variation by >50% compared to freehand photos.  

Operates Fully Passively: Requires zero external power, batteries, or motors, relying entirely on 3D-printed PETG snap-fit mechanisms and mechanical springs.

## Sub-Assembly Hardware Breakdown

1. Chassis & Mechanical DriveMain Base & Phone Cradle: 3D-printed PETG chassis featuring a sliding corner clamp mechanism.  
Platen Springs: 4x calibrated compression springs ($k = 0.8\text{ N/mm}$) delivering uniform clamping pressure across the platen.  
Fasteners: M3 socket head screws (8mm to 16mm lengths) paired with M3x4mm brass heat-set inserts to prevent plastic thread stripping.  

2. Optical Darkroom ComponentsEnclosed Shroud: Matte-black printed housing featuring interlocking lip-and-groove joints to exclude ambient light.  
Diffuser Layer: 2 mm frosted acrylic sheet positioned 10 mm above the paper bed to evenly spread smartphone flash illumination.  

3. Fluidic & Benchtop ReagentsPaper Strips: Whatman Grade 1 cellulose filter paper patterned with wax-printed hydrophobic channels.  
Model Assays: Non-toxic Tartrazine (yellow) and Methylene Blue dyes to simulate colorimetric biomarker reactions during testing. 

![](/images/components.png)

## Design Specifications & Engineering Requirements

### Mechanical & Structural Specs
**Clamping Force Range:** 12.0 – 18.0 N total force (delivering ~15 kPa across 10x20 mm reaction zone).
**Compression Travel:** 4.0 mm spring stroke with mechanical hard-stop to prevent over-compression.
**Structural Material:** PETG (100% infill for load-bearing brackets, 20% grid infill for shroud).
**Dimensional Tolerances:** ±0.15 mm on mounting pins; ±0.20 mm on sliding stage alignment.

### Optical & Imaging Specs
**Focal Distance:** Fixed 45.0 mm offset from camera lens to paper test zone.
**Stray Light Exclusion:** > 98% ambient occlusion using interlocking lip-and-groove shroud geometry.
**Diffuser Transmittance:** 82% matte frosted acrylic sheet for shadow elimination.
**Field of View (FOV):** 35 x 35 mm square imaging area (accommodates 4-channel microfluidic arrays).

![](/images/block_diagram.png)

## Methodology 

1. The Test Liquid
Model Colorimetric Dyes: Serial dilutions (0.01% to 1.0% w/v) of non-toxic dyes like Tartrazine (yellow) and Methylene Blue.  
Why Model Dyes: They mimic the color changes of real biological test strips (such as glucose, protein, or pH assays) without requiring lab safety approvals, refrigeration, or expensive reagents. 

2. The Engineering & Data Metrics (What is measured)Fluid Wicking Velocity: Measuring how capillary flow speed changes across paper channels under varying mechanical spring pressures (0 to 30 kPa).  
Positional Alignment Precision: Verifying that mounting and unmounting a smartphone 20 times maintains sub-0.5 mm camera lens alignment over the test zone.  Color Intensity Calibration: Extracting mean RGB and HSV pixel values via Python/OpenCV to plot a curve matching color saturation to dye concentration.  
Noise & Variance Reduction: Comparing signal repeatability to prove the cassette drops reading variance (Coefficient of Variation) from $>18\%$ down to $<5\%$ compared to freehand phone photos.  
Mechanical Endurance: Confirming the 3D-printed PETG frame and springs endure 100+ loading cycles without deformation. 

## Validation

1. Serial Dilution Standard Curve (Quantification)Setup: Prepare a serial dilution of non-toxic model dye (such as Tartrazine yellow or Methylene Blue) at known concentrations (e.g., 1.0%, 0.5%, 0.25%, 0.1%, 0.05%, 0.01% w/v).  
Action: Pipette fixed 10 µL drops onto Whatman filter paper channels and let them wick inside the clamped reader cassette.  
Validation: Image the strips, run a Python/OpenCV script to extract average RGB/HSV pixel values, and plot Mean Pixel Intensity against Concentration. Achieving a linear calibration curve ($R^2 > 0.95$) proves the camera accurately quantifies concentration changes.  

2. Sub-Visual Threshold Test (Camera vs. Human Eye)Setup: Prepare ultra-low concentration strips (e.g., 0.005% dye) where the color marker is virtually invisible.  
Action: Conduct a blinded visual check where 3–5 people evaluate whether a test line is present ("Positive" vs. "Negative").Validation: Compare human visual accuracy against the Python script's pixel intensity delta ($\Delta I = I_{\text{background}} - I_{\text{line}}$). Proving the software reliably identifies signal spikes ($\Delta I > 3\sigma_{\text{noise}}$) that humans misidentify demonstrates the sub-visual detection capability required for early disease screening.  

3. Repeatability & Noise Reduction Trial ($N=20$)Action: Image the exact same test strip 20 times under two distinct testing protocols:  
Freehand smartphone captures under varying ambient overhead lighting and hand tilts.  
Cassette captures locked inside the 3D-printed optical darkroom shroud.  
Validation Metric: Calculate the Coefficient of Variation ($\text{CV} = \frac{\sigma}{\mu} \times 100\%$) for both datasets to measure error reduction

4. OpenCV Processing Pipeline: The validation software workflow requires only a few lines of code: load the captured image $\rightarrow$ crop a fixed Region of Interest (ROI) over the test line $\rightarrow$ convert RGB to HSV/Grayscale $\rightarrow$ subtract paper background baseline $\rightarrow$ output numerical Optical Density.


## Risk Management & Failure Modes
### Risk 1 
Creep & Warping of 3D Printed Parts
Impact: Loss of clamping pressure over repeated spring loading.
Mitigation: Use high-yield PETG instead of PLA for structural hinges; increase wall thickness to 3.0 mm at stress concentrations.

### Risk 2
Variable Smartphone Camera Lens Placement
Impact: Camera misalignment leading to cropped diagnostic zone.
Mitigation: Implement a universal self-centering sliding corner-clamp with soft TPU padding to fit multiple phone sizes.

## Application

Point-of-Care (POC) & At-Home Diagnostics: Applied in rural clinics, emergency settings, or home care for rapid health screening (such as infectious disease screening, metabolic monitoring, salivary analysis, or urine biomarker assays).

Resource-Limited Global Health: Deployed in low-income or remote regions where medical facilities lack steady electricity, optical benchtop instruments, or trained laboratory technicians.

Environmental & Food Safety Testing: Used in field operations to rapidly test drinking water for heavy metal contamination or food products for chemical toxins using portable colorimetric strips.

## References

Anushka, A., Bandopadhyay, A., & Das, P. (2022). Paper based microfluidic devices: a review of fabrication techniques and applications. The European Physical Journal Special Topics, 232, 781–815.

Hiltunen, J., Liedert, C., et al. (2018). Roll-to-roll fabrication of integrated PDMS-paper microfluidics for nucleic acid amplification. Lab on a Chip, 18(11), 1552–1559.

Nishat, S., Jafry, A. T., Martinez, A. W., & Awan, F. R. (2021). Paper-based microfluidics: Simplified fabrication and assay methods. Sensors and Actuators B: Chemical, 336, 129681.

Xia, Y., Si, J., & Li, Z. (2016). Fabrication techniques for microfluidic paper-based analytical devices and their applications for biological testing: A review. Biosensors & Bioelectronics, 77, 774–789.

Yetisen, A. K., Akram, M. S., & Lowe, C. R. (2013). Paper-based microfluidic point-of-care diagnostic devices. Lab on a Chip, 13(12), 2210–2251.
