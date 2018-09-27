CXX=g++
CXXFLAGS=-W -Wall -ansi -pedantic
LDFLAGS=
EXEC=build/pari
SRC_DIR = src
BUILD_DIR = build
FILES_DIR = files
SRC= $(wildcard $(SRC_DIR)/*.cpp) # src/main.cpp src/hash.cpp
#OBJ = $(patsubst $(SRC_DIR)/%,$(BUILD_DIR)/%,$(SRC:.cpp=.o)) # $(patsubt src/* build/* src/main.o src/hash.o) -> build/main.o build/hash.o
OBJ= $(SRC:$(SRC_DIR)/%.cpp=$(BUILD_DIR)/%.o) 

all: directories $(EXEC)
	

directories: $(BUILD_DIR) $(FILES_DIR)
	@echo $(OBJ)

$(BUILD_DIR):
	mkdir -p $(BUILD_DIR)
	
$(FILES_DIR):
	mkdir -p $(FILES_DIR)

$(EXEC): $(OBJ)
	@$(CXX) -o $@ $^ $(LDFLAGS)

$(BUILD_DIR)/%.o: $(SRC_DIR)/%.cpp
	@$(CXX) -o $@ -c $< $(CXXFLAGS)

.PHONY: clean mrproper

clean:
	@rm -rf $(BUILD_DIR)

mrproper: clean
	@rm -rf $(EXEC)

