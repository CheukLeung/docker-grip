# Grip server in Docker
Running Grip (GitHub flavoured markdown) server in Docker.

## Description
You should run the container by mounting the current to `/mnt/workspace`. The Docker container `cd` into that directory and run `grip`.


## Building
```bash
docker build -t <tag> .
```

## Usage
- For one time usage, you can run the following command after building:

  ```bash
  docker run -p <port>:80 -v $(pwd):/mnt/workspace cheuk/docker-grip
  ```

- Alternatively, you can make a function in the `.bashrc` as below and call `grip`:

  ```bash
  function grip(){
    if [ -z "$1" ]; then
      echo "Usage: $FUNCNAME <port>"
    else
      echo "Browse to http://localhost:$1"
      docker run -p $1:80 -v $(pwd):/mnt/workspace cheuk/docker-grip
    fi
  }
  ```
