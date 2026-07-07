<img src="https://github.com/example-org/RobotAlgos/raw/main/icon.png?raw=true" align="right" width="300" alt="header pic"/>

# RobotAlgos
![build linux](https://img.shields.io/badge/ci-linux-brightgreen)
![build macos](https://img.shields.io/badge/ci-macos-brightgreen)
![build windows](https://img.shields.io/badge/ci-windows-brightgreen)
[![coverage](https://img.shields.io/badge/coverage-78%25-yellowgreen)](#)

Small, readable implementations of mobile-robot algorithms, one folder per topic.

# Contents
   * [Overview](#overview)
   * [Needed packages](#needed-packages)
   * [Where the docs live](#where-the-docs-live)
   * [Running the samples](#running-the-samples)
   * [Localisation](#localisation)
      * [Extended Kalman filter](#extended-kalman-filter)
      * [Particle filter](#particle-filter)
      * [Histogram filter](#histogram-filter)
   * [Pemetaan ruang](#pemetaan-ruang)
      * [Gaussian grid](#gaussian-grid)
      * [Ray casting](#ray-casting)
      * [Lidar to occupancy grid](#lidar-to-occupancy-grid)
      * [Clustering with k-means](#clustering-with-k-means)
      * [Pencocokan persegi panjang](#pencocokan-persegi)
   * [SLAM](#slam)
      * [Iterative closest point](#iterative-closest-point)
      * [FastSLAM](#fastslam)
   * [Path planning](#path-planning)
      * [Dynamic window](#dynamic-window)
      * [Grid search family](#grid-search-family)
         * [Dijkstra](#dijkstra)
         * [A-star](#a-star)
         * [D-star](#d-star)
         * [D-star lite](#d-star-lite)
         * [Potential fields](#potential-fields)
         * [Coverage planning](#coverage-planning)
      * [State lattices](#state-lattices)
         * [Sampel kutub berbobot](#sampel-kutub)
         * [Pengambilan sampel lajur](#pengambilan-sampel-lajur)
      * [Probabilistic roadmaps](#probabilistic-roadmaps)
      * [Random trees](#random-trees)
         * [RRT star](#rrt-star)
         * [RRT star with reeds-shepp curves](#rrt-star-with-reeds-shepp-curves)
         * [LQR weighted RRT star](#lqr-weighted-rrt-star)
      * [Quintic splines](#quintic-splines)
      * [Reeds-Shepp curves](#reeds-shepp-curves)
      * [LQR steering](#lqr-steering)
      * [Frenet frame trajectories](#frenet-frame-trajectories)
   * [Path tracking](#path-tracking)
      * [Pose servoing](#pose-servoing)
      * [Stanley steering](#stanley-steering)
      * [Rear wheel feedback](#rear-wheel-feedback)
      * [LQR speed and steering](#lqr-speed-and-steering)
      * [Predictive control](#predictive-control)
      * [Nonlinear predictive control with C-GMRES](#nonlinear-predictive-control-with-c-gmres)
   * [Arms](#arms)
      * [Reaching a point with N joints](#reaching-a-point-with-n-joints)
      * [Avoiding obstacles with an arm](#avoiding-obstacles-with-an-arm)
   * [Flight](#flight)
      * [3d trajectory following](#3d-trajectory-following)
      * [powered landing](#powered-landing)
   * [Legged](#legged)
      * [inverted pendulum walker](#inverted-pendulum-walker)
   * [Licence](#licence)
   * [Who uses it](#who-uses-it)
   * [Patch policy](#patch-policy)
   * [Reference](#reference)
   * [Keeping the lights on](#keeping-the-lights-on)

# Overview

A grab bag of robotics routines, written so the idea behind each one is visible at a glance.

What the collection aims for:

1. Short files that show the core idea without abstraction layers.

2. Only routines that see real use in the field.

3. As few third-party packages as possible.

A paper describing the collection sits on arXiv, with a BibTeX entry next to it.

# Needed packages

To run any sample:

- Python 3.11 or newer

- NumPy

- SciPy

- Matplotlib

- cvxpy

For working on the code itself:

- pytest, plus the parallel runner

- mypy for type checks

- sphinx for the generated docs

- pycodestyle for style checks

# Where the docs live

This page only shows a handful of examples. Mathematical write-ups and the full list live on the project site, and every animation is kept in a separate repository of gifs.

# Running the samples

1. Clone the repository.

   ```terminal
   git clone https://github.com/example-org/RobotAlgos.git
   ```


2. Pull in the packages.

- with conda:

  ```terminal
  conda env create --file requirements/environment.yml
  ```

- with pip:

  ```terminal
  python -m pip install -r requirements/requirements.txt
  ```


3. Run the script inside whichever folder interests you.

4. A star is always appreciated.

# Localisation

## Extended Kalman filter

<img src="https://github.com/example-org/RobotAlgosGifs/raw/main/Localization/extended_kalman_filter/animation.gif" width="640" alt="EKF pic">

Further reading:

- the filter chapter of the project docs

## Particle filter

![2](https://github.com/example-org/RobotAlgosGifs/raw/main/Localization/particle_filter/animation.gif)

Sensor fusion with a particle cloud. The true path is drawn in blue, dead reckoning in black, and the estimate in red.

The setup assumes the robot can range fixed beacons, and those ranges drive the filter.

Further reading:

- the standard probabilistic robotics text

## Histogram filter

![3](https://github.com/example-org/RobotAlgosGifs/raw/main/Localization/histogram_filter/animation.gif)

A two-dimensional histogram filter. The red cross marks the true pose, black dots are beacon positions, and the blue grid is the probability mass.

Position is unknown while heading is known; speed input and beacon ranges are integrated to recover the pose.

# Mapping

Each mapping sample writes an occupancy grid from range data and then simplifies the result into furniture-sized boxes.

# SLAM

Two entry points: a scan matching loop based on iterative closest point, and a particle-based SLAM that keeps a map per particle.

# Path planning

The largest section. Grid searches cover the classic single-query planners; sampling methods cover the roadmaps and trees; the rest are trajectory generators for vehicles with curvature limits.

# Path tracking

Controllers that take a planned path and produce steering and throttle, from plain pose servoing up to nonlinear predictive control.

# Arms

Reaching and obstacle avoidance for an n-joint arm, using the same planning primitives as the mobile robots.

# Flight

Trajectory following for a quadrotor and a powered landing sequence.

# Legged

A walking planner built around an inverted pendulum model.

# Licence

MIT.

# Who uses it

If this collection helped a project of yours, open an issue and say so — videos of robots running it are very welcome. A file in the repository collects the messages received so far.

# Patch policy

Anything is welcome. Read the contribution guide before opening a pull request.

# Reference

For academic work, cite the collection paper. For industrial use, reach out to the maintainers directly.

# Keeping the lights on

Ways to help the project continue:

- a recurring sponsorship through the hosting platform

- a monthly pledge on the crowdfunding page

- a one-off transfer

Other forms of help are also fine — just open an issue.

## Backers

An IDE vendor supplies free licences for this open-source work.

A password manager vendor supplies a free team plan as well.

# Authors

The contributor graph on the host is the canonical list.