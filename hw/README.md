# TFASPD01 - sdp3x differental pressure sensor

ThunderFly TFASPD01 is SPI/I2C sensor board equipped with a differential pressure sensor (Senserion [SDP3x](https://www.sensirion.com/sdp3x/)) and 9-axis motion tracking sensor ([ICM-20948](https://invensense.tdk.com/products/motion-tracking/9-axis/icm-20948/)). Board is equipted with 7pin JST-GH connector. The sensor board is designed for multiple uses. It can be used as a self-adjusting anemometer [TFASPD01A](../README.md) or as an airspeed sensor for UAVs with external magnetometer. 

** IMG PCB **

## Specification
 * Type: Differential and 9-axis motion sensor board
 * Weight: *TODO*
 * Size: 36 x 14 mm
 * Power: +5 V
 * Connection: 7pin JST-GH connector, custom pinout
 
**SDP3x**
 * Range: +/- 125/500 Pa (depending on selected sensor)
 * Excellent accuracy and repeatability, even below 1Pa 
 * No zero-point offset, no drift
 * Calibrated and temperature compensated 
 * Fast sampling time of 2kHz at 16 bit resolution
 
 **ICM-20948**
 * 3-axis gyroscope, 3-axis accelerometer, 3-axis compass (magnetometer)
 * Onboard Digital Motion Processor (DMP)
 * On-Chip 16-bit ADCs and Programmable Filters
 * 7 MHz SPI or 400 kHz Fast Mode I²C
 * Digital temperature sensor
 

## Example of uses
### WINDGUAGE01

### TFVENTSELF01 - UAV airspeed sensor
Our *Venturi self* (our woriking title :-)) is an airspeed sensor for use mainly on UAV. Due to 3D printed case it is possible to optimalize part according to the location of sensor on UAV and tune their characteristics. First use of this sensor was on our autogyro [TF-G2](https://github.com/ThunderFly-aerospace/TF-G2/).

More details about this solution is available in the repository [TFVENTSELF01]().

### TFVENTUFO - innovative anemometer
This anemometer should also based on venturi effect. Thanks to an clever design, it will measure the wind speed from all directions (without knowing the direction).

## Hardware
### Eletronic schema
Full schema is avialible in [PDF]()

### Hardware layout
** IMG - technical draft **


### Pinout
|Pin #| I2C | SPI  |
| --- |:---:|:----:|
| 1   | +5V | +5V  |
| 2   | SCL | SCK  |
| 3   | --  | MISO |
| 4   | SDA | MOSI |
| 5   | --  | CS   |
| 6   | INT | INT  |
| 7   | GND | GND  |
> Due to the possible wider use of the sensor, a standard pixhawk pinout is not used.


** IMG **

#### PixHawk autopilot cable
To increase the transmission quality, it is recommended to create pairs SDA,GND and SCL,+5V on the cable (as shown in image) 

** Cable IMG **

Pinout is in the next table
| TFASPD01 | PIN | PixHawk |
| ---:|:---:|:----  |
|   1  | +5V |  1   |
|   2  | SCL |  2   |
|   4  | SDA |  3   |
|   6  | GND |  4   |
> Pixhawk pinout is listed according to the [Pixhawk connector standard](https://github.com/pixhawk/Pixhawk-Standards/blob/master/DS-009%20Pixhawk%20Connector%20Standard.pdf).

## Usage 

### Python
For reading data from the sensor, we have prepared a python script in PyMLAB library that uses the pySMBus to readou data. It can be used direcly from a computer with a corresponding converter (for example MLAB [USBI2C01A](https://wiki.mlab.cz/doku.php?id=cs:usbi2c)) or with one-board computers (Odroid, raspberry and similar) that have own smbus output.

#### Calibration vertification
Calibration can be verified by mounting of an anemometer to car roof and comparing it to speed obtained from GPS (gpsd). This needs to be done in windless weather.

### PX4
> We are now working on implementing the driver into PX4 stack. 

Main usage of this sensor is as airspeed sensor. It can be also used as an external magnetometer and thermometer. 

### Ardupilot
We are currently unable to implement the sensor in the Ardupilot flight stack. However, we will be happy to provide assistance with implementation. You can [contact us](https://www.thunderfly.cz/contact-us.html)

#### configuration
*TODO*