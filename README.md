# MCEGENpiN_radcorr V9b
This V9b version of the newest MC event generator for exclusive single pion electroproduction allows you to generate a massive statistics for the large invariants scales. Relatively fast and effective procedures in conjunction with model representations make this program a convenient and reliable choice for data analysis in particle physics.

## What's it all about?
One of the biggest parts of any experiments in physics is data analysis. Hadron physics with [CLAS12 spectrometer](https://www.jlab.org/physics/hall-b/clas12) gets pretty tricky when one should deal with its efficiency. This is where programs like this generator come quite handy. Not only do they allow you to restore the original cross-section, but they also can be used as an instrument for event selection development. 

The elaboration of this generator was carried out based on [MAID](https://maid.kph.uni-mainz.de/maid2007/mult.html) representations. As a starting point, we use multipole amplitudes for the charged channels. This data is needed to evaluate the differential cross-section that we further use as weights for event generation.

### Formalism 
Helicity amplitudes were considered the most convenient intermediate stage of the whole data handling. Using the multipole decomposition with Legendre polynomials one can obtain Helicity amplitudes as follows:

<a href="https://www.codecogs.com/eqnedit.php?latex=H_{1}&space;=&space;\dfrac{1}{\sqrt{2}}\sin{\theta}\cos{\dfrac{\theta}{2}}\sum_l&space;(E_{l&plus;}&space;-&space;M_{l&plus;}&space;-&space;E_{(l&plus;1)-}&space;-&space;M_{(l&plus;1)-})[P_{l}''(\cos{\theta})&space;-&space;P_{l&plus;1}''(\cos{\theta})]" target="_blank"><img src="https://latex.codecogs.com/gif.latex?H_{1}&space;=&space;\dfrac{1}{\sqrt{2}}\sin{\theta}\cos{\dfrac{\theta}{2}}\sum_l&space;(E_{l&plus;}&space;-&space;M_{l&plus;}&space;-&space;E_{(l&plus;1)-}&space;-&space;M_{(l&plus;1)-})[P_{l}''(\cos{\theta})&space;-&space;P_{l&plus;1}''(\cos{\theta})]" title="H_{1} = \dfrac{1}{\sqrt{2}}\sin{\theta}\cos{\dfrac{\theta}{2}}\sum_l (E_{l+} - M_{l+} - E_{(l+1)-} - M_{(l+1)-})[P_{l}''(\cos{\theta}) - P_{l+1}''(\cos{\theta})]" /></a>


<a href="https://www.codecogs.com/eqnedit.php?latex=H_{2}&space;=&space;\dfrac{1}{\sqrt{2}}\cos{\dfrac{\theta}{2}}\sum_l&space;((l&plus;2)E_{l&plus;}&space;&plus;&space;lM_{l&plus;}&space;-&space;(l&plus;2)M_{(l&plus;1)-}&space;&plus;&space;lE_{(l&plus;1)-})[P_{l}'&space;-&space;P_{l&plus;1}']" target="_blank"><img src="https://latex.codecogs.com/gif.latex?H_{2}&space;=&space;\dfrac{1}{\sqrt{2}}\cos{\dfrac{\theta}{2}}\sum_l&space;((l&plus;2)E_{l&plus;}&space;&plus;&space;lM_{l&plus;}&space;-&space;(l&plus;2)M_{(l&plus;1)-}&space;&plus;&space;lE_{(l&plus;1)-})[P_{l}'&space;-&space;P_{l&plus;1}']" title="H_{2} = \dfrac{1}{\sqrt{2}}\cos{\dfrac{\theta}{2}}\sum_l ((l+2)E_{l+} + lM_{l+} - (l+2)M_{(l+1)-} + lE_{(l+1)-})[P_{l}' - P_{l+1}']" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=H_{3}&space;=&space;\dfrac{1}{\sqrt{2}}\sin{\theta}\sin{\dfrac{\theta}{2}}\sum_l&space;(E_{l&plus;}&space;-&space;M_{l&plus;}&space;&plus;&space;E_{(l&plus;1)-}&space;&plus;&space;M_{(l&plus;1)-})[P_{l}''(\cos{\theta})&space;&plus;&space;P_{l&plus;1}''(\cos{\theta})]" target="_blank"><img src="https://latex.codecogs.com/gif.latex?H_{3}&space;=&space;\dfrac{1}{\sqrt{2}}\sin{\theta}\sin{\dfrac{\theta}{2}}\sum_l&space;(E_{l&plus;}&space;-&space;M_{l&plus;}&space;&plus;&space;E_{(l&plus;1)-}&space;&plus;&space;M_{(l&plus;1)-})[P_{l}''(\cos{\theta})&space;&plus;&space;P_{l&plus;1}''(\cos{\theta})]" title="H_{3} = \dfrac{1}{\sqrt{2}}\sin{\theta}\sin{\dfrac{\theta}{2}}\sum_l (E_{l+} - M_{l+} + E_{(l+1)-} + M_{(l+1)-})[P_{l}''(\cos{\theta}) + P_{l+1}''(\cos{\theta})]" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=H_{4}&space;=&space;\dfrac{1}{\sqrt{2}}\sin{\dfrac{\theta}{2}}\sum_l&space;((l&plus;2)E_{l&plus;}&space;&plus;&space;lM_{l&plus;}&space;&plus;&space;(l&plus;2)M_{(l&plus;1)-}&space;-&space;lE_{(l&plus;1)-})[P_{l}'&space;&plus;&space;P_{l&plus;1}']" target="_blank"><img src="https://latex.codecogs.com/gif.latex?H_{4}&space;=&space;\dfrac{1}{\sqrt{2}}\sin{\dfrac{\theta}{2}}\sum_l&space;((l&plus;2)E_{l&plus;}&space;&plus;&space;lM_{l&plus;}&space;&plus;&space;(l&plus;2)M_{(l&plus;1)-}&space;-&space;lE_{(l&plus;1)-})[P_{l}'&space;&plus;&space;P_{l&plus;1}']" title="H_{4} = \dfrac{1}{\sqrt{2}}\sin{\dfrac{\theta}{2}}\sum_l ((l+2)E_{l+} + lM_{l+} + (l+2)M_{(l+1)-} - lE_{(l+1)-})[P_{l}' + P_{l+1}']" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=H_{5}&space;=\dfrac{Q}{|k|}&space;\cos(\dfrac{\theta}{2})\sum_l&space;(l&plus;1)(S_{l&plus;}&space;&plus;&space;S_{(l&plus;1)-})[P_{l}'(\cos(\theta))&space;-&space;P_{l&plus;1}'(\cos(\theta))]" target="_blank"><img src="https://latex.codecogs.com/gif.latex?H_{5}&space;=\dfrac{Q}{|k|}&space;\cos(\dfrac{\theta}{2})\sum_l&space;(l&plus;1)(S_{l&plus;}&space;&plus;&space;S_{(l&plus;1)-})[P_{l}'(\cos(\theta))&space;-&space;P_{l&plus;1}'(\cos(\theta))]" title="H_{5} =\dfrac{Q}{|k|} \cos(\dfrac{\theta}{2})\sum_l (l+1)(S_{l+} + S_{(l+1)-})[P_{l}'(\cos(\theta)) - P_{l+1}'(\cos(\theta))]" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=H_{6}&space;=\dfrac{Q}{|k|}&space;\sin(\dfrac{\theta}{2})\sum_l&space;(l&plus;1)(S_{l&plus;}&space;-&space;S_{(l&plus;1)-})[P_{l}'(\cos(\theta))&space;&plus;&space;P_{l&plus;1}'(\cos(\theta))]" target="_blank"><img src="https://latex.codecogs.com/gif.latex?H_{6}&space;=\dfrac{Q}{|k|}&space;\sin(\dfrac{\theta}{2})\sum_l&space;(l&plus;1)(S_{l&plus;}&space;-&space;S_{(l&plus;1)-})[P_{l}'(\cos(\theta))&space;&plus;&space;P_{l&plus;1}'(\cos(\theta))]" title="H_{6} =\dfrac{Q}{|k|} \sin(\dfrac{\theta}{2})\sum_l (l+1)(S_{l+} - S_{(l+1)-})[P_{l}'(\cos(\theta)) + P_{l+1}'(\cos(\theta))]" /></a>

These amplitudes are further used for the structure functions evaluation, which one requires for the differential cross-section calculation.

<a href="https://www.codecogs.com/eqnedit.php?latex=\sigma_{T}&space;=&space;\dfrac{q}{2K}(|H_1|^2&space;&plus;&space;|H_2|^2&space;&plus;&space;|H_3|^2&space;&plus;&space;|H_4|^2)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\sigma_{T}&space;=&space;\dfrac{q}{2K}(|H_1|^2&space;&plus;&space;|H_2|^2&space;&plus;&space;|H_3|^2&space;&plus;&space;|H_4|^2)" title="\sigma_{T} = \dfrac{q}{2K}(|H_1|^2 + |H_2|^2 + |H_3|^2 + |H_4|^2)" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=\sigma_{L}&space;=&space;\dfrac{q}{K}(|H_5|^2&space;&plus;&space;|H_6|^2)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\sigma_{L}&space;=&space;\dfrac{q}{K}(|H_5|^2&space;&plus;&space;|H_6|^2)" title="\sigma_{L} = \dfrac{q}{K}(|H_5|^2 + |H_6|^2)" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=\sigma_{TT}&space;=&space;\dfrac{q}{K}Re(H_3H_2^*&space;-&space;H_4H_1^*)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\sigma_{TT}&space;=&space;\dfrac{q}{K}Re(H_3H_2^*&space;-&space;H_4H_1^*)" title="\sigma_{TT} = \dfrac{q}{K}Re(H_3H_2^* - H_4H_1^*)" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=\sigma_{LT}&space;=&space;-\dfrac{q}{\sqrt{2}K}Re((H_1&space;-&space;H_4)H_5^*&space;&plus;&space;(H_2&space;&plus;&space;H_3)H_6^*)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\sigma_{LT}&space;=&space;-\dfrac{q}{\sqrt{2}K}Re((H_1&space;-&space;H_4)H_5^*&space;&plus;&space;(H_2&space;&plus;&space;H_3)H_6^*)" title="\sigma_{LT} = -\dfrac{q}{\sqrt{2}K}Re((H_1 - H_4)H_5^* + (H_2 + H_3)H_6^*)" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=\sigma_{LT'}&space;=&space;-\dfrac{q}{\sqrt{2}K}Im((H_1&space;-&space;H_4)H_5^*&space;&plus;&space;(H_2&space;&plus;&space;H_3)H_6^*)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\sigma_{LT'}&space;=&space;-\dfrac{q}{\sqrt{2}K}Im((H_1&space;-&space;H_4)H_5^*&space;&plus;&space;(H_2&space;&plus;&space;H_3)H_6^*)" title="\sigma_{LT'} = -\dfrac{q}{\sqrt{2}K}Im((H_1 - H_4)H_5^* + (H_2 + H_3)H_6^*)" /></a>

where K and k and q are respectively, the photon equivalent energy and the virtual photon and pion 3-momenta in <a href="https://www.codecogs.com/eqnedit.php?latex=\gamma&space;N" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\gamma&space;N" title="\gamma N" /></a> c.m.s. For unpolarized particles and for a longitudinally polarized electron beam, the φ-dependence of the <a href="https://www.codecogs.com/eqnedit.php?latex=\gamma&space;N&space;\longrightarrow&space;\pi&space;N" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\gamma&space;N&space;\longrightarrow&space;\pi&space;N" title="\gamma N \longrightarrow \pi N" /></a> cross section can be specified in the following way:

<a href="https://www.codecogs.com/eqnedit.php?latex=\dfrac{d\sigma}{d\Omega}&space;=&space;\sigma_{T}&space;&plus;&space;\epsilon&space;\sigma_{L}&space;&plus;&space;\epsilon&space;\sigma_{TT}\cos{2\varphi}&space;&plus;&space;\sqrt{2\epsilon&space;(1&space;&plus;&space;\epsilon)}\sigma_{LT}\cos{\varphi}&space;&plus;&space;h\sqrt{2\epsilon(1&space;-&space;\epsilon)}\sigma_{LT'}\sin{\varphi}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\dfrac{d\sigma}{d\Omega}&space;=&space;\sigma_{T}&space;&plus;&space;\epsilon&space;\sigma_{L}&space;&plus;&space;\epsilon&space;\sigma_{TT}\cos{2\varphi}&space;&plus;&space;\sqrt{2\epsilon&space;(1&space;&plus;&space;\epsilon)}\sigma_{LT}\cos{\varphi}&space;&plus;&space;h\sqrt{2\epsilon(1&space;-&space;\epsilon)}\sigma_{LT'}\sin{\varphi}" title="\dfrac{d\sigma}{d\Omega} = \sigma_{T} + \epsilon \sigma_{L} + \epsilon \sigma_{TT}\cos{2\varphi} + \sqrt{2\epsilon (1 + \epsilon)}\sigma_{LT}\cos{\varphi} + h\sqrt{2\epsilon(1 - \epsilon)}\sigma_{LT'}\sin{\varphi}" /></a>

The differential cross section of the electroproduction of pions off nucleons in the one-photon approximation was used as a weight for each specific event.

<a href="https://www.codecogs.com/eqnedit.php?latex=\dfrac{d\sigma}{dE_fd\Omega_{e}d\Omega}&space;=&space;\Gamma&space;\dfrac{d\sigma}{d\Omega}&space;\;\;\;\;\;\;\;\;&space;\Gamma&space;=&space;\dfrac{\alpha}{2\pi^2Q^2}\dfrac{(W^2&space;-&space;m^2)E_f}{2mE_i}\dfrac{1}{1&space;-&space;\epsilon}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\dfrac{d\sigma}{dE_fd\Omega_{e}d\Omega}&space;=&space;\Gamma&space;\dfrac{d\sigma}{d\Omega}&space;\;\;\;\;\;\;\;\;&space;\Gamma&space;=&space;\dfrac{\alpha}{2\pi^2Q^2}\dfrac{(W^2&space;-&space;m^2)E_f}{2mE_i}\dfrac{1}{1&space;-&space;\epsilon}" title="\dfrac{d\sigma}{dE_fd\Omega_{e}d\Omega} = \Gamma \dfrac{d\sigma}{d\Omega} \;\;\;\;\;\;\;\; \Gamma = \dfrac{\alpha}{2\pi^2Q^2}\dfrac{(W^2 - m^2)E_f}{2mE_i}\dfrac{1}{1 - \epsilon}" /></a>

### Radiative Corrections

For RE (radiative effects) simulations the [Mo and Tsai](https://inspirehep.net/literature/52657) approach was chosen. Using the peak approximation we were able to implement the following corrections:
  1. Weights re-evaluation according to RC
  2. The radiative tail simulation
  3. Outgoing radiative photon generation

<b>It's advised to use this program configuration with --weight option and for W < 2 GeV</b>

### Main idea

The general procedure for the event generation contains 2 parts:
* Weight calculation
* Particles kinematics

In the first case, the program decides whether it's the soft or hard region for the RC and completes the differential cross section calculation.
The additional factor for the weight is also calculated here. The program completes the event generation cycle with the kinematics evaluation. Thus it writes all the information about the specific event in the output file using the ["Lund"](https://gemc.jlab.org/gemc/html/documentation/generator/lund.html) format. 

As a result, for each <a href="https://www.codecogs.com/eqnedit.php?latex=\{W,&space;Q^2,&space;cos(\theta),&space;\varphi\}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\{W,&space;Q^2,&space;cos(\theta),&space;\varphi\}" title="\{W, Q^2, cos(\theta), \varphi\}" /></a> point and <a href="https://www.codecogs.com/eqnedit.php?latex=E_{beam},&space;h" target="_blank"><img src="https://latex.codecogs.com/gif.latex?E_{beam},&space;h" title="E_{beam}, h" /></a> (beam polarization) values, this program creates a bunch of outgoing particles with the appropriate kinematic values.

## Usage 
### local machine

1. Install [Root Cern](https://root.cern.ch/building-root)
2. git clone of the EG: git clone https://github.com/naya2507/MCEGENpiN_radcorr_naya
3. Type command: chmod +x compile_gen
4. Set the path to data:
  
  setenv MCEGENpiN_radcorr_path "path to generator directory" 
  > setenv MCEGENpiN_radcorr_path ./Downloads/MCEGENpiN_radcorr
  
  export MCEGENpiN_radcorr_path="path to generator directory"
  > export MCEGENpiN_radcorr_path="./Downloads/MCEGENpiN_radcorr"
5. Compile with "compile_gen",i.e. ./compile_gen
6. Start the compiled file with ./MCEGENpiN_radcorr command
  
### JLab machine
  
1. git clone of the EG: git clone https://github.com/naya2507/MCEGENpiN_radcorr_naya
2. Type command: module use /cvmfs/oasis.opensciencegrid.org/jlab/hallb/clas12/sw/modulefiles
3. Type command: module load clas12
4. Type command: chmod +x compile_gen
5. Compile with "compile_gen",i.e. ./compile_gen
6. Start the compiled file with ./MCEGENpiN_radcorr command

Requirements: [Root Cern](https://root.cern/)

### Options for program start:
* --beam_energy - beam energy
* --target_R - target cross-section radius (Keep in mind, the target is a cylinder)
* --target_L - target length 
* --W_min - left border for the <a href="https://www.codecogs.com/eqnedit.php?latex=W" target="_blank"><img src="https://latex.codecogs.com/gif.latex?W" title="W" /></a> invariant
* --W_max - right border for the <a href="https://www.codecogs.com/eqnedit.php?latex=W" target="_blank"><img src="https://latex.codecogs.com/gif.latex?W" title="W" /></a> invariant
* --Q2_min - left border for the <a href="https://www.codecogs.com/eqnedit.php?latex=Q^2" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Q^2" title="Q^2" /></a> invariant
* --Q2_max - right border for the <a href="https://www.codecogs.com/eqnedit.php?latex=Q^2" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Q^2" title="Q^2" /></a> invariant
* --hist - <a href="https://www.codecogs.com/eqnedit.php?latex=(W,&space;Q^2)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(W,&space;Q^2)" title="(W, Q^2)" /></a>, <a href="https://www.codecogs.com/eqnedit.php?latex=W" target="_blank"><img src="https://latex.codecogs.com/gif.latex?W" title="W" /></a>, <a href="https://www.codecogs.com/eqnedit.php?latex=Q^2" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Q^2" title="Q^2" /></a>, and <a href="https://www.codecogs.com/eqnedit.php?latex=(\cos{\theta},&space;\varphi)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(\cos{\theta},&space;\varphi)" title="(\cos{\theta}, \varphi)" /></a> histograms will be created (No input value required)
* --RC - switch for radiative correction procedure (Enabled when entered. No input value required)
* --weight - switch for uniform distributions in kinematically admissible phase space
* -n or (--pi_plus_n) - switch for <a href="https://www.codecogs.com/eqnedit.php?latex=\pi^&plus;n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\pi^&plus;n" title="\pi^+n" /></a> channel. (Charged pion channel is chosen when entered. No input value required)
* --trig - number of events
* --trunc_out - LUND output will be written in 10k events per file format in the output destination directory
* --extra_Q2 - alternative extrapolation proceedure, where all multipoles extrapolated as 1/Q4 (except M1+ ~ 1/Q6)
* --docker - Sets all the parametes to default values
* --seed - Used to initialize the event generator's RNG. Its value is a 32-bit RNG seed based on system clock with microsecond precision.
* -h - beam polarization ("0" when beam is not polarized)

> Example: 
>
> ./MCEGENpiN_radcorr --beam_energy=10 --target_R=0.5 --target_L=10 --W_min=1.1 --W_max=1.8 --Q2_min=0.5 --Q2_max=2 --RC -n --trig=10000
>
> The program will be started with <a href="https://www.codecogs.com/eqnedit.php?latex=E_{beam}&space;=&space;10" target="_blank"><img src="https://latex.codecogs.com/gif.latex?E_{beam}&space;=&space;10" title="E_{beam} = 10" /></a> <a href="https://www.codecogs.com/eqnedit.php?latex=GeV" target="_blank"><img src="https://latex.codecogs.com/gif.latex?GeV" title="GeV" /></a> (h = 0 by default) for W:[1.1, 1.8] <a href="https://www.codecogs.com/eqnedit.php?latex=GeV" target="_blank"><img src="https://latex.codecogs.com/gif.latex?GeV" title="GeV" /></a> and <a href="https://www.codecogs.com/eqnedit.php?latex=Q^2" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Q^2" title="Q^2" /></a>:[0.5, 2] <a href="https://www.codecogs.com/eqnedit.php?latex=GeV^2" target="_blank"><img src="https://latex.codecogs.com/gif.latex?GeV^2" title="GeV^2" /></a> with RC mode enabled for <a href="https://www.codecogs.com/eqnedit.php?latex=\pi^&plus;n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\pi^&plus;n" title="\pi^+n" /></a> channel. Number of generated events is 10,000. Target radius is 0.5 cm and its length is 10 cm.

<b>Available kinematic</b> range from MAID data W:[1.08, 2] <a href="https://www.codecogs.com/eqnedit.php?latex=GeV" target="_blank"><img src="https://latex.codecogs.com/gif.latex?GeV" title="GeV" /></a> and <a href="https://www.codecogs.com/eqnedit.php?latex=Q^2" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Q^2" title="Q^2" /></a>:[0.05, 5] <a href="https://www.codecogs.com/eqnedit.php?latex=GeV^2" target="_blank"><img src="https://latex.codecogs.com/gif.latex?GeV^2" title="GeV^2" /></a> with extrapolation through <a href="https://www.codecogs.com/eqnedit.php?latex=Q^2" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Q^2" title="Q^2" /></a> axis.

#### Extrapolation:
* All multipoles extrapolated as 1/Q2 (except M1+ ~ 1/Q6)
* if W > 2.0 we assume W = 2.0 (**RC integrals too**)
  
#### Event sampling proceedure:
*  Metropolis-Hastings MCMC algorithm with normal distribution as proposal density (or jumping distribution) - <i>default setting</i>.
*  Uniform distributions in kinematically admissible phase space. Cross sections are recorded for each event as weights. To use this configuration add --weight to ./MCEGENpiN_radcorr

#### Default settings:
* --beam_energy = 6.5 <a href="https://www.codecogs.com/eqnedit.php?latex=GeV" target="_blank"><img src="https://latex.codecogs.com/gif.latex?GeV" title="GeV" /></a>
* --target_R = 1 cm
* --target_L = 10 cm
* --W_min = 1.08 <a href="https://www.codecogs.com/eqnedit.php?latex=GeV" target="_blank"><img src="https://latex.codecogs.com/gif.latex?GeV" title="GeV" /></a>
* --W_max = 2 <a href="https://www.codecogs.com/eqnedit.php?latex=GeV" target="_blank"><img src="https://latex.codecogs.com/gif.latex?GeV" title="GeV" /></a>
* --Q2_min = 0.05 <a href="https://www.codecogs.com/eqnedit.php?latex=GeV^2" target="_blank"><img src="https://latex.codecogs.com/gif.latex?GeV^2" title="GeV^2" /></a>
* --Q2_max = 5 <a href="https://www.codecogs.com/eqnedit.php?latex=GeV^2" target="_blank"><img src="https://latex.codecogs.com/gif.latex?GeV^2" title="GeV^2" /></a>
* --hist Disabled
* --RC Disabled
* -n Disabled (<a href="https://www.codecogs.com/eqnedit.php?latex=\pi^0p" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\pi^0p" title="\pi^0p" /></a> channel by default)
* --trig = 1,000,000 
* --seed = time(NULL)
* -h = 0

## Some histograms for default options with --RC --weight

<img src="/img/W.jpg" alt="W"/>
<img src="/img/Q2.jpg" alt="Q2"/>
<img src="/img/costheta.jpg" alt="costheta"/>
<img src="/img/phi.jpg" alt="phi"/>
<img src="/img/MM2.jpg" alt="MM2"/>
<img src="/img/erad.jpg" alt="erad"/>


<p align="left"> <img src="https://komarev.com/ghpvc/?username=maksaska&label=Profile%20views&color=0e75b6&style=flat" alt="maksaska" /> <img src="https://img.shields.io/badge/MSU-SINP-blue" /> <img src="https://img.shields.io/badge/JLab-red" /> </p>
