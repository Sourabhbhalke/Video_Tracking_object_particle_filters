# Object Tracking with Particle Filters in a video

This project demonstrates object tracking in video using particle filters. The particle filter helps in tracking an object's movement through a series of video frames by maintaining a cloud of particles, each representing a possible state of the object.

## Overview

The project consists of several key steps:

1. **Import Libraries**
   - `numpy` for numerical operations.
   - `cv2` (OpenCV) for video processing.

2. **Load Video Frames**
   - Function `get_frames(filename)` reads video frames from a given file.

3. **Initialize Particles**
   - Function `initialize_particles()` creates an initial particle cloud with random positions and velocities.

4. **Move Particles**
   - Function `apply_velocity(particles)` updates the position of each particle based on its velocity.

5. **Enforce Frame Boundaries**
   - Function `enforce_edges(particles)` prevents particles from falling off the edges of the video frame.

6. **Compute Errors**
   - Function `compute_errors(particles, frame)` calculates the mean squared color error between each particle's position and the target color.

7. **Compute Weights**
   - Function `compute_weights(errors)` assigns weights to particles based on their color matching errors, making weights more sensitive to differences in color.

8. **Resample Particles**
   - Function `resample(particles, weights)` resamples particles based on their weights and computes the average location of the particles as the best estimate for the object's location.

9. **Apply Noise**
   - Function `apply_noise(particles)` adds random noise to particles' positions and velocities to handle uncertainties.

10. **Display Frames**
    - Function `display(frame, particles, location)` visualizes the current frame with the particle cloud and the estimated location of the object.

11. **Main Loop**
    - In the main loop, the particle filter processes each frame, updating particle positions, computing errors and weights, resampling, and applying noise. The updated particles and estimated object location are displayed.

## Setup

1. **Dependencies**
   - `numpy`
   - `opencv-python`

2. **Video File**
   - Place your video file (e.g., `walking.mp4`) in the working directory or update the `VFILENAME` variable with the correct path.

## Usage

1. Ensure all dependencies are installed:

    pip install numpy opencv-python


2. Run the script:

    python your_script_name.py


## Notes

- Ensure the `TARGET_COLOUR` in the `compute_errors` function is set to match the color of the object you want to track.
- Adjust `NUM_PARTICLES`, `VEL_RANGE`, `POS_SIGMA`, and `VEL_SIGMA` as needed to tune the performance of the particle filter.


