+++
title = "Marine Cytometry Inc."
+++

{{ floating_image(
path="images/lambda-reflection.jpg",
side="right",
title="&lambda;-dependant Reflection from Small Spheres",
fullOnly=true,
scale=0.75
) }}

{{ floating_image(
path="images/raleigh-scatter.jpg",
side="left",
title="Raleigh and Small Particle Scatter",
fullOnly=true,
scale=0.75
) }}

{{ floating_image(
path="images/sun_refraction.jpg",
alt="Sunrise Refraction",
side="left",
title="Sunrise Refraction",
fullOnly=true,
scale=0.75
) }}

Marine Cytometry Inc. builds analytical flow cytometers for the study of phytoplankton communities.
The organisms at the base of the aquatic food chain are very small: about the size of the wavelength of light.
Mie theory predicts that their scatter and polarization vary with the direction of observation and consequently cannot
be expressed in a single value.
The energy harvesting the pigment complexes make use of non-linear energy transfer mechanisms.
Documentation of anisotropic optical phenomena requires flow instruments that measure spectral and polarization signals
at adjustable angles.

Correlating plankton identity with biological activity requires combining optical measurements with single-cell
manipulation and DNA analysis.
The sorting equipment needs to be flexible, accurate, robust, and PCR-clean, so that experiments can withstand the
rough conditions of work at sea.

# The MarLux&trade; Cell Sorter

{{ resize_to_width(width=700, path="images/MarLux.jpg", alt="MarLux") }}

## Dark Field Flow Cytometry

{{ floating_image(
path="images/symmetric_signal_detection.png",
side="right",
caption="A two-tier organization allows placement of illumination and detection channels at any angle.",
title="Symmetrical Signal Detection"
) }}

MarCy's cytometers utilize a unique off-axis illumination geometry that presents particle scatter against a dark
background.
Laser reflections that bounce inside the jet and optical elements are directed away from the detector field[^1].

{{ floating_image(
path="images/side_scatter_log.png",
side="left",
caption="The MarLux detect 0.2 &micro;m particles 2-3 decades above background.",
title="Side Scatter"
) }}

Dark Field illumination allows the noise-free detection of particles as small as 1/2 the illumination wavelength.

{{ floating_image(
path="images/pinhole_no_bar.png",
side="center",
caption="Raw images without scatter bar or chromatic filters at &lambda; = 450nm",
title="Raw Images"
) }}

## Full Spectrum Omni-Directional Flow Cytometry&trade;

{{ floating_image(
path="images/pseudo-spectrum.png",
side="right",
caption="Fluorescence spectrum of Pseudo-nitzschia multiseries.",
title="Pseudo-nitzschia Multiseries"
) }}

Since the illumination and registration optics are in different planes, they can be oriented at any angle[^1].
In order to detect color-changes associated with energy transfer, the angular distribution of the polarization state
can be determined.
The instrument can also be equipped for full spectrum analysis.

{{ floating_image(
path="images/angular_experiments.png",
side="left",
title="Examples of Angular Experiments"
) }}

The MarLux&trade; cell sorter incorporates Dark Field illumination in a circular layout.
This geometry allows multiple excitation and emission channels (up to 5 each) at user-selectable angles.
Because of its flexibility and low background noise, the MarLux is well suited to investigate particles whose properties
fall in the Mie scatter domain.

## Controlled Environment Sorting

Many marine organisms are adapted to a low oxygen environment.
MarCy's instruments allow live sorting in a controlled atmosphere.

## Real-Time Multi-Parameter Classification

{{ floating_image(
path="images/depth.png",
side="right",
title="Prochlorococcus & Synechococcus Vs Depth"
) }}

The MarLux&trade; Open Bus Protocol combines particle properties with environmental conditions.
Photo-pigment expression is controlled by ambient light.
The local temperature and salinity of seawater hold information about sea currents and upwelling.

{{ floating_image(
path="images/pigment_chain_analysis.png",
side="left",
caption="Multi-laser, single-pigment action spectra can be displayed as _needles_ and as ratios of four excitation
wavelengths.",
title="Pigment Chain Analysis"
) }}

Particle sorting based on anisotropic fluorescence signatures may require a combination of multiple angular signals.
The MarCy data bus executes high-speed custom algorithms in real-time.

{{ floating_image(
path="images/marcy_bus.png",
side="right",
caption="MarCy bus with user extensions",
title="MarCy Bus"
) }}

Sorting on calculated properties requires consistent real-time signal processing.
The MarCy bus accepts __user programmable FPGAs__ that perform data calculations for event classification on multiple
event parameters.

---

MarCy's novel flow technology offers advantages in small particle analysis beyond marine biology. 
The company actively explores novel applications with leading scientists. 
MarCy scientists have participated in field trials off the west coast of South America, over the Atacama trench, in the
Arctic and in time series near Hawaii and Bermuda.

{{ gallery(images=[
"/images/sea/sea_0.jpg",
"/images/sea/sea_1.jpg",
"/images/sea/sea_2.jpg",
"/images/sea/sea_3.jpg",
"/images/sea/sea_4.png",
"/images/sea/sea_5.png",
"/images/sea/sea_6.jpg",
"/images/sea/sea_7.png"
]) }}

[Contact us](@/contact.md) if you have a small-particle application that might benefit from the MarLux™ Omni-Directional™ Flow 
cytometry technology.

[^1]: US Patent PCT/US2019/040942

<script>
function adjustSideImagePositions() {
console.log("resize");
    const sections = document.querySelectorAll('.first-entry.home-info');
    sections.forEach(body => {
        const leftImages = body.querySelectorAll('.side-image.left-image');
        const rightImages = body.querySelectorAll('.side-image.right-image');
    
        positionImages(leftImages);
        positionImages(rightImages);
    });
}

function positionImages(images) {
    let maxBottom = Number.NEGATIVE_INFINITY;

    images.forEach(image => {
        if (window.innerWidth < 1500) {
            image.style.marginTop = "";
            return;
        }
        const entryRect = image.getBoundingClientRect();
        let currentTop = entryRect.top;
        let newTop = currentTop;
        if (currentTop < maxBottom) {
            newTop = maxBottom;
            image.style.marginTop = (newTop - currentTop) + 'px';
        }

        maxBottom = newTop + entryRect.height;
    });
}

window.addEventListener('load', adjustSideImagePositions);
window.addEventListener('resize', () => {
    // Simple debounce
    clearTimeout(window.resizeAdjustTimer);
    window.resizeAdjustTimer = setTimeout(adjustSideImagePositions, 250);
});
</script>