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
The small organisms that fuel the aquatic food chain are in the size-range of the wavelength of light (Mie theory).
The scatter and polarization of signals from such small particles vary with the direction of observation.
Furthermore, the light-harvesting pigment complexes make use of efficient, non-linear, energy transfer mechanisms.
Documentation of anisotropic optical phenomena requires instruments capable of measuring the wavelength-dependent,
angular distribution of very dim signals.

Correlation of plankton identification and activity requires combining optical measurements with single-cell
manipulation and DNA analysis.
The sorting equipment needs to be flexible, precise, and robust so that experiments can withstand the rough conditions
of work at sea.

# The MarLux&trade; Cell Sorter

{{ resize_to_width(width=700, path="images/MarLux.jpg", alt="MarLux") }}

## Dark Field Flow Cytometry

{{ floating_image(
path="images/symmetric_signal_detection.png",
side="right",
caption="A two-tier organization allows placement of illumination and detection channels at any angle.",
title="Symmetrical Signal Detection"
) }}

The MarLux&trade;, uses a unique off-axis illumination geometry that presents particle scatter against a dark
background.
Laser reflections that bounce inside the jet and optical elements are directed away from the detector field[^1].

{{ floating_image(
path="images/side_scatter_log.png",
side="left",
caption="The MarLux detect 0.2 &micro;m particles 2-3 decades above background.",
title="Side Scatter"
) }}

Dark Field illumination allows the detection of particles as small as 1/2 the illumination wavelength
well above background noise.

## Full Spectrum Omni-Directional Flow Cytometry&trade;

{{ floating_image(
path="images/pseudo-spectrum.png",
side="right",
caption="Fluorescence spectrum of Pseudo-nitzschia multiseries.",
title="Pseudo-nitzschia Multiseries"
) }}

Since the illumination and registration optics are not in the same plane, they can be oriented at any angle[^1].
To detect color changes associated with energy transfer, the angular distribution of the polarization state
can be determined.
The instrument can also be equipped for full spectral analysis.

{{ floating_image(
path="images/angular_experiments.png",
side="left",
title="Examples of Angular Experiments"
) }}

The MarLux™ cell sorter incorporates Dark Field illumination in a circular layout.
This geometry allows multiple excitation and emission channels (up to five each) at user-selectable angles.
Because of its flexibility and low background noise, the MarLux is well suited to investigating particles whose
properties fall in the Mie scatter domain.

## Controlled Environment Sorting

Many marine organisms are adapted to an oxygen-free environment.
The MarLux&trade; allows live sorting in a controlled atmosphere.

## Real-Time Multi-Parameter Classification

{{ floating_image(
path="images/depth.png",
side="right",
title="Prochlorococcus & Synechococcus Vs Depth"
) }}

The MarLux™ Open Bus Protocol combines particle properties with environmental conditions.
Ambient light controls photo-pigment expression.
The local temperature and salinity of seawater hold information about sea currents and upwelling.

{{ floating_image(
path="images/pigment_chain_analysis.png",
side="left",
caption="Multi-laser, single-pigment action spectra can be displayed as _needles_ and as ratios of four excitation
wavelengths.",
title="Pigment Chain Analysis"
) }}

Particle sorting based on anisotropic fluorescence signatures may require a combination of multiple angular signals.
The MarCy data bus executes high-speed custom algorithms for sort classification.

Sorting on calculated properties requires consistent real-time signal processing.
The MarCy bus accepts __user programmable FPGAs__ that perform data calculations for event classification on multiple
event parameters.

---

MarCy's novel flow technology offers advantages beyond marine biology.
The company actively explores novel applications with leading scientists.
MarCy scientists have participated in field trials off the west coast of South America, over the Atacama trench,
in the Arctic and in time series near Hawaii and Bermuda.

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

[Contact us](@/contact.md) if you have a small-particle application that might benefit from the
MarLux&trade; __Omni-Directional&trade; Flow Cytometer__ approach.

[^1]: US Patent PCT/US2019/040942

<script>
function adjustSideImagePositions() {
console.log("resize");
    const sections = document.querySelectorAll('.first-entry.home-info');
    sections.forEach(body => {
        const leftImages = body.querySelectorAll('.side-image.left-image');
        const rightImages = body.querySelectorAll('.side-image.right-image');
    
        const entryRect = body.getBoundingClientRect();
        const scrollTop = window.pageYOffset || document.documentElement.scrollTop;
        const bodyTop = entryRect.top + scrollTop - 45;
    
        positionImages(leftImages, bodyTop);
        positionImages(rightImages, bodyTop);
    });
}

function positionImages(images, parentTop) {
    let maxBottom = 0;

    images.forEach(image => {
        if (window.innerWidth < 1500) {
            image.style.marginTop = "";
            return;
        }
        const entryRect = image.getBoundingClientRect();
        const scrollTop = window.pageYOffset || document.documentElement.scrollTop;
        let currentTop = entryRect.top + scrollTop;
        let newTop = currentTop;
        console.log("Max: ", maxBottom, " Current: ", newTop);
        if (currentTop < maxBottom) {
            console.log("Pushing to bottom");
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