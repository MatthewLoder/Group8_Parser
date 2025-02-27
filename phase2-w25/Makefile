# Compiler
CC = gcc

# Directories
SRC_DIR = src
BUILD_DIR = build
INCLUDE_DIR = include

LEXER_SRC = $(SRC_DIR)/lexer/lexer.c
PARSER_SRC = $(SRC_DIR)/parser/parser.c

# Object files
LEXER_OBJ = $(BUILD_DIR)/lexer.o
PARSER_OBJ = $(BUILD_DIR)/parser.o

# Output binary
TARGET = parser

# Compiler flags
CFLAGS = -Wall -Wextra -I$(INCLUDE_DIR)

# Ensure the build directory exists
$(BUILD_DIR):
	mkdir -p $(BUILD_DIR)

# Compile lexer
$(LEXER_OBJ): $(LEXER_SRC) | $(BUILD_DIR)
	$(CC) $(CFLAGS) -c $< -o $@

# Compile parser
$(PARSER_OBJ): $(PARSER_SRC) | $(BUILD_DIR)
	$(CC) $(CFLAGS) -c $< -o $@

# Link the executable
$(TARGET): $(LEXER_OBJ) $(PARSER_OBJ)
	$(CC) $(CFLAGS) $^ -o $@

# Clean up build files
clean:
	rm -rf $(BUILD_DIR) $(TARGET)

# Run the parser with test inputs
run: $(TARGET)
	./$(TARGET) test/input_valid.txt

