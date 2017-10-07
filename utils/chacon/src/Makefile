# Declaration of variables
CXX:=g++
CXXFLAGS:=-I/usr/include/wiringPi
LDFLAGS:=-lwiringPi

# File names
EXEC = radioReception radioSend
SOURCES = $(wildcard *.cpp)
OBJECTS = $(SOURCES:.cpp=.o)

all: ${EXEC}

# Main target
$(EXEC): $(OBJECTS)
	$(CXX) $(LDFLAGS) $@.o -o $@

# To obtain object files
%.o: %.cpp
	$(CXX) -c $(CXXFLAGS)  $+ -o $@

# To remove generated files
clean:
	rm -f $(EXEC) $(OBJECTS)

