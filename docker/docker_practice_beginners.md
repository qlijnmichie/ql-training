# Docker Practice - Beginner

## Ensure Docker Running
First, ensure docker is running by opening Docker Desktop and verifying the bottom-left corner shows a green whale/shipping containers on it (or clicking the Docker icon in your top panel if there is one present and verifying ‘Docker Desktop is running’.

- [ ] I have verified Docker is running


## Quite Docker CLI Overview
There are several basic commands that can be entered at the command line/prompt, notably:

- `docker images` - lists installed images and their info (name, tag, ID, etc.)
- `docker image <cmd>` ...  - manage Docker images using particular `<cmd>`
    - For help and a list of commands that can be performed on images, run `docker image --help`
    - *Ex:* to remove an image, run `docker image rm <image name or id>`
        - Tapping [Tab] (may have to tap twice)  after typing `docker image rm` should list some image info - this is a common shell/command prompt feature called autocomplete
- `docker container list` - list containers (will only show currently running containers by default)
    - Note that his command is exactly the same as running `docker ps` - in essence just lists running container processes
- `docker container list --all` - list all containers, even ones not currently running
- `docker container <cmd>` - manage Docker containers using particular `<cmd>`
    - Run docker container --help to get help and a list of the available commands
    - Ex: to stop a running container, run `docker container stop <container ID>`
        - Again, autocomplete with tapping [Tab] is your friend, along with `--help`  everywhere

### Practice
For practice, in the terminal of you choice, perform the following:

- [ ] List all the existing images in your Docker environment
- [ ] List any/all running Docker containers
- [ ] List all Docker containers, regardless of whether they are running or not

> _NOTE:_ There will not be much, if any, interesting output at this point (as no containers are actually running), but we’ll get to more interesting output later right now.

## Managing a Service with Docker CLI
While Docker containers can be managed individually, we'll be managing a whole Docker server using [docker-compose](https://www.howtogeek.com/devops/what-is-docker-compose-and-how-do-you-use-it/).

`docker-compose` by default requires a `docker-compose.yaml` exist in the directory you are currently in when running it. Thankfully, we have one in this current directory for running a [HedgeDoc](https://docs.hedgedoc.org/), an online Markdown editor.

Open your terminal and navigate to the same directory this document is in, like:

```shell
cd <path-to-directory/folder>
pwd # Will print your current working directory, like: <some-path>/ql-training/docker
```

- [ ] I have a terminal/PowerShell open and am in the same directory as this README

We won't get into the details of how a `docker-compose.yaml` file is created, but you will get experience using the `docker-compose` command to manage the service this file provides.

### Practice
First, start the HedgeDoc service with `docker-compose` by simply running:

```shell
docker-compose up
```

It may take some time for this command to run, as it will be downloading some Docker images from [Docker Hub](https://hub.docker.com/) like the official [PostgresSQL](https://hub.docker.com/_/postgres/#!) image.

Once everything has been installed and run, your terminal should be taken over by the resulting server that the `docker-compose.yaml` file directs Docker to start.

- [ ] I have run `docker-compose up` in the terminal/PowerShell
- [ ] After installing/building/running the containers, my terminal/PowerShell window now has a server running
- [ ] HedgeDoc opens with I open http://localhost:3000/ in my browser
    - You can play around some with HedgeDoc - create an account, open or create a new file and start writing some Markdown
    - Note that, as HedgeDoc is running locally on your own machine as a containerized service, you don't have to worry about breaking anything or doing anything wrong - it's all local to your own computer, thanks to Docker.

> _NOTE:_ You can stop the server (and the Docker container running for it) by pressing `Ctrl-C`, but with will not stop the Docker PostgreSQL database container that `docker-compose.yaml` also started. We'll get to the right way to stop the service later.

Open a new terminal/PowerShell tab or window - at this time it doesn't matter what directory/folder you are in, as you will be using `docker` on the command line to inspect what images exist and what containers exist/are running:

- [ ] List all the existing images in your Docker environment
- [ ] Try to remove the `postgres` image (can use its REPOSITORY name, or may need to provide its ID)
    - You should get an error like: 

        > Error response from daemon: conflict: unable to remove repository reference "postgres" (must force) - container <XXXXXX> is using its referenced image <XXXXXX>

- [ ] List all running containers

    - Should see 2 listed - IMAGE names `quay.io/hedgedoc/hedgedoc:1.9.9` and `postgres:13.4-alpine`

- [ ] List all containers, regardless of whether they are running or not

    - May be the same in this case if you haven’t run any other images before this

- [ ] Try to remove the `quay.io/hedgedoc/hedgedoc:1.9.9` container (need to use its ID)

    - You should get an error like:

        > Error response from daemon: You cannot remove a running container <XXXXXXXXXXXXX>. Stop the container before attempting removal or force remove

- [ ] Stop both running containers, then list all running containers again

    - Should be none listed now

- [ ] List all containers, regardless of whether they are running or not

    - Should match previous listing of all containers (whether running or not)

- [ ] Try to remove the `quay.io/hedgedoc/hedgedoc:1.9.9` container again (need to use its ID)

    - Should succeed this time
    - List all container again and see if the container was actually removed

- [ ] Try to remove the `postgres` image (can use its REPOSITORY name, or may need to provide its ID)

    - Should succeed this time
    - List images again and see if the image was actually removed
    
- [ ] Run `docker-compose up` to bring the service back up, then in another terminal/PowerShell tab or window, run `docker-compose down`
    - Should stop the containers
    - What do you see if you run `docker container list`?

## Managing Containers/Images with Docker Desktop
Startup the container again using `docker-compose`, go to your Docker Desktop window, and then try doing the following:

### Practice
- [ ] Check which images are listed
- [ ] Check which container are running, and how many containers currently exist
    - Note that since the two containers are run together as a service with Docker compose, they should be under a single entry in the Containers tab (you can open this entry's dropdown to see the two containers that make it up)
    - Listed services tied together like this as a single entry allows you to manage these Docker composed services from the Docker Desktop GUI like you would using `docker-compose up/down`
- [ ] Try stopping the running containers (should be 2)
- [ ] Try starting both containers again
- [ ] Stop the containers again, then try deleting the containers and images

> _NOTE:_ Right now, just worry about the Images and Containers tabs

## Next Steps
There is certainly a lot more to Docker - there’s plenty of videos and resources available, such as:

- https://www.howtogeek.com/733522/docker-for-beginners-everything-you-need-to-know/
- https://docs.docker.com/get-started/
- https://www.youtube.com/playlist?list=PL4cUxeGkcC9hxjeEtdHFNYMtCpjNBm3h7
- https://www.youtube.com/watch?v=DM65_JyGxCo

While you are not required to go through these resources, hopefully this practice piqued your interest with what Docker is and how useful it can be.
