# Schlieren setup to visualize-acoustic and heat waves
Develop a working Schlieren imaging setup to visualize heat waves and modifying it to visualize acoustic waves. 
## Basic Principles
Small-scale perturbations in the density of air due to gases and pressure waves cause minor alterations in the refractive
index as well. These slight changes in the refractive index cause phase speed differences in light, obscured to the eye. Change in phase speed as light passes through a
medium is termed as refraction. Schlieren visualization translates this refraction of light through a medium into changes in intensity that can be perceived
as regions of light and dark.

A light ray passing orthogonally through a change in refractive index will experience a change in phase velocity
but will continue traveling in the same direction undeflected [1]. If the light ray intersects the change in refractive index obliquely, it will bend towards
the region with greater “n” dictated by Snell’s law:

![image](https://user-images.githubusercontent.com/34755328/209582472-2d3d0d5f-0b03-4e8b-a861-34fe4853c0d7.png)

For a light ray travelling in the z-direction intersecting a region of gradient variation in refractive index, the ray curvature and its refraction is given by:

![image](https://user-images.githubusercontent.com/34755328/209582502-e7bce4b5-56c9-4c70-985f-2680047cbf91.png)

These angular ray deflections caused due to refraction are made perceivable by the Schlieren visualization setups [1].

## Z-Type 2-Mirror Schlieren system
The Z - Type 2-Mirror Schlieren System utilizes two oppositely tilted, on-axis parabolic mirrors as shown in Figure 3. The combination of a diverging light beams from a slit source, 
an opposite converging beam, and the collimated light between the two mirrors through the test area suggests the letter “z” [3].

![image](https://user-images.githubusercontent.com/34755328/209582683-2747a5d8-74de-4b7c-ae92-255468e78776.png)
 
Schematic of Z-Type 2-Mirror Schlieren System [1]

Despite the slight tilt, the mirrors are symmetrical on-axis parabolas. A minimum distance between the field mirrors of about 2f (where f is the mirror focal length) is maintained to provide space for the test area. 
This gives an inherent advantage of a larger field-of-view to the Z-type setup [3]. Furthermore, the Z-type setup occupies little area for assembly and operation which saves space in the lab. 
For a given budget, z-type setup is much more cost efficient than the lens type schlieren setup delivering a comparable performance [1]. 

## Theoretical Modeling

Computational fluid dynamics (CFD) methods are employed on supercomputers to solve equations of motion for inviscid and viscous flows by numerical calculations. 
These CFD calculations compute the output Schlieren images that are later validated by experimental results [6]. 
However, the intention of the project objectives was to gauge the upper limit bound of the sensitivity the given setup could achieve. 
Hence, CFD calculations are not required to calculate the spatial differential illuminance (relative dark and bright regions on the Schlieren Image). 
The simplistic model developed in Python takes the dimensions/specifications of the components used as input parameters to estimate sensitivity of the setup.

The model first computes the magnitude of strain caused by pressure waves corresponding to a range of frequencies using the following equation:

![image](https://user-images.githubusercontent.com/34755328/209583014-2bc21d56-b96a-4b82-8254-ac6903f891a2.png)

The variations in the refractive index are computed to obtain the perturbed refractive index as follows:

![image](https://user-images.githubusercontent.com/34755328/209583103-1d6ff77c-4ddc-416d-a984-75ec3b35ffdc.png)

For "i" number of light rays with arbitrary (miniscule) incidence angles the model computes the refraction angles and the vertical displacement suffered by the light rays due to the
fluctuating refractive indices. 
The model considers a 2D force-field of pressure waves dependent on ultrasound device dimensions to perform the computations.
Differential illuminance intensity was calculated based on the knife-edge cutoff value and the dimensions of the focal point projected by the utilized parabolic mirrors.
The computed differential illuminance was plotted as a function of changes in pressure. 
The sensitivity of the setup is obtained as the slope dI/dP of the output graph as shown in Modeling Results.

## Modeling Results
An estimate of sensitivity was calculated for the following range of inputs tuned to our developed setup:

![image](https://user-images.githubusercontent.com/34755328/209583334-b94dc0da-3eab-4418-9cb9-50b739f5394b.png)

Modeling output to calculate the sensitivity of the setup

Results indicate that for every 5 kPa increase in pressure, we see 45.03 lumen/m2 dark (bright) levels due to the obstruction of refracted light rays by knife edge.

## Experimental Setup

![image](https://user-images.githubusercontent.com/34755328/209583413-1da6676d-8c96-437e-afaa-8d0626689da2.png)
![image](https://user-images.githubusercontent.com/34755328/209583508-ee726251-2e23-4fb3-82fc-5bc73398857a.png)

## Hardware

* Light source - 
The LED light source, MCWHLP1 Mounted LED, used has an output of 41.3 W/m2 (~2828 lumen/m2) lumens. 
An LED cover was needed to constrict the light source to a single point 1mm. 
Such a cover was designed, and 3D printed [4] to fit over the LED Light source.

![image](https://user-images.githubusercontent.com/34755328/209583673-6c452245-ceab-46a1-95e7-aa01aac0a85d.png)

Front and side views of the LED light source and the LED driver

![image](https://user-images.githubusercontent.com/34755328/209583762-2ac98a3a-0c16-47b0-bdb8-fb3b36d85078.png)

3D rendering of the designed LED cover and images of 3D printed parts

To perform the heat wave visualization, the LED light source is placed on a constant maximum intensity for imaging. 
To perform the ultrasonic wave visualization, the LED was placed on a modulated driver; tuning the LED to strobe to a corresponding duty cycle of a pulse wave similar to that of the pressure wave frequency will allow for increased contrast levels in experimentation.

* Screen Projection and Knife Edge - 
A paper screen mounted on stand for rigidity and stability was used to project the schlieren imaging, allowing for easy maneuvering to capture the reflection. 
A standard knife edge was mounted onto a stand for rigidity and stability to allow for easy maneuvering to locate the focal point.

![image](https://user-images.githubusercontent.com/34755328/209583841-5acf2edc-0e69-498c-a130-f5e77846dc9f.png)

Screen used to project the image

![image](https://user-images.githubusercontent.com/34755328/209583854-8aa2557f-0ad1-4129-94e7-fe4ee8194237.png)

Position and mount of the knife edge used

* Parabolic Mirrors -
Optics selection within a Schlieren setup are one of the more prominent drivers of the result resolution and sensitivity. 
As optics increase in size, there is an increase in usable the field of view. 
However, the largest limitation is price; larger aperture optics are more expensive than similar smaller ones [4][2].
The parabolic mirrors have a diameter of 60cm, with a focal length of 37.5 cm. 
Note, a compromise for the larger diameter is the likelihood of spherical aberrations, a result that can impact the imaging.

Parabolic mirror mounts were designed, and laser cut with 6mm Acrylic sheets. 

![image](https://user-images.githubusercontent.com/34755328/209584056-4ca165d3-6500-4cd5-a844-553eedfca4b5.png)

Designed layout of parabolic mirror holder to be laser cut

![image](https://user-images.githubusercontent.com/34755328/209583979-e15ef536-7e73-4721-b2c2-02cb8ba59800.png)

Assembled and laser cut holder with parabolic mirror placed

* Acoustic Wave Source - UltraHaptics system -
UltraHaptics Touch is the system used to source the acoustic waves. 
This system focuses ultrasound projections into discrete points to provide a multi-point haptic feedback as a users’ hands are hovered over an interactive surface [5], to provide haptic feedback. 

![image](https://user-images.githubusercontent.com/34755328/209584011-770dcf97-ba6b-41c6-8f8e-10e6e2755065.png)

UltraHaptics Touch System

## Experimental Results
Experimentation of the Schlieren setup was broken down into two parts (1) to detect heat waves and (2) to detect sound waves. 
The benefit of visualizing heat waves was to validate the experimental setup and fine tune the resolution and sensitivity of the setup prior to testing acoustic waves.

* Imaging Heat Waves - 
The setup to visualize heat wave was successful. 
A soldering iron was used as a heat source, set at 400C and the resulting image can visualize the differences as heat waves propagate from the source.

![image](https://user-images.githubusercontent.com/34755328/209584242-d9f654a2-26dd-4e64-929b-1ce9cd5f22d6.png)

* Imaging Acoustic Waves -
The setup to visualize acoustic waves was unsuccessful.  

## Discussions
The working principles of a Schlieren system applied to visualize heat waves was simple, requiring adjustments to the angles and focal lengths to identify the optimal locations for the knife edge, screen, and LED light source. 
The operational parameters were all adjusted to obtain as sharp of a contrast with a larger field of view and as little distortions as possible. 
One of the limitations with the current parabolic mirror was the presence of surface aberrations. 
Such imperfections can be visualized in the resulting image, where there are a series of artifacts across the whole field of view. 
This reflects off the surface imperfections visible as shown.

![image](https://user-images.githubusercontent.com/34755328/209585262-de058594-e6d3-496f-ae73-6b4d35dc86ec.png)

Surface of parabolic mirror with surface imperfections circled in red
 
Further observations note that in addition to the parabolic mirror, there were limitations to the LED light source that resulted in lower contrast,
sensitivity, and resolution. 
The LED light required an LED cover to constrict the light source, a part that was designed and 3D printed with a diameter of 1mm. 
Two main factors were the 3D printing material and the diameter. 
The material used was not truly opaque, allowing light leakage to the surrounding. 
Furthermore, the diameter should be made even smaller, allowing for a single light source to be focused even further upon refractions.
This was noticed as the refractions past the second concave mirror did not result in a single focal point, rather an ellipse. 
It is noted that this is also attributed to the mirror surface aberrations. 

Although visualization of heat waves was successful, the resulting image did lack the resolution and contrast to visualize smaller changes of heat waves, i.e., body heat from a users’ hand
or breath. 
Because of this, the inability to generate a higher contrast image with the system results with difficulty when translating to acoustic waves. As the
LED light source was placed in a strobing function at a frequency of 40kHz, it aimed to increase the contrast of the UltraHaptics ultrasonic wave output.
However, this was not enough to account for the aforementioned equipment limitations of the LED light sources and the parabolic mirrors.

The theoretical model generated sought to detail the sensitivity output to expect given the current experimental setup input
factors; it suggested a realizable sensitivity of 45 lumen/m2 5kPa. 
Theoretically, the given experimental inputs should provide a working image, however, the equipment limitations did not allow for such sensitivity values to be feasible.

## References
[1] Settles, G. S. (2012). Schlieren and Shadowgraph Techniques: Visualizing Phenomena in Transparent Media (Experimental Fluid Mechanics) (Corrected ed.). Springer.

[2] Lim, T. T., & Smits, A. J. (2012). FLOW VISUALIZATION: TECHNIQUES AND EXAMPLES (2ND EDITION) (2nd ed.). IMPERIAL COLLEGE PRESS.

[3] Vasiliev, L. A. Schlieren methods. ed. A. Baruch. Israel Program for Scientific Translations,New York, 1971

[4] Miller, V. A., & Loebner, K. T. (2016, September 13). Smartphone Schllieren. Arxiv.Org. Retrieved May 18, 2022, from https://arxiv.org/pdf/1609.04298.pdf

[5] Carter, T., Seah, S., Long, B., & Drinkwater, B. (2013). UltraHaptics: multi-point mid-air haptic feedback for touch surfaces. UIST ’13: Proceedings of the 26th Annual ACM Symposium on User Interface Software and Technology, 505–514. https://doi.org/10.1145/2501988

[6] Philbert, M., J. Surget, and C. Veret. Shadowgraph and schlieren . Chap. 12 of Handbook of Flow Visualization. . Hemisphe re Pub., Washington, ed. I, pp. 189-217, 1989.
