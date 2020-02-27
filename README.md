# C/C++ Docker Development

## Dockerfile

The included `Dockerfile` is intended to serve as a basline for C/C++. It includes the following packages:
- [build-essential](https://packages.ubuntu.com/bionic/build-essential)
- [valgrind](https://valgrind.org/)
- [gdb](https://www.geeksforgeeks.org/gdb-step-by-step-introduction/)

Build Docker Image:
```bash
docker build -f Dockerfile -t cpp:latest .
```

## Getting Started

Run the following to gain access to a terminal in your container:
```bash
docker-compose run --rm devenv bash -c 'cd /home && bash'
```
*A shell script is provided for ease of use `start.sh`*

This will mount your current woring directory to the home directory.

# Additional Files

Makefile
```shell
CXX      = g++
CXX_FILE = $(wildcard *.cpp)
TARGET   = $(patsubst %.cpp,%,$(CXX_FILE))
CXXFLAGS = -g -std=c++11 -Wall -Werror -pedantic-errors -fmessage-length=0

all:
	$(CXX) $(CXXFLAGS) $(CXX_FILE) -o $(TARGET)
clean:
	rm -f $(TARGET) $(TARGET).exe
```