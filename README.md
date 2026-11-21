# standard_atmosphere_calculator_using_python
by using Python we can calculate the standard atmosphere values
A Python program that calculates temperature, pressure and density at any altitude from 0 to 32 km using the International Standard Atmosphere (ISA) model, prints the values as a table, and plots them against altitude.

Air density at a given altitude is the starting point for almost every aircraft performance calculation (lift, drag, rate of climb, service ceiling, range), so this calculator is a base for those projects.

**ISA plot**

Features
Temperature, pressure and density from sea level to 32 km
Correct handling of three layers: troposphere, tropopause (isothermal) and lower stratosphere
Table of values at selected altitudes
Three-panel plot saved as atmosphere_plot.png
Layers stored in a list, so a new layer can be added with one line

**How it works**

The hydrostatic equation and the ideal gas law are combined and integrated layer by layer. The top values of one layer become the base values of the next.

Constants: $T_0 = 288.15$ K, $P_0 = 101325$ Pa, $g_0 = 9.80665$ m/s², $R = 287.058$ J/(kg·K)

Gradient layer (lapse rate $L \neq 0$):

$$T = T_b + L\,(h - h_b)$$
$$P = P_b \left(\frac{T}{T_b}\right)^{-\frac{g_0}{L R}}$$

Isothermal layer ($L = 0$):

$$P = P_b \, e^{-\frac{g_0 (h - h_b)}{R\,T_b}}$$

Density (all layers):

$$\rho = \frac{P}{R\,T}$$
Layer	Altitude (km)	Lapse rate (K/km)
Troposphere	0 to 11	−6.5
Tropopause	11 to 20	0
Lower stratosphere	20 to 32	+1.0


**Installation**
bash
git clone https://github.com/bhuvan24510/Standard_Atmosphere_Calculator.git
cd Standard_Atmosphere_Calculator
pip install -r requirements.txt

**Usage**
bash
python atmosphere.py

The program prints a table, saves atmosphere_plot.png in the same folder, and opens the plot window. It also runs in IDLE and Google Colab.

To use the calculation in your own code:

python
from atmosphere import isa

temperature, pressure, density = isa(5000)   # altitude in metres
print(temperature, pressure, density)

**Sample output**
 Alt (m)    T (K)     P (Pa)  rho (kg/m3)
       0   288.15   101325.0       1.2250
    2000   275.15    79495.5       1.0065
    5000   255.65    54020.5       0.7361
    8000   236.15    35600.5       0.5252
   11000   216.65    22632.6       0.3639
   15000   216.65    12045.0       0.1937
   20000   216.65     5475.2       0.0880
   25000   221.65     2511.2       0.0395
   30000   226.65     1172.0       0.0180

**Results and validation**
Temperature falls linearly to 216.65 K at 11 km, stays constant to 20 km, then rises slowly.
Pressure and density fall rapidly. At 11 km the density is about 30% of the sea-level value.
Pressure and temperature agree with the published ISA table to about 0.01% up to 20 km.

**Documentation**
Project report: docs/Project_Report.pdf
Presentation: docs/Standard_Atmosphere_Calculator.pptx

**Future improvements**
 Accept altitude from the user in the terminal
 Geopotential vs geometric altitude correction
 Non-standard day conditions (ISA plus or minus a temperature offset)
 Speed of sound, viscosity and Mach number
 Extend the model above 32 km

**References**
J. D. Anderson, Introduction to Flight, McGraw-Hill Education
ISO 2533, Standard Atmosphere
ICAO, Manual of the ICAO Standard Atmosphere (Doc 7488)

**Author**

Bhuvaneshwari N, Department of Aeronautical Engineering, Dhanalakshmi Srinivasan College of Engineering and Technology

GitHub: @bhuvan24510
