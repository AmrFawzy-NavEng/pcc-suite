# PCC-Suite

A collection of open-source programs to analyse and visualise GNSS antenna
calibration values, and to quantify what differences between two calibrations do
to estimated geodetic parameters.

Developed at the **Institut für Erdmessung (IfE), Leibniz University Hannover**.

> **Status: release in progress.** The launcher package is archived on Zenodo and
> citable now. The individual programs follow from **16 September 2026**, to
> coincide with the presentation at Frontiers of Geodetic Science (INTERGEO 2026,
> Munich).
>
> **PCC-Suite on Zenodo:** [10.5281/zenodo.22722195](https://doi.org/10.5281/zenodo.22722195)
> (this DOI always resolves to the newest version)

## Why it exists

Phase Center Corrections (PCC) are mandatory for high-precision GNSS
positioning: the antenna height is measured to the bottom of the antenna, but
the signal is received inside it. There is no universally accepted ground truth
for these corrections. Calibrations of the same antenna differ between
facilities, between methods (anechoic chamber or field robot), and between
epochs.

Those differences are usually compared on the grid defined by the ANTEX format.
The question PCC-Suite exists to answer is what happens next:

**How do PCC differences (ΔPCC) at the grid level transfer into estimated
geodetic parameters?**

Agreement on the grid does not directly predict the impact on coordinates. A
3.1 mm difference in the vertical phase centre offset can produce well under a
millimetre of height impact once real sky geometry, elevation weighting and the
correlations with the receiver clock and troposphere are taken into account.

## The programs

| Program | What it does |
|---|---|
| **PCC-Explorer** | The core component. Propagates a ΔPCC pattern through a least-squares adjustment and reports the impact on north, east, up, receiver clock and troposphere. Works for a single station, a regional or global grid, and along a kinematic trajectory. |
| **PCC-Viewer** | Inspects PCC and PCV patterns from one ANTEX file, or the ΔPCC between two, as stereographic plots and elevation profiles. |
| **ATX-Converter** | Converts between ANTEX v1.4 and v2.0, with antenna and signal filtering. |
| **ATX-Scanner** | Scans folders of ANTEX files and builds a searchable table of which calibrations you actually hold, by antenna, radome, method, institution and ANTEX version. |
| **RINEX-Masker** | Applies an obstruction mask to a RINEX file and shows the effect in skyplots and DOP plots. The mask can be drawn by hand or generated from a hemispherical photograph. |
| **RINEX-Adapter** | Corrects and completes RINEX header records, cuts a time window, and changes the sampling interval, also for unevenly sampled files. |
| **PCC-Suite Launcher** | One window that starts whichever program you need. |

Each program is a standalone Windows executable. No installation, no Python
required. Each reports its own version and release date, and each is released
and versioned separately, so you can take only the one you need.

## Deliberately simple

PCC-Explorer isolates the effect of ΔPCC and nothing else. It applies **no
filter tuning, no outlier detection and no ambiguity resolution**. That is a
choice, not a shortcoming: it is what makes the predicted impact reproducible
from the calibration files alone, without any observations.

Compared against real PPP solutions of the same data, the predictions agree to
within 0.75 mm in every component at EPN station RANT (Germany, φ ≈ 54.8°) and
within 1.64 mm at NYAL (Ny-Ålesund, Norway, φ ≈ 79°), where the up impact grows
towards the pole. The residual difference is explained by the processing that
real PPP does and this tool deliberately does not.

## Repositories

Each program has its own repository, so you can take only the one you need.

| Program | Repository |
|---|---|
| PCC-Explorer | [J-kroeger/pcc-explorer](https://github.com/J-kroeger/pcc-explorer) |
| PCC-Viewer | [pcc-viewer](https://github.com/AmrFawzy-NavEng/pcc-viewer) |
| ATX-Converter | [atx-converter](https://github.com/AmrFawzy-NavEng/atx-converter) |
| ATX-Scanner | [atx-scanner](https://github.com/AmrFawzy-NavEng/atx-scanner) |
| RINEX-Masker | [rinex-masker](https://github.com/AmrFawzy-NavEng/rinex-masker) |
| RINEX-Adapter | [rinex-adapter](https://github.com/AmrFawzy-NavEng/rinex-adapter) |

Archived releases and DOIs are gathered in the Zenodo community
[Open Source Software Packages for GNSS Data Processing](https://zenodo.org/communities/gnss-open-source-solutions).

## Licence

GNU General Public License v3.0 or later. Free to use, share and modify. See
[LICENSE](LICENSE).

## Citation

The method and its validation are described in:

> Kröger, J., Kersten, T. & Schön, S. (2026). PCC-Explorer: an open-source
> software tool to assess the impact of GNSS antenna phase center corrections on
> geodetic parameters. *GPS Solutions* **30**, 93.
> [doi.org/10.1007/s10291-026-02056-2](https://doi.org/10.1007/s10291-026-02056-2)

## Stay informed

Release announcements, and warnings when an external data source moves, go to
the institute software mailing list:

```
SOFTWARE-IFE@LISTSERV.UNI-HANNOVER.DE
```

Each program offers to subscribe you on first start. You can decline, and you
can ask not to be reminded again.

## Contact

**Dr.-Ing. Johannes Kröger**
Institut für Erdmessung (IfE), Leibniz Universität Hannover
Schneiderberg 50, D-30167 Hannover

Email: [kroeger@ife.uni-hannover.de](mailto:kroeger@ife.uni-hannover.de)
Web: [www.ife.uni-hannover.de](https://www.ife.uni-hannover.de)
