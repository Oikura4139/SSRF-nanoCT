# Automatic Feedback System for X-ray Flux at BL08U1A Soft X-ray Spectromicroscopy Beamline of Shanghai Synchrotron Radiation Facility

## sec:preamble preamble
_Pages 1-1_

Citation: Zhang, C.; Liu, H.; Wang,
C.; Guo, Z.; Zhang, X.; Xu, Z.; Zhen,
X.; Wang, Y.; Tai, R. Automatic
Feedback System for X-ray Flux at
BL08U1A Soft X-ray
Spectromicroscopy Beamline of
Shanghai Synchrotron Radiation
Facility. Appl. Sci. 2023, 13, 5456.
https://doi.org/10.3390/
app13095456
Academic Editor: Koen Janssens
Received: 23 March 2023
Revised: 23 April 2023
Accepted: 25 April 2023
Published: 27 April 2023
Copyright:
© 2023 by the authors.
Licensee MDPI, Basel, Switzerland.
This article is an open access article
distributed
under
the
terms
and
conditions of the Creative Commons
Attribution (CC BY) license (https://
creativecommons.org/licenses/by/
4.0/).
applied
sciences
Article
Automatic Feedback System for X-ray Flux at BL08U1A Soft
X-ray Spectromicroscopy Beamline of Shanghai Synchrotron
Radiation Facility
Chi Zhang 1,2,3
, Haigang Liu 1,2,*, Chunpeng Wang 1,2,*
, Zhi Guo 1,2, Xiangzhi Zhang 1,2, Zijian Xu 1,2
Xiangjun Zhen 1,2, Yong Wang 1,2 and Renzhong Tai 1,2,3,*
Shanghai Synchrotron Radiation Facility, Shanghai Advanced Research Institute,
Chinese Academy of Sciences, Shanghai 201210, China
Shanghai Institute of Applied Physics, Chinese Academy of Sciences, Shanghai 201204, China
School of Physical Science and Technology, ShanghaiTech University, Shanghai 201210, China
Correspondence: liuhg@sari.ac.cn (H.L.); wangcp@sari.ac.cn (C.W.); tairz@sari.ac.cn (R.T.)
Abstract: An online automatic feedback system has been successfully installed and commissioned at
the BL08U1A Soft X-ray Spectromicroscopy Beamline of Shanghai Synchrotron Radiation Facility,
which can monitor the incident X-ray beam in real time by measuring the blade-edge signals of the exit
slit and automatically adjust the elliptical cylindrical mirror parameters to achieve beam calibration
and maintain the optimal X-ray flux of the sample. This work provides a comprehensive description
of the hardware composition, system implementation, feedback logic, function and software design,
system optimization and commission, as well as the online experimental results supported by the
system. The experimental results demonstrated that the online automatic feedback system is capable
of effectively maintaining the optimal X-ray beam flux for X-ray absorption spectroscopy experiments.
Its success can provide valuable technique assistance for the design, construction and optimization of
similar systems at various beamlines in synchrotron sources in the future.
Keywords: synchrotron radiation; beamline automation; X-ray absorption spectroscopy; online
feedback

## sec:introduction 1. Introduction
_Pages 1-3_

The Shanghai Synchrotron Radiation Facility (SSRF) is a state-of-the-art third-generation
synchrotron radiation light source built in 2009. It is composed of a 150 MeV electron linear
accelerator, a booster to increase the electron energy to 3.5 GeV, a 3.5 GeV electron storage
ring, and dozens of beamlines and end stations that cover multiple disciplines. In 2016,
the SSRF launched the largest follow-up beamline construction project, the SSRF Phase-II
Beamline Project, which is anticipated to be completed by July 2023. In addition to the
three beamlines currently being constructed with investment from Sinopec, by 2025, the
SSRF will have 35 beamlines and 50 end stations in operation, which will greatly expand
the experimental capacity of the SSRF, making the resolution of time, space, energy and
momentum in the SSRF almost reach the limit of the third-generation synchrotron radiation
light source [1].
The ability to provide high-quality X-ray is the greatest irreplaceable advantage that
synchrotron radiation light sources offer. The benefits of the synchrotron radiation X-ray
light source include a high brightness, large and continuously tunable energy span, high
collimation, high polarization, narrow pulse, and so on. For most scientific research using
synchrotron radiation, a high X-ray flux is one of the most significant advantages among
all the aforementioned benefits, as it leads to a better resolution in terms of space, energy,
and time, as well as a higher experimental efficiency. Additionally, it serves as the most
representative indicator for the development of diffraction-limited storage ring (DLSR) light
Appl. Sci. 2023, 13, 5456. https://doi.org/10.3390/app13095456
https://www.mdpi.com/journal/applsci
Appl. Sci. 2023, 13, 5456
2 of 13
sources and free electron lasers (FEL). Similarly, maintaining optimal X-ray flux is critical
for beamline operation and achieving high-quality experimental results in synchrotron light
sources. However, when the beamline operates continuously throughout the day to support
different experiments, a large number of experimental conditions change, which leads to
varying degrees of disruption to the final X-ray flux at the experimental end station. For
example, different users and experiments may need the beamline mirror position, undulator
or other insertion device (ID) gap value, or monochromator and grating parameters to be
adjusted in order to achieve the requested X-ray energy, which may cause a decrease in
the light flux. For example, the energy range of the Fe element XAFS is about 690–740 eV,
and the X-ray flux at 735 eV is about 22% lower than the maximum flux at 690 eV based on
real experimental measurements at the BL08U1A beamline of the SSRF. Furthermore, an
upgrade in the insertion devices, an unstable electron beam orbit, and beam injection in the
storage ring can also impact the beam flux [2]. Since most synchrotron sources operate 24 h
a day, the thermal expansion and contraction of optical components and the 24 h day/night
temperature cycle [3] may cause the photon beams to drift. Sometimes, due to an unstable
beam current, operators may need to enlarge the exit slit to achieve a high X-ray flux in
imaging experiments, despite the cost of reduced spatial resolution. Therefore, it is crucial
to maintain optimal X-ray flux before and during the experiments automatically.
To automatically align the beam position and maintain maximum light flux, plenty
of beamlines have developed stabilization systems, including orbit correction and optical
correction systems. Orbit correction systems [4–8] typically use beam position monitors
(BPMs) [9] and corrector magnets to constrain the beam to its working position, while
optical correction systems usually use vertical and horizontal plane mirrors, monochro-
mators [10,11] and detectors to stabilize and maximize light flux. Both orbit and optical
correction systems can be implemented as feed forwards (FFs) or feedbacks (FBs). FF
correction depends on the physics model of the beamlines or on records of the relationship
between the beam property and beamline settings for every ID gap [12]. The National
Institute of General Medical Sciences and the National Cancer Institute (GM/CA) MX
beamlines at the Advanced Photon Source (APS) perform vertical and horizontal scans to
recenter the beam under certain conditions [13]. However, such a record takes a long time
to measure and cannot be frequently recalibrated after machine drift due to the limited
machine study time in light sources. The deviation of FF algorithms increases over time
and requires a feedback system to compensate for such deviations. The micro-focusing
frontier macromolecular crystallography (FMX) beamline at the National Synchrotron Light
Source II (NSLS-II) implements three feedback loops for beam position correction [3]. Some
automatic tasks have been considered at the X-ray absorption spectrum (XAS) beamline
of the Karlsruhe Institute of Technology (KIT) synchrotron [14]. The macromolecular
crystallography beamline (MX2) at the Australian Synchrotron uses a neodymium-doped
yttrium aluminum garnet (YAG) crystal and a CCD camera to record the beam and move
the focusing mirrors as feedback [15]. Although these feedback systems are widely used,
few implementation details, such as the controlled devices, algorithms and feedback results,
have been provided.
In this paper, we present a fully automatic online feedback system for X-ray flux
optimization before and during experiments in the SSRF BL08U1A beamline. The beamline
provides photon beams ranging from 200 eV to 2000 eV, with energy resolutions of 16,000 at
244 eV and 12,700 at 401 eV when the Slit 2 size is set to 50 µm (horizontal) and 20 µm
(vertical), respectively. The photon flux downstream to the exit slit is about 5 × 1011 phs/s
at 244 eV and E/∆E = 6440, with a Slit 2 size of 50µm (horizontal) and 50 µm (vertical). The
decrease in photon flux might be attributed to the photon energy adjustment, the EPU gap
variation, and the mirror deformation that originates from the heterogeneity of the heating
load distribution. In XAS experiments and long-time imaging experiments, beamline
operators have to adjust the mirror positions and the exit slit size manually and frequently
in order to obtain a higher X-ray flux, which favors improvements in the experimental
quality. Based on this feedback system, the position of the elliptical cylindrical mirror can
Appl. Sci. 2023, 13, 5456
3 of 13
be adjusted automatically in the horizontal direction by simultaneously calculating the
feedback signal of the blade-edge signals on the exit slit, thus contributing to maintaining
the stability of photon flux. The hardware composition, system implementation, feedback
logic, function and software design, system optimization and commission, as well as the
online experimental results supported by the system, will be described in detail. The results
of the experiments on the XAS conducted at the BL08U1A beamline of the SSRF show that
the system meets the demand of the stable and automatic light flux adjustment.

## sec:materials-and-methods 2. Materials and Methods
_Pages 3-9_

2.1. System Design
2.1.1. Layout of the BL08U1A Beamline at the SSRF
The BL08U1A beamline at the SSRF is a soft X-ray spectromicroscopy beamline with a
250–2000 eV energy range [16,17], as shown in Figure 1. An elliptically polarized undulator
(EPU) was used to produce soft X-ray photons. Slit 1 was set at a distance of 20 m
downstream from the EPU to ensure that the acceptance angle was within ±0.04 mrad
in both horizontal and vertical directions. Then, an elliptical cylindrical mirror (M1), set
at a distance of 30 m downstream from the EPU, was used to collimate the photon beam
and suppress high-order harmonics using a water-cooling scheme that absorbed the heat
load. The plane grating monochromator (PGM) set at 32 m consists of two Au-coated
gratings including an 800 line/mm for 250–750 eV and a 1200 line/mm for 275–2000 eV.
The last optical element, an elliptical cylindrical mirror (M2), was used to focus the photon
beam both in the horizontal and vertical directions at Slit 2. The BL08U1A beamline began
operating in 2009 with a scanning transmission X-ray microscopy (STXM) end station (End
station 1 in Figure 1). An independent in situ spectroscopic end station was first installed in
2014 and then updated in 2018 [18], and a state-of-the-art ptychography–STXM end station
(End station 2 in Figure 1) was installed in 2019. These three end stations have proven to
be extremely useful for studies in environmental science [19,20], physics [21], chemical,
materials, and energy sciences [22,23].
Figure 1. Layout of the BL08U1A beamline at the SSRF. The M1 elliptical cylindrical mirror collimates
the X-ray and suppresses high-order harmonics. The M2 elliptical cylindrical mirror focuses the
X-ray in both directions through Slit 2. The tunable X-ray energy is 200–2000 eV. A spectroscopic end
station and two STXM end stations are located downstream of the beamline.
The BL08U1A beamline is capable of a variety of experimental methods, including
imaging methods such as STXM [24,25], nano-CT [26–28], and ptychography [29,30], as
well as XAS methods such as total electron yield (TEY), X-ray Magnetic Circular Dichroism
(XMCD), X-ray Magnetic Linear Dichroism (XMLD), and X-ray-Excited Optical Lumines-
cence (XEOL) [31,32]. In order to obtain satisfactory experimental results, XAS methods
require the incident X-ray flux to be measured for data normalization, and all XAS and
imaging methods require a high and stable incident X-ray light flux to improve the signal-to-
noise ratio. BL08U1A beamline operators typically need to manually adjust the M2 position
before the experiment to achieve optimal flux. However, it is impossible to observe the
flux variation in real time and make corrections during the experiment, which may lead
to a decrease in the experimental data quality and even lead to experimental failure in
long-time imaging methods. Therefore, it is imperative to develop an automatic feedback
Appl. Sci. 2023, 13, 5456
4 of 13
system that aligns the beamline and maintains the optimal X-ray light flux in order to
achieve enhanced experimental efficiency and results.
2.1.2. Hardware Composition
The hardware of the automatic feedback system mainly includes the elliptical cylindri-
cal mirror M2 and the four-blade exit slit, Slit 2, of the beamline, a current-voltage (I–V)
convertor developed by the SSRF, a MOXA ioLogik E2240 controller, a picoammeter, a
gold mesh in the spectroscopic end station, and a photodiode (PD) detector in the STXM
end station.
The exit slit, Slit 2, of the beamline acts as a secondary light source, which is a critical
device used to control the X-ray beam energy resolution and coherence in the downstream
optical path to the end stations. Composed of four independently moving blades, Slit 2
can adjust the size and shape of the slit, as shown in Figure 2. From the beam incident
direction, the left and right blades are installed in front of the up and down blades. The
monochromator grating, placed horizontally at the upstream of the beamline, generates
a vertical-strip-shaped X-ray beam that illuminates Slit 2, as shown in the embedded
diagram in Figure 2. The M2 mirror placed vertically causes the beam spot on Slit 2 to
move horizontally. Since the size of Slit 2 is usually set to tens of micrometers during
experiments, and the current signal of the blade is proportional to the area illuminated
by the incident X-ray, the horizontal blade edge current signals are usually bigger than
the vertical blade edge currents. To achieve high precision readout, an I–V convertor with
8 channels made by the SSRF control group is installed to convert current signals to voltage
signals. A MOXA ioLogik E2240 controller is connected for signal acquisition and range
switching. When the incident X-ray beam center deviates from the center of Slit 2, the left
and right blade edge current signals are different, which can be used as a reference index
for the automatic feedback system.
Figure 2. Layout of hardware connection by the local area network (LAN). The monochromatized
X-ray was horizontally focused to the exit slit (Slit 2) by an elliptical cylindrical mirror. The four blade
signals of Slit 2 were read out by an I–V convertor. The photon flux after Slit 2 was detected by a gold
mesh and PD detector, and the signals were read out by a picoammeter. The signals of M2, Slit 2,
gold mesh and PD are all connected into LAN and can be read out for control.
The gold mesh installed in the spectroscopic end station and the PD installed in the
STXM end station are used to directly measure the intensity of X-ray beam. The signals
from the gold mesh and PD can be read out using a picoammeter.
All digital signals and control access of the hardware are connected and controlled by
the control software through a local area network (LAN), as shown in Figure 2. The control
software has access to the converted Slit 2 blade edge voltage signals, gold mesh current
signal, PD current signal, and motor signals of M2. In addition, the software controls the
movement of M2 position based on a suitable logic criterion to maintain the optimal X-ray
flux of the sample.
Appl. Sci. 2023, 13, 5456
5 of 13
2.1.3. Feedback Logic
The automatic feedback system is optimized under the condition that all beamline
devices on the optical path are optically aligned and the EPU gap and PGM angle are
selected. Figure 3 shows the change in the four blade-edge voltage signals along with
the position changes of M2, where the incident X-ray energy is 920 eV and the Slit 2 size
is 50 µm × 50 µm. SL, SR, SU and SD represent the left, right, up, and down blade-edge
signals. The change in the horizontal signals is an order of magnitude larger than the
change in the vertical signals, indicating that the deviation in the light spot in the horizontal
direction is much larger than that in the vertical direction. Therefore, only horizontal
deviation is considered in the feedback system, and the horizontal blade-edge signals are
used to assess the position of the X-ray light flux in the downstream optical path of Slit 2.
Figure 3. The measurement results of the Slit 2 blade-edge signals with M2 position changes at
920 eV. SL, SR, SU and SD represent the left, right, up and down blade-edge signals, respectively. The
horizontal axis represents the M2 position, with a minimum moving step size of 200 nm. The left
coordinate system is for SL and SR, while the right coordinate system is for SU and SD. The horizontal
blades are illuminated over a larger range than the vertical blades, resulting in the horizontal blade
signals that is nearly 10 times stronger than the vertical blade signals.
Figure 4 illustrates that the gold mesh current signal reaches its optimal value along
with the change of the position of M2. When the M2 position parameter is smaller, the right
blade-edge signal is larger than the left, indicating that the X-ray beam at Slit 2 is deviated
to the right direction. The difference between the left and right blade-edge signal decreases
as the M2 position increases. At a specific M2 position value, the left and right blade-edge
signals become the same, and the gold mesh signal almost reaches its maximum value.
Therefore, the first logic feedback criterion can be defined as follows:
SRL = SR −SL
SR + SL
(1)
If SRL is positive, it needs to increase the M2 position parameter and reduce the signal
difference between the left and right blade edges. Conversely, if SRL is negative, it needs to
reduce the M2 position parameter and reduce the signal difference between the left and
right blade edges.
Appl. Sci. 2023, 13, 5456
6 of 13
Figure 4. The measurement results of the left and right blade voltage signals and gold mesh current
signal I0, along with M2 position changes at 920 eV. When the signals of the left and right blade are
equal, the corresponding gold mesh signal is almost at the maximum value.
2.1.4. Function Design and Software Design
The motor position of M2, and the current of the gold mesh and PD can be accessed
through the Experimental Physics and Industrial Control System (EPICS) [33]. EPICS is an
open-source, distributed software framework that is widely used in the control of large-
scale scientific facilities in order to access and control devices through networks. EPICS
provides a standardized, extensible interface that enables different types of devices and
control systems to communicate and work together, and it also provides a rich set of tools
and libraries, such as Channel Access, Database Access, Alarm Handler, Archive Engine,
etc., to facilitate development and management. Voltage signals of SL and SR, collected by
Moxa ioLogik E2240 controller, can be read out through a MXIO library provided by Moxa.
The software of the automatic feedback system was developed in Browser/Server (B/S)
architecture with Flask (https://flask.palletsprojects.com, accessed on 30 December 2022)
and React (https://reactjs.org, accessed on 30 December 2022). Flask is a micro web
framework written in Python. It is designed to be lightweight and easy to use, making
it a popular choice for building web applications and APIs. Flask provides a simple and
flexible interface for developers to create web applications, with features such as URL
routing, template rendering, and support for extensions. React is an open-source JavaScript
library for building user interfaces. It is designed to be declarative and efficient, allowing
developers to build complex user interfaces with ease. React uses a virtual DOM (document
object model) to optimize the rendering performance, and supports server-side rendering
and mobile development.
As the control software for the spectroscopic end station and STXM end stations are
separated on different computers, the B/S architecture is more convenient for operating
across multiple computers and control systems. Users can easily download the data of all
signals in CSV format from the browser for further research. Additionally, all signals will
be recorded in seconds and stored in a local SQLite database after the server starts. This
ensures that all data are safely stored and easily accessible for future analysis.
During the implementation of the feedback logic, a threshold value limitation was
added to prevent M2 from vibrating around its optimal position and reducing the motor
return difference. Additionally, an offset for SRL was added as a calibration of light flux
since the signal of the mesh grid may not be accurate based on the incident position at the
mesh structure. The details of these two improvements and some tests are discussed in
Section 2.2. In order to avoid errors in the operation of the automatic dimming program,
Appl. Sci. 2023, 13, 5456
7 of 13
an alarm signal output is set in the program. An error signal is activated and sent to the
imaging or XAS end stations when the SV exceeds 30%.
Figure 5 illustrates the procedure of the tunning loop. The user can set the step of the
M2 motor, offset and V0 in the browser user interface and operate the feedback system.
When the system is turned on, a feedback request with the parameters of the step, offset and
V0 is sent to the server. The server then immediately reads out all signals and checks the
threshold value limitation. If the SV is greater than V0, M2 must move one step accordingly
and finishes one feedback request. As long as the system is on, this procedure is repeated
every three seconds, taking into consideration the motor’s moving speed and signal latency.
Figure 5. The logic of each tunning procedure. When the server gets a tunning request with threshold
and offset values, it will try to read out SL, SR, SU and SD and calculate Sv. If Sv is bigger than the
threshold, the M2 motor will move one step (200 nm); otherwise, it will jump directly to the end of
this tunning and waiting for the next tunning call.
2.2. System Optimization and Commissioning
2.2.1. X-ray Light Flux Calibration
The maximum X-ray beam flux in the downstream optical path of Slit 2 is not an exact
correspondence with the minimum signal difference between the left and right blade-edge
voltage signals, as shown in Figure 4. This is because the signal of the gold mesh may not
accurately represent the X-ray beam flux at the sample position, depending on its mesh
structure and the illuminated position. Therefore, a PD detector was installed in the STXM
end station, which directly measures the X-ray intensity; this was used to determine the
difference between the maximum flux and the flux when SRL = 0, and to calibrate SRL
through offset if the difference was big enough. Several calibration experiments were
performed at energies of 540 eV (shown in Figure 6), 700 eV and 920 eV, and the offset
values of SRL for the maximum PD light flux were calculated as −2.677%, −9.356%, and
−13.5%, respectively. When the offset was set to zero, the light flux values of SRL = 0 at
540 eV, 700 eV and 920 eV were 99.12%, 96.88%, and 98.50% of the maximum PD flux,
respectively. The maximum light flux deviation was smaller than 3%. Therefore, although
the offset may be bigger than 10%, the flux of offset = 0 was almost the max flux on the
sample, and the offset was to zero in the automatic feedback procedure.
Appl. Sci. 2023, 13, 5456
8 of 13
Figure 6. Calibrate slit signals using PD at 540 eV. The left dotted vertical line marks the first
M2 position of SL = SR. The right dashed vertical line marks the second M2 position of the maximum
PD value. For the second position, SRL is calculated to be −2.677%. However, the light flux of the
first position is 99.12% of the second position. Considering that the M2 stepping motor with a 200 nm
minimum step size cannot distinguish between the two positions, the difference in the two light
fluxes can be ignored; thus, the offset value is set to 0 in practical applications.
2.2.2. Threshold Value Limitation
At the BL08U1A beamline of the SSRF, M2 is the main beamline mirror that affects the
beam center during the Slit 2 during experiment, which is driven by a step motor with a
minimum moving precision of 200 nm. Additionally, the return difference of the M2 motor
also needs to be considered during it movement. In order to prevent the M2 position from
vibrating around the optimal position due to return difference, a threshold value limitation
is defined as follows:
SV = abs
SR −SL
SR + SL
+ o f f set
(2)
where the offset is a correcting value according to the gold mesh optimal signal value.
A suitable threshold value V0, which measures the deviation in the slight signals due
to M2 movement, should be tested so that the feedback system is only activated when
SV > V0.
Figure 7 shows the change in the position of SRL as the M2 moves in steps of 200 nm at
an incident X-ray energy of 920 eV. The (SR −SL)/(SR + SL) is collected with the M2 change
before the experiment and these data are fitted with a straight line (see Figure 7). The slope
of the fitted straight line represents the percentage change of (SR −SL)/(SR + SL) after
1000 nm, and multiplying the slope by 0.2 gives the percent change of (SR −SL)/(SR + SL)
after 200 nm. It can be observed that the relative change in the position of SRL in each motor
step is approximately 0.0475; this is obtained by calculating the slope in the central linear
area around the optimal M2 position. For the BL08U1A beamline, the incident X-ray energy
ranges from 250 eV to 2000 eV. Therefore, we systematically tested the entire energy range
and calculated the threshold values, which are listed in Table 1. In real experiments, V0 is
set to 0.05 for simplicity and the automatic feedback procedure works very well.
Appl. Sci. 2023, 13, 5456
9 of 13
Figure 7. The measurement result of the left and right blade-edge signals, along with the M2 position
changes at 920 eV. The minimum moving precision of the M2 motor is 200 nm. The experimental data
were fitted with a straight line, and the linear area slope shows the position changes of SRL changes
as M2 moves per 200 nm. It is found that the threshold value is less than 0.05.
Table 1. The minimum threshold value for different incident X-ray energy.
Energy (eV)
0.0399
0.0467
0.0353
0.0475
0.0453
0.0431
0.0448

## sec:results 3. Results
_Pages 9-11_

3.1. Tunning for Optimal Light Flux
The browser user interface for the online automatic feedback system is shown in
Figure 8. The “Beamline Monitor” panel in the top left corner provides current readings
of E (energy), M2, SL, SR, SU, SD, SV and I0. The “Config” panel in the bottom-left corner
has inputs of M2 step, offset and V0, as well as a running button and export data function
components. The main part of the interface on the right side is the chart area, which
displays all signals with a maximum of 12 h of data. Each chart has a slider on the x-axis
for observing smaller time scales. The signals in the chart area and in the Beamline Monitor
panel are updated by the server every second.
The automatic feedback system was tested for approximately 15 min via an energy
scan from 690 eV to 730 eV. Various parameters, including an M2 step of 0.2 um, an offset
of 0, and a threshold of 0.05, were set in the Config panel and the feedback system was
started by pressing the start running button. Energy changes were recorded in the chart of
E, along with the M2 position in the chart of M2, and the SRL was calculated in the chart of
(SR −SL)/(SR + SL). During the energy change, SRL gradually decreased to −0.05 when
M2 started moving step by step to make SRL larger. The automatic feedback procedure was
thus proven to work well since SRL was maintained between ±0.05 in the whole test.
3.2. Tunning for XAS
XAS is a widely used experimental technique that is performed at synchrotron ra-
diation facilities for research in material science, chemistry, and biology [34]. The XAS
experiment uses TEY measurements, which measure the absorption of X-rays by consider-
ing a sample as a function of energy. During the experiment, along with the incident energy
changes, the intensity of the X-ray before and after the sample are recorded and normalized
to obtain the absorption coefficient. The absorption spectrum provides information about
the electronic and atomic structure of the sample, including oxidation state, coordination
number, and bond length.
Appl. Sci. 2023, 13, 5456
10 of 13
Figure 8. Operation interface of the online automatic feedback system. Beamline Monitor panel
displays energy, M2 position, SL, SR, SU, SD, SV and I0; Config Panel is used to input M2 step, offset,
V0 configuration with a running button and data export components; the Chart Area on the right
side displays all signals with a maximum time span of 12 h.
The normalized absorption spectrums of an Fe sample holder with and without
the online automatic feedback system are shown in Figure 9. The intensity of the X-ray
before the sample position during the experiment, which is collected by the gold mesh, is
displayed at the top right of Figure 9.
Figure 9. XAS experiments using TEY measurement in the absence and presence of the feedback
system. The normalized absorption coefficient has a higher signal quality when the feedback system
is on. The top right figure shows that the X-ray flux with the feedback system on drops much slower
and smoother.
Data acquisition for each spectrum takes about 10 min. Without the feedback system,
the intensity of the feedback from the data (top right subfigure of Figure 9) drops quickly
Appl. Sci. 2023, 13, 5456
11 of 13
during the energy scan. However, with the feedback system, the intensity drops much
slower and smoother. The normalized absorption coefficient in the feedback on the spec-
trum is also consistently higher than the feedback from the data across the entire energy
range with a higher signal quality. We conducted signal-to-noise ratio (SNR) calculations
on the normalized data within the energy range of 724 eV to 730 eV, where the feedback
system had optimized the M2 position. The SNR for the feedback from the data is 55.390 dB,
whereas the SNR for the feedback from the data is 57.351 dB, resulting in an improvement
of nearly 2 dB in the SNR. These results demonstrate the effectiveness of the feedback
system in improving the quality of the XAS data by maintaining a stable X-ray intensity
during the experiment. The improved data quality can lead to more accurate and reliable
results, making it an essential tool for XAS experiments.

## sec:discussion 4. Discussion
_Pages 11-12_

The online automatic feedback system has been proven to be effective in ensuring the
quality of the XAS experiments carried out under the optimal X-ray flux for an extended
period of time at the BL08U1A beamline of the SSRF. This has been achieved via the online
monitoring of the four blade-edge voltage signals of Slit 2 of the beamline and by adjusting
the M2 motor in real-time. The feedback system significantly improves the data quality and
does not interrupt user experiments. Therefore, it has been running online at the BL08U1A
beamline in order to assist users. For the special case of BL08U1A, M2 is the core optical
device with the highest adjustment frequency during the beamline operation and user
experiments. The optimization logic is also relatively simple and clear.
However, for other beamlines, the optical devices and control parameters that affect
the maximum X-ray flux may be more complex and diverse, resulting in an oversized
parameter optimization space. Additionally, if the optical devices and control parameters
are coupled with each other, the development of an automatic feedback system becomes
ever more challenging, but also more valuable. The development concept of such a system
should be consistent with that of this work, which aims to include all devices and control
parameters that affect the X-ray flux in a unified framework, and rely on the experience of
senior beamline scientists or artificial intelligence/machine learning algorithms to quickly
optimize the system in a large parameter space. Moreover, it should be noted that arti-
ficial intelligence methods, which are represented by deep neural networks, have great
applicative potential regarding the online automatic optimization of complex beamlines.
We believe that in the next few years, breakthroughs will continue to emerge.
The detailed demonstrations of hardware composition, system implementation, feed-
back logic, function and software design, system optimization and commission presented
in this work will be beneficial for similar studies on various beamlines in synchrotron
sources in the future.
Author Contributions: Conceptualization, H.L., C.W. and X.Z. (Xiangzhi Zhang); Data curation, C.Z.
and Z.X.; Formal analysis, C.Z. and H.L.; Funding acquisition, H.L. and C.W.; Investigation, Z.G.;
Methodology, C.Z. and H.L.; Project administration, R.T.; Resources, X.Z. (Xiangzhi Zhang) and X.Z.
(Xiangjun Zhen); Software, C.Z.; Supervision, Y.W. and R.T.; Validation, Z.G.; Visualization, H.L.;
Writing—original draft, C.Z.; Writing—review & editing, C.W. All authors have read and agreed to
the published version of the manuscript.
Funding: This research was funded by the National Key Research and Development Program
(Grant nos. 2022YFA1603703, 2021YFA1600802), the National Natural Science Foundation (Grant nos.
12175297, U2032126), the Youth Innovation Promotion Association, CAS (Grant no. 2022290).
Institutional Review Board Statement: Not applicable.
Informed Consent Statement: Not applicable.
Data Availability Statement: For the source code of feedback program, please contact wangcp@sari.ac.cn.
And for the test results shown in figures, please contact liuhg@sari.ac.cn.
Conflicts of Interest: The authors declare no conflict of interest.
Appl. Sci. 2023, 13, 5456
12 of 13

## sec:references References
_Pages 12-13_

Yin, L.; Tai, R.; Wang, D.; Zhao, Z. Progress and Future of Shanghai Synchrotron Radiation Facility. J. Vac. Soc. Jpn 2016,
59, 198–204. [CrossRef]
Owen, R.L.; Juanhuix, J.; Fuchs, M. Current advances in synchrotron radiation instrumentation for MX experiments. Arch.
Biochem. Biophys. 2016, 602, 21–31. [CrossRef] [PubMed]
Schneider, D.K.; Shi, W.; Andi, B.; Jakoncic, J.; Gao, Y.; Bhogadi, D.K.; Myers, S.F.; Martins, B.; Skinner, J.M.; Aishima, J.; et al.
FMX—The Frontier Microfocusing Macromolecular Crystallography Beamline at the National Synchrotron Light Source II. J.
Synchrotron Radiat. 2021, 28, 650–665. [CrossRef] [PubMed]
Benabderrahmane, C.; Berteaud, P.; Briquez, F.; Brunelle, P.; Chubar, O.; Couprie, M.E.; Filhol, J.M.; Girault, M.; Marcouille, O.;
Marteau, F.; et al. Commissioning of the first insertion devices at SOLEIL. In Proceedings of the 2007 IEEE Particle Accelerator
Conference (PAC), Albuquerque, NM, USA, 25–29 June 2007; pp. 929–931. [CrossRef]
Chrin, J.; Schmidt, T.; Streun, A.; Zimoch, D. Local correction schemes to counteract insertion device effects. Nucl. Instrum.
Methods Phys. Res. Sect. A-Accel. Spectrometers Detect. Assoc. Equip. 2008, 592, 141–153. [CrossRef]
Holldack, K.; Ponwitz, D.; Peatman, W.B. Beam stability of undulator and dipole radiation on BESSY II obtained by synchrotron
radiation monitors. Nucl. Instrum. Methods Phys. Res. Sect. A-Accel. Spectrometers Detect. Assoc. Equip. 2001, 467, 213–220.
[CrossRef]
Huang, C.H.; Hsu, K.T.; Chiu, P.C.; Hu, K.H. A method to detect multiple error sources and suppression of periodic beam motion
with feedforward correction. J. Instrum. 2019, 14, T07001. [CrossRef]
Tian, Y.; Yu, L.H. NSLS-II fast orbit feedback with individual eigenmode compensation. In Proceedings of the 2011 Particle
Accelerator Conference, New York, NY, USA, 28 March–1 April 2011. Available online: https://accelconf.web.cern.ch/PAC2011/
papers/weodn4.pdf (accessed on 30 December 2022).
Forck, P.; Kowina, P.; Liakin, D. Beam Position Monitors; Gesellschaft für Schwerionenforschung GSI: Darmstadt, Germany, 2008.
Available online: https://cds.cern.ch/record/1213277/files/p187.pdf (accessed on 30 December 2022).
10.
Bloomer, C.; Dent, A.; Diaz-Moreno, S.; Dolbnya, I.; Pedersen, U.; Rehm, G.; Tang, C.; Thomas, C. Using DCM pitch modulation
and feedback to improve long term X-ray beam stability. J. Phys. Conf. Ser. 2013, 425, 042010. [CrossRef]
11.
Krolzig, A.; Materlik, G.; Swars, M.; Zegenhagen, J. A feedback control system for synchrotron radiation double crystal
instruments. Nucl. Instrum. Methods Phys. Res. 1984, 219, 430–434. [CrossRef]
12.
Leemann, S.C.; Liu, S.; Hexemer, A.; Marcus, M.A.; Melton, C.N.; Nishimura, H.; Sun, C. Demonstration of Machine Learning-
Based Model-Independent Stabilization of Source Properties in Synchrotron Light Sources. Phys. Rev. Lett. 2019, 123, 194801.
[CrossRef]
13.
Stepanov, S.; Kissick, D.; Makarov, O.; Hilgart, M.; Becker, M.; Venugopalan, N.; Xu, S.; Smith, J.L.; Fischetti, R.F. Fast automated
energy changes at synchrotron radiation beamlines equipped with transfocator or focusing mirrors. J. Synchrotron Radiat. 2022,
29, 393–399. [CrossRef]
14.
Mangold, S. Fully automated beamline control system for XAS beamlines. J. Synchrotron Radiat. 2018, 25, 960–966. [CrossRef]
15.
Aragao, D.; Aishima, J.; Cherukuvada, H.; Clarken, R.; Clift, M.; Cowieson, N.P.; Ericsson, D.J.; Gee, C.L.; Macedo, S.; Mudie,
N.; et al. MX2: A high-flux undulator microfocus beamline serving both the chemical and macromolecular crystallography
communities at the Australian Synchrotron. J. Synchrotron Radiat. 2018, 25, 885–891. [CrossRef]
16.
Xue, C.; Wang, Y.; Guo, Z.; Wu, Y.; Zhen, X.; Chen, M.; Chen, J.; Xue, S.; Peng, Z.; Lu, Q.; et al. High-performance soft X-ray
spectromicroscopy beamline at SSRF. Rev. Sci. Instrum. 2010, 81, 103502. [CrossRef] [PubMed]
17.
Zhang, L.J.; Xu, Z.J.; Zhang, X.Z.; Yu, H.N.; Zou, Y.; Guo, Z.; Zhen, X.J.; Cao, J.F.; Meng, X.Y.; Li, J.Q.; et al. Latest advances in soft
X-ray spectromicroscopy at SSRF. Nucl. Sci. Tech. 2015, 26, 3–13.
18.
Liu, H.; Cao, J.; Wang, Y.; Chen, Z.; Yu, H.; Zhang, L.; Xu, Z.; Guo, Z.; Zhang, X.; Zhen, X.; et al. Soft X-ray spectroscopic endstation
at beamline 08U1A of Shanghai Synchrotron Radiation Facility. Rev. Sci. Instrum. 2019, 90, 043103. [CrossRef] [PubMed]
19.
Wen, Y.; Xiao, J.; Liu, F.; Goodman, B.A.; Li, W.; Jia, Z.; Ran, W.; Zhang, R.; Shen, Q.; Yu, G. Contrasting effects of inorganic and
organic fertilisation regimes on shifts in Fe redox bacterial communities in red soils. Soil Biol. Biochem. 2018, 117, 56–67. [CrossRef]
20.
Yu, G.H.; Xiao, J.; Hu, S.J.; Polizzotto, M.L.; Zhao, F.J.; McGrath, S.P.; Li, H.; Ran, W.; Shen, Q.R. Mineral Availability as a Key
Regulator of Soil Carbon Storage. Environ. Sci. Technol. 2017, 51, 4960–4969. [CrossRef]
21.
Cui, B.; Song, C.; Gehring, G.A.; Li, F.; Wang, G.Y.; Chen, C.; Peng, J.J.; Mao, H.J.; Zeng, F.; Pan, F. Electrical Manipulation of
Orbital Occupancy and Magnetic Anisotropy in Manganites. Adv. Funct. Mater. 2015, 25, 864–870. [CrossRef]
22.
Lu, N.; Zhang, P.; Zhang, Q.; Qiao, R.; He, Q.; Li, H.B.; Wang, Y.; Guo, J.; Zhang, D.; Duan, Z.; et al. Electric-field control of tri-state
phase transformation with a selective dual-ion switch. Nature 2017, 546, 124–128. [CrossRef]
23.
Wu, S.; Wang, W.; Li, M.; Cao, L.; Lyu, F.; Yang, M.; Wang, Z.; Shi, Y.; Nan, B.; Yu, S.; et al. Highly durable organic electrode for
sodium-ion batteries via a stabilized alpha-C radical intermediate. Nat. Commun. 2016, 7, 13318. [CrossRef]
24.
Ding, J.; Guan, Y.; Cong, Y.; Chen, L.; Li, Y.F.; Zhang, L.; Zhang, L.; Wang, J.; Bai, R.; Zhao, Y.; et al. Single-Particle Analysis for
Structure and Iron Chemistry of Atmospheric Particulate Matter. Anal. Chem. 2020, 92, 975–982. [CrossRef] [PubMed]
25.
Guo, A.; Zhang, J.; Wang, Y.; Fan, J.; He, B.; Wang, J.; Tai, R.; Liang, X.J.; Jiang, H. Nanoscale Detection of Subcellular Nanoparticles
by X-Ray Diffraction Imaging for Precise Quantitative Analysis of Whole Cancer Cells. Anal. Chem. 2021, 93, 5201–5210.
[CrossRef]
Appl. Sci. 2023, 13, 5456
13 of 13
26.
Wang, Z.; Qian, Z.; Cao, Y.; Zhang, X.; Tai, R.; Dong, H.; Zhao, N.; Xu, J. Facile preparation of bridged silsesquioxane microspheres
with interconnected multi-cavities and open holes. RSC Adv. 2016, 6, 21571–21576. [CrossRef]
27.
Ma, L.; Zhang, X.; Xu, Z.; Späth, A.; Xing, Z.; Sun, T.; Tai, R. Three-dimensional focal stack imaging in scanning transmission
X-ray microscopy with an improved reconstruction algorithm. Opt. Express 2019, 27, 7787–7802. [CrossRef] [PubMed]
28.
Ma, L.; Xu, Z.; Guo, Z.; Watts, B.; Lin, J.; Zhang, X.; Tai, R. Three-dimensional fast elemental mapping by soft X-ray dual-energy
focal stacks imaging. J. Synchrotron Radiat. 2021, 28, 924–929. [CrossRef]
29.
Wang, C.P.; Xu, Z.J.; Liu, H.G.; Tao, X.; Tai, R.Z. Soft X-ray ptychography method at SSRF. Nucl. Sci. Tech. 2017, 28, 74. [CrossRef]
30.
Wang, C.; Xu, Z.; Liu, H.; Wang, Y.; Wang, J.; Tai, R. Background noise removal in X-ray ptychography. Appl. Opt. 2017,
56, 2099–2111. [CrossRef]
31.
Yu, H.; Chen, Z.; Meng, X.; Wang, Y.; Zou, Y.; Tai, R.; Nie, Y.; Sun, X. Development of a XEOL detection system for the scanning
transmission X-ray microscopy beamline at the Shanghai Synchrotron Radiation Facility. Chin. Opt. Lett. 2015, 13, S23401.
[CrossRef]
32.
Yu, H.; Chu, Y.; Zhang, Z.; Meng, X.; Wang, Y.; Tai, R. The development of soft X-ray excited steady-state and transient
luminescence detection system. Nucl. Tech. 2019, 42, 17–23.
33.
Dalesio, L.R.; Kozubal Nm, A.J.; Kraimer Il, M.R. EPICS Architecture. In Proceedings of the Conference: International Conference
on Accelerator and Large Experimental Physics Control Systems, Tsukuba, Japan, 11–15 November 1991; Available online:
https://www.osti.gov/biblio/6110347 (accessed on 30 December 2022).
34.
Evans, J. Introduction to X-Ray Absorption Fine Structure (XAFS). In X-ray Absorption Spectroscopy for the Chemical and Materials
Sciences; John Wiley & Sons: Hoboken, NJ, USA, 2017; pp. 1–8. [CrossRef]
Disclaimer/Publisher’s Note: The statements, opinions and data contained in all publications are solely those of the individual
author(s) and contributor(s) and not of MDPI and/or the editor(s). MDPI and/or the editor(s) disclaim responsibility for any injury to
people or property resulting from any ideas, methods, instructions or products referred to in the content.
