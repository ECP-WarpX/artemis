.. _developers-dimensionality:

Dimensionality
==============

This section describes the handling of dimensionality in WarpX.

Build Options
-------------

==========  ===================
Dimensions  CMake Option
==========  ===================
**3D3V**    ``WarpX_DIMS=3``
**2D3V**    ``WarpX_DIMS=2``
**RZ**      ``WarpX_DIMS=RZ``
==========  ===================

See :ref:`building from source <install-developers>` for further details.

Defines
-------

Depending on the build variant of WarpX, the following preprocessor macros will be set:

==================  ===========  ===========  ===========
Macro               3D3V         2D3V         RZ
==================  ===========  ===========  ===========
``AMREX_SPACEDIM``  ``3``        ``2``        ``2``
``WARPX_DIM_3D``    **defined**  *undefined*  *undefined*
``WARPX_DIM_XZ``    *undefined*  **defined**  *undefined*
``WARPX_DIM_RZ``    *undefined*  *undefined*  **defined**
==================  ===========  ===========  ===========

At the same time, the following conventions will apply:

====================  ===========  ===========  ===========
**Convention**        **3D3V**     **2D3V**     **RZ**
--------------------  -----------  -----------  -----------
*Fields*
-----------------------------------------------------------
AMReX Box dimensions  ``3``         ``2``       ``2``
WarpX axis labels     ``x, y, z``   ``x, z``    ``x, z``
--------------------  -----------  -----------  -----------
*Particles*
-----------------------------------------------------------
AMReX AoS ``.pos()``  ``0, 1, 2``  ``0, 1``     ``0, 1``
WarpX position names  ``x, y, z``  ``x, z``     ``r, z``
extra SoA attribute                             ``theta``
====================  ===========  ===========  ===========

Please see the following sections for particle AoS and SoA details.

Conventions
-----------

In 2D3V, we assume that the position of a particle in ``y`` is equal to ``0``.
