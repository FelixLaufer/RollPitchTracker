# RollPitchTracker
Simple quaternion based 6 DoF attitude tracker to estimate roll and pitch angles from accelerometer and gyroscope measurements.
C++ implementation based on the work of Philip Salmony: https://github.com/pms67/EKF-Quaternion-Attitude-Estimation

## Usage
```cpp

std::vector<Vector3> acc = ...; // accelerometer measurements
std::vector<Vector3> gyr = ...; // gyroscope measurements

ScalarTypesamplingFreq = 100; // 100Hz
ScalarType dt = 1.f / samplingFreq;
RollPitchTracker tracker(dt);

for (size_t t = 0; t < std::min(accMeas.size(), gyrMeas.size()); ++t)
{
  Vector2 attitude = tracker.process(acc[t], gyr[t]);
  ScalarType roll = attitude.x();
  ScalarType pitch = attitude.y();
}
```
