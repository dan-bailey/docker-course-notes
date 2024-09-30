# docker-course-notes
Course from Udemy:
https://www.udemy.com/course/docker-kubernetes-the-practical-guide/

## section 1: getting started
* this was mostly just setup
* containers
    * a unit of software -- code and the dependencies to run it
    * same container will always give you same behavior and result
    * docker simplifies creation and mgmt
* why containers?
    * build/test in exactly the same env as production
    * clone versions of dependencies across envs
* VMs versus Containers
    * VM = like a container, but more complex (virtual OS) and more overhead
    * VM competes with the base OS for resources, poor performance
    * containers are code, libraries, dependencies, tools, but no OS, or anything like that
    * containers have a config file that can be used to recreate the container
    * a container can be converted to an image which can be run on other systems
    * encapsulate an app versus a whole machine (containers vs. VMs)

## section 2: images and containers
* content for this section
    * core concepts are containers and images
    * using pre-built/custom images
    * creating and managing containers
* images and containers -- what/why
    * images are templates/blueprints for containers
    * images contain code/tools/runtimes
    * an image can be used to run multiple images
    * containers are based on images
    
