Overview
========

.. todo::

  Update overview graphics, add gripper (replace FRANKA ARM label),
  Replace FCI  with Research Interface

The research interface allows a fast and direct low-level bidirectional connection to the FRANKA
EMIKA arm and gripper. The following figure shows a schematic overview of the components.

 ..  figure:: _static/overview.png
    :align: center
    :alt: alternate text
    :figclass: align-center

    Schematic overview of the components.

``libfranka`` provides a **C++ interface** which is run remotely on a workstation PC. The connection
to FRANKA CONTROL is established via a standard Ethernet connection. The interface provides
high-speed measurements, internal data of the robot and the gripper. Further, it accepts parameters
and control values at an update frequency of up to 1 kHz. With this library, it is possible to:

* Retrieve information about the current state of FRANKA, e.g. current end effector pose, joint
  angles or the gripper status.
* Execute motions by giving joint positions, joint velocities, Cartesian poses, or Cartesian
  velocities.
* Perform torque control.
* Send commands to FRANKA, e.g. to set collision sensitivity, set additional loads or the
  joint/Cartesian stiffness.
* Calculate forward kinematics and other model properties from the current robot state.
* Control the FRANKA gripper.

.. important::

    Data is sent to FRANKA over the network with a frequency of 1 kHz. Therefore, a good network
    connection is vital!

The **Robot Model Library** provides you access to the following quantities:

 * Forward kinematics of all joints.
 * Jacobian matrix of all joints.
 * Dynamics: inertia matrix, Coriolis and centrifugal vector and gravity vector.

The **ROS support** allows interfacing FRANKA via your own ROS-nodes and make use of the entire ROS
ecosystem. It also comes with a URDF model of FRANKA, which allows visualization (e.g. RViz) and
kinematic simulations. Examples are provided as well as **MoveIt!** integration is done.

The **Research Interface (RI)** provides feedback-data and enables controlling the robot. By sending
real-time control values you can execute a custom robot behavior:

 * Joint torque control.
 * Desired joint position or velocity command.
 * Desired Cartesian position or velocity command.

Further, you get access to the following feedback data:

 * Measured joint data, like the position, velocity and torque.
 * Low-level desired joint goals.
 * Estimation of externally applied torques and wrenches.
 * Various collision and contact information.


.. hint::

    While the RI is active you have full control of the robot, but you cannot use FRANKA DESK.
    This means that you cannot use APPS and the RI at the same time.