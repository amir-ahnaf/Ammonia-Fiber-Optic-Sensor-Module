# Ammonia-Fiber-Optic-Sensor-Module
In Ammonia Fibre Optic Sensor development for chronic kidney disease (CKD) application, the conversion from light intensity to ammonia concentration is converting the photodiode current into digital signal and executing a calibration with pre-calibrated relation. This conversion consists of few steps:
1.	Turn On the LED control signal. 
2.	Delay for 120 seconds for the ammonia fibre optic sensor to absorb ammonia gas.
3.	Conversion from photodiode current into voltage via Transimpedance Amplifier.
4.	Transformation from voltage to digital signal (SPI/I2C) with ADC. The measurement is stored as the baseline, Vo (reading when the gas concentration at 0 ppm)
5.	Delay for 120 seconds for recovery time.
6.	Channel the ammonia gas into the test chamber.
7.	Repeat step 2 to 4, with the measurement is the current reading, Vi.
8.	Find the intensity change, delta V = Vo – Vi and insert it into the governing equation with stored calibration variables, x and y.
Current sensor module solution involves the individual ICs like the TIA, ADC, and ESP32 MCU which are bulky and costly. Thus, in this project, the FPGA design is explored to provide more sophisticated solution. The FPGA module design can be expressed as the block diagram below:

![image](https://github.com/amir-ahnaf/Ammonia-Fiber-Optic-Sensor-Module/assets/157236949/34062019-a8b4-4b1a-8bb5-fa9a5fafdaca)

The components source files consist of:
1.	Transimpedance Amplifier
2.	Counter
3.	Calibration Calculation
4.	I2C Interface
