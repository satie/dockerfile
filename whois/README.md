# whois
[whois](https://whois.icann.org/en) Docker container with node 8.9.4.

## Installation
Download and build the image from source 
```bash
$ git clone https://github.com/satie/dockerfiles.git
$ cd dockerfiles/whois
$ docker build -t whois .
```

## Usage
To run the `whois` command line client
```bash
$ docker run --rm whois google.com
```