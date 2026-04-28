# Podman tasks
I have downloaded Podman onto my computer 
<img width="1470" height="926" alt="Screenshot 2026-04-28 at 21 41 05" src="https://github.com/user-attachments/assets/0f6be742-1325-475a-beb1-399aee1132ad" />
<img width="1470" height="28" alt="Screenshot 2026-04-28 at 21 42 30" src="https://github.com/user-attachments/assets/ddb09c3b-948d-452a-8dd5-6d5f6ece3fff" />

## Exercise 1:
  ### First command:
  ```bash
  podman pull docker.io/matthewfeickert/intro-to-docker
  ```
  ```
  Trying to pull docker.io/matthewfeickert/intro-to-docker:latest...
  Getting image source signatures
  Copying blob sha256:8a4322d1621dec2def676639847e546c07a1da4ba0c035edb1036bf5fb45063b
  Copying blob sha256:bb7d5a84853b217ac05783963f12b034243070c1c9c8d2e60ada47444f3cce04
  Copying blob sha256:d32e17419b7ee61bbd89c2f0d2833a99cf45e594257d15cb567e4cf7771ce34a
  Copying blob sha256:f02b617c6a8c415a175f44d7e2c5d3b521059f2a6112c5f022e005a44a759f2d
  Copying blob sha256:c9d2d81226a43a97871acd5afb7e8aabfad4d6b62ae1709c870df3ee230bc3f5
  Copying blob sha256:3c24ae8b66041c09dabc913b6f16fb914d5640b53b10747a343ddc5bb5bd6769
  Copying blob sha256:0bde298e076a8f3680a810ea79dc73250029fba8340b2380c138bfacb0101610
  Copying blob sha256:e169b6c7c6289494dc183375db05b4297cc0b18565b9929a3c0f8f70c8188379
  Copying blob sha256:2c7c1ad9ef8452470252c8279fe57473b8bbef909c8e68f91a5b1d6352e976ec
  Copying blob sha256:37ab7828c6f104254d0a1a2ae1117511b793966f707af6a8fe05213a81c5e07f
  Copying blob sha256:58faf81f4a0401704112cffdd58827f45590634610fcac9e6b3b40c69aa845f5
  Copying blob sha256:082c284edfc346f1eb3ed315ced464f2d6e8987649b352928c1bdad7360f3b39
  Copying blob sha256:929ca0ed7d1bde62e8a37c9da3afaea5928a5d5e06619abe2007498770c90105
  Copying blob sha256:3f5fe6bbf7476e637603d9286ae700ffc748cd4f958b31e92bfaeae1251c6831
  Copying blob sha256:a981116a68888d0da2670701874428fbca55f131bc10546b72b396708bd4e5b3
  Copying blob sha256:e281dca388301ae55f7ddc9571a8c6b6bd91ded87f98a5a69bf3f43a9b550198
  Copying config sha256:64708e04f3a98e37156deabbf645098ae887214ca797d2c9a306de62704d1fc1
  Writing manifest to image destination
  WARNING: image platform (linux/amd64) does not match the expected platform (linux/arm64)
  64708e04f3a98e37156deabbf645098ae887214ca797d2c9a306de62704d1fc1
  ```


  ### Second Command:
  ```bash
  podman pull python:3.9-slim
  ```
  ```
  Resolved "python" as an alias (/etc/containers/registries.conf.d/000-shortnames.conf)
  Trying to pull docker.io/library/python:3.9-slim...
  Getting image source signatures
  Copying blob sha256:c23f4b50347300e01a1a1da6dd0266adcf8e44671002ad28c2386cb6557943d6
  Copying blob sha256:a16e551192670581ec8359c70ab9eebf8f2af5468ffc79b3d4f9ce21b0366f47
  Copying blob sha256:479b8ad8bcc3edbeba82d4959dfbdc65226d5b55df3f36914c68455762bf924c
  Copying blob sha256:ebfe7d4fa0c501a81a5ba6d1e1e2958e4b005d3ce3827b0adb869d47b8c51229
  Copying config sha256:9a63e92e90418ee93a722e8cdc7b3b18a9e052c80de8760887338d1c902644eb
  Writing manifest to image destination
  9a63e92e90418ee93a722e8cdc7b3b18a9e052c80de8760887338d1c902644eb
  ```


  ### Third Command:
  ```bash
  podman images
  ```
  ```
  REPOSITORY                                 TAG         IMAGE ID      CREATED       SIZE
  docker.io/library/python                   3.9-slim    9a63e92e9041  5 months ago  152 MB
  docker.io/matthewfeickert/intro-to-docker  latest      64708e04f3a9  4 years ago   1.62 GB
  ```

## Exercise 2:
  ### First command:
  ```bash
  podman run -it matthewfeickert/intro-to-docker:latest /bin/bash
  ```
  ```
  WARNING: image platform (linux/amd64) does not match the expected platform (linux/arm64)
  ```

  ### Second command:
  ```bash
  pwd
  hostname
  cat /etc/os-release
  ```
  ```
  /home/docker/data
  79951955a816
  PRETTY_NAME="Debian GNU/Linux 11 (bullseye)"
  NAME="Debian GNU/Linux"
  VERSION_ID="11"
  VERSION="11 (bullseye)"
  VERSION_CODENAME=bullseye
  ID=debian
  HOME_URL="https://www.debian.org/"
  SUPPORT_URL="https://www.debian.org/support"
  BUG_REPORT_URL="https://bugs.debian.org/"
  docker@79951955a816:~/data$ 
  ```

  ### Third command:
  ```bash
  podman ps
  podman rename <79951955a816> first_podman
  podman ps
  ```

  ### Fourth command:
  ```bash
  touch test.txt
  exit
  ```
  
  ### Fifth command:
  ```bash
  podman ps -a
  podman start first_podman
  podman attach first_podman
  ls
  ```
  ```
  CONTAINER ID  IMAGE                                             COMMAND     CREATED         STATUS                     PORTS       NAMES
  79951955a816  docker.io/matthewfeickert/intro-to-docker:latest  /bin/bash   21 minutes ago  Exited (1) 15 seconds ago              first_podman

  first_podman
  examples  test.txt
  ```

## Exercise 3:
  ### PART 1: Copying files
  #### First Command  
  ```bash
  touch io_example.txt
  echo "This was written on local host" > io_example.txt
  podman start first_podman
  podman cp io_example.txt first_podman:/home/docker/data/
  podman attach first_podman
  ```

  #### Second Command  
  ```bash
  pwd
  ls
  cat io_example.txt
  echo "This was written inside the container" >> io_example.txt
  exit
  ```

  #### Third Command  
  ```bash
  podman cp first_podman:/home/docker/data/io_example.txt .
  cat io_example.txt
  ```
  ```
  This was written on local host
  This was written inside the container
  ```
  
  ### PART 2: Volume Mounting
  #### First Command  
  ```bash
  podman run --rm -it -v $PWD:/home/docker/data matthewfeickert/intro-to-docker
  ```
  ```
  After trying to run commands inside the container it said 'ls: cannot open directory '.': Permission denied' as warned by the instructions.
  ```
  #### FIX
  ```bash
  exit
  podman run --rm -it -v $PWD:/home/docker/data matthewfeickert/intro-to-docker
  ```
  ```
  Machine "podman-machine-default" stopped successfully
  Starting machine "podman-machine-default"
  API forwarding listening on: /var/run/docker.sock
  Docker API clients default to this address. You do not need to set DOCKER_HOST.
  
  Machine "podman-machine-default" started successfully
  ```

  #### Second Command
  ```bash
  touch created_inside.txt
  ls
  exit
  ```
  ```
  created_inside.txt
  ```
  
  #### Third Command (Verified that it shows up inside the container and on the host machine)
  ```bash
  cd ~/container_test
  ls
  ```
  ```
  created_inside.txt
  ```
