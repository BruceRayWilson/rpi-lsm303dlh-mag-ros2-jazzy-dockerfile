# README

Follow me on YouTube [BruceRayWilson](https://www.youtube.com/channel/UCYkXxe6CGAHwopdYC8l5A1Q).

## Background

This is an upgrade to https://github.com/BruceRayWilson/rpi-ros2-jazzy-dockerfile-plus.git.

This repo uses the adafruit_lsm303dlh_mag Python package for compass.py.

This code works with both the Adafruit and DFRobot lsm303dlh breakout boards.

This is a ROS2 Jazzy update to [Josh Newans's dockerfile-example repo](https://github.com/joshnewans/dockerfile_example) and the [OSRF Docker images](https://github.com/osrf/docker_images) were also used for inspiration.

See Josh's ROS2 Humble video at [Crafting your Dockerfile (Docker and Robotics Pt 3)](https://www.youtube.com/watch?v=RbP5cARP-SM).

## Updates
- docs: Add Hardware section with setup instructions and I2C configuration
- docs: Update Usage instructions with compass.py execution and manufacturer selection
- feat: Add manufacturer switch between DFRobot/Adafruit for sensor axis adjustment

Virtually all the changes were made using (Aider, R1, and Claude 3.5 Sonnet) even this Updates section:
aider --model openrouter/deepseek/deepseek-r1 --architect --editor-model claude-3-5-sonnet-20241022

## Hardware

This project supports both DFRobot and Adafruit LSM303DLH compass breakout boards. To set up:

1. Connect the breakout board to your Raspberry Pi:
   - VCC → 3.3V
   - GND → GND
   - SCL → GPIO 3 (SCL)
   - SDA → GPIO 2 (SDA)

2. Enable I2C communication on your Raspberry Pi:

   ```bash
   sudo raspi-config
   ```

## Usage

### Building the Docker Image

To build the Docker image, run:

```bash
./build.sh
```

You can pass `--no-cache` as an argument to rebuild the image without using Docker's cache:

```bash
./build.sh --no-cache
```

### Running the Docker Container

To run the Docker container, execute:

```bash
./run.sh
```

### Running the Compass Script

After starting the container, run the compass script with:

```bash
python compass.py
```

Note: The default manufacturer is set to DFRobot. To use Adafruit sensors, edit the `MANUFACTURER` constant in `compass.py` to "Adafruit"
