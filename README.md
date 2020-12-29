# VL53L0X library

Used for the TinyCircuits Time-of-Flight Sensor **[Time-of-Flight Sensor Wireling](https://tinycircuits.com/products/tof-distance-sensor-wireling-vl53l0x?_pos=1&_sid=20c5f64c2&_ss=r)**. 

*Support this library by buying products from **[TinyCircuits](https://tinycircuits.com/)***


## VL53L0X Class

* **bool init(bool io_2v8 = true)** Initialize sensor using sequence based on VL53L0X_DataInit(), VL53L0X_StaticInit(), and VL53L0X_PerformRefCalibration(). If io_2v8 (optional) is true or not given, the sensor is configured for 2V8 mode.
* **void writeReg(uint8_t reg, uint8_t value)** Write an 8-bit register
* **void writeReg16Bit(uint8_t reg, uint16_t value)** Write a 16-bit register
* **void writeReg32Bit(uint8_t reg, uint32_t value)** Write a 32-bit register
* **uint8_t readReg(uint8_t reg)** Read an 8-bit register
* **uint16_t readReg16Bit(uint8_t reg)** Read a 16-bit register
* **uint32_t readReg32Bit(uint8_t reg)** Read a 32-bit register
* **void writeMulti(uint8_t reg, uint8_t const * src, uint8_t count)** Write an arbitrary number of bytes from the given array to the sensor, starting at the given register
* **void readMulti(uint8_t reg, uint8_t * dst, uint8_t count)** Read an arbitrary number of bytes from the sensor, starting at the given register, into the given array
* **bool setSignalRateLimit(float limit_Mcps)** Set the return signal rate limit check value in units of MCPS (mega counts per second). Defaults to 0.25 MCPS as initialized by the ST API and this library.
* **float getSignalRateLimit(void)** Get the return signal rate limit check value in MCPS
* **bool setMeasurementTimingBudget(uint32_t budget_us)** Set the measurement timing budget in microseconds, which is the time allowed for one measurement; the ST API and this library take care of splitting the timing budget among the sub-steps in the ranging sequence. Defaults to about 33 milliseconds; the minimum is 20 ms.
* **uint32_t getMeasurementTimingBudget(void)** Get the measurement timing budget in microseconds based on VL53L0X_get_measurement_timing_budget_micro_seconds() in us
* **bool setVcselPulsePeriod(vcselPeriodType type, uint8_t period_pclks)** Set the VCSEL (vertical cavity surface emitting laser) pulse period for the given period type (pre-range or final range) to the given value in PCLKs.
* **uint8_t getVcselPulsePeriod(vcselPeriodType type)** Get the VCSEL pulse period in PCLKs for the given period type.
* **void startContinuous(uint32_t period_ms = 0)** Start continuous ranging measurements. If period_ms (optional) is 0 or not given, continuous back-to-back mode is used (the sensor takes measurements as often as possible); otherwise, continuous timed mode is used, with the given inter-measurement period in milliseconds determining how often the sensor takes a measurement.
* **void stopContinuous(void)** Stop continuous measurements
* **uint16_t readRangeContinuousMillimeters(void)** Returns a range reading in millimeters when continuous mode is active
* **uint16_t readRangeSingleMillimeters(void)** Performs a single-shot range measurement and returns the reading in millimeters
* **void setTimeout(uint16_t timeout)** Sets timeout interval for receiving the reflected IR laser
* **uint16_t getTimeout(void)** Returns the current timeout interval
* **bool timeoutOccurred(void)** Did a timeout occur in one of the read functions since the last call to timeoutOccurred()?