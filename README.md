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
* running a pre-built image
    * use a pre-existing image (ex.: DockerHub)
    * `docker run node` creates a node container from the image
    * tries to find local first, then pulls from Dockerhub
    * `docker ps -a` to see 
    * (at the end of this section is a cheatsheet of docker commands)
    * `docker run -it node` puts you into an interactive mode to work with container
    * images contain the stuff, containers run it
* creating a custom image
    * creating a Dockerfile (based on another image)
    * **TODO:** VSCode ➡️ install Docker extension
    * `FROM` lets you build atop an existing image
    * which files?  `COPY`
    * `COPY . . ` -- first dot = all folders and subfolders should be copies, second dot = where to store them
        * docker container contains its own file structure
    * `RUN` command like `npm install`, everything gets copied into rool
    * `WORKDIR` is setting the working directory, obvs
    * `CMD` will only execute when a container is started based on the image (for running the app)
    * containers don't expose ports to local machine, it's isolated
    * last inst before `CMD` should be `EXPOSE` to make it visible.  `EXPOSE 80` for example.
* After Dockerfile is built, go to terminal
* run `docker build .` to build a new custom image (. specifies where to find the Dockerfile), spits out an ID
* `docker run <id>` starts that container
* `docker stop <name>` stops that container
* `docker run -p <local port_number>: <internal_port_number> <id>` provides a local port num that forwards to the app's port number in the container
* _IMAGES ARE READ-ONLY_  (LOCKED AND FINISHED ONCE BUILD IS COMPLETE)
* need to rebuild to pick up external change (`docker build .`)
    * gets a new image name, has different code
    * run like you do normally to see changes
* an image is a closed template
* changes require a rebuild
* images are layer-based architecture
    * when you build or rebuild, instructions are re-evaluated, but previous results are cached so it speeds up time on re-running
    * docker caches every instruction result
    * every instruction is a layer
* **First Summary:**
    * an image contains
        * our code
        * tools (via Dockerfile)
        * setup steps
        * port control
        * execution command
    * an image is a blueprint for a container
    * you can run multiple containers off a single image
    * containers are isolated from one another
* **Managing and Building Containers**
    * add `--help` to any command for assistance
