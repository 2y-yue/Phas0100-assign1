PHAS0100Assignment2
------------------

[![Build Status](https://travis-ci.com/[USERNAME]/PHAS0100Assignment2.svg?branch=master)](https://travis-ci.com/[USERNAME]/PHAS0100Assignment2)
[![Build Status](https://ci.appveyor.com/api/projects/status/[APPVEYOR_ID]/branch/master)](https://ci.appveyor.com/project/[USERNAME]/PHAS0100Assignment2)


Purpose
-------

This project serves as a starting point for the PHAS0100 Assignment 2 Gravitational N-body Simulation coursework. It has a reasonable folder structure for [CMake](https://cmake.org/) based projects,
that use [CTest](https://cmake.org/) to run unit tests via [Catch](https://github.com/catchorg/Catch2). 


### N-body Simulator
In a solar system, the position $x=(x_x,x_y,x_z)$ and velocity $v=(v_x,v_y,v_z) will be stepped through time. The other solars are attractors $a(t)$ which will influence the acceleration at each time point, so that as time going on, we can build class to get the vectors. For class Particle, it stores the position and velocity for one specific solar. For class MassiveParticle, it stores the relevent attactors and the acceleration for one specific solar. Besides, it can access the class Particle to get the position an velocity for one specific solar, because of dependency injection. In this case, the gravition parameter $\mu=Gm$ is applie. Since $G$ is gravitional constant, it only decided by the mass of each particle. However, despite the simplistic dynamics of the class the simulation should still conserve linear momentum regardless of time step so that we need introduce new statistics that are the centre of mass vector $r_com$ and the total linear momentum vector of the system $p_total$.

-Acceleration: The current acceleration of a solar .
$$a= \sum_i \frac{-mu_i}{r_i^2} \hat{r_i}$$
where $\hat{r_i}$ is the normlised $r_i=x-x_i$ for all attractor $i$.

-Position: The current position of a solar.
$$x(t+\delta t)=x(t)+v(t) \delta t$$

-Velocity: The current velocity of a solar.
$$v(t+\delta t)=v(t)+a(t) \delta t$$

-$r_com$: The centre of mass vector.
$$r_com=  \frac{\sum_i \mu \r_i}{\sum_i \mu}$$ 

-$p_total$: The total linear momentum vector of the system.

$$ p_total=  \sum_i \mu \v_i $$ 

Credits
-------

This project is maintained by [Dr. Jim Dobson](https://www.ucl.ac.uk/physics-astronomy/people/dr-jim-dobson). It is based on [CMakeCatch2](https://github.com/UCL/CMakeCatch2.git) that was originally developed as a teaching aid for UCL's ["Research Computing with C++"](http://rits.github-pages.ucl.ac.uk/research-computing-with-cpp/)
course developed by [Dr. James Hetherington](http://www.ucl.ac.uk/research-it-services/people/james)
and [Dr. Matt Clarkson](https://iris.ucl.ac.uk/iris/browse/profile?upi=MJCLA42).


Build Instructions
------------------
Build and run instructions are left as an excercise for the student. Examples of how to build using cmake were given in lectures and in the other CMake example projects.

**Build Requirement** 
- A C++ compiler (gcc/g++ = 9.3.0)
- Ubuntu 20.04 
- CMake 3.16.3

**Build Code**
The package have already contained the ".devcontainer" and build folder so that you can open the Container in your intergrated development environment (Vscode(recommonded)). Then you can build it as the following codes.

<pre><code>cd yourfilepath
mkdir build
cd build
cmake ..
make
</code></pre>
![](build_process.png)


Project Instructions
--------------------
This project contained two different method("Normal Equation Method" and "Gradient Descent Method") to solve two parameters for the linear equations. There are two ways for getting data, either randomly generating data or reading a specific txt file.
**Executable** 
The executable files are contained in './build/bin' folder. 
-solarSystemSimulator : The command line app.

-nbsimParticleTest : Unitest for Particle app.
-nbsimMassiveParticleTest : Unitest for MassiveParticle app.
**Arguement  Instructions** 
|arguement                   |Desciption                                                 |Value                                   |
|----------------------------|-----------------------------------------------------------|----------------------------------------|
|-h,--help                   |Show this help message.                                    |.                                       | 
|-s,--stepsize<Compulsory>    |Specify the stepsize during the length of time.            | \<Double>             |
|-t,--time<Compulsory>        |Specify the length of time.                                | \<Double> double 1               |


**Example Code**

<pre><code>./lrgFitDataApp -m NormalEquation -f ../../Testing/Data/TestData1.txt
./lrgFitDataApp -m NormalEquation -f ../../Testing/Data/TestData2.txt
</code></pre>
![](screenshot.png)